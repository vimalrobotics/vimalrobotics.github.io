---
date: 2019-04-15
title: IoT-Based PC Power Control System
subtitle: Safe Embedded IoT Automation
image: '/images/iot_pc_cover.png'
category: embedded-iot
featured: false
---

## Overview

This project implements a **safe IoT-based PC power control system** that allows a desktop computer
to be powered ON or OFF remotely using **voice commands via Google Assistant**.

The core engineering focus of the system was **electrical safety**, achieved through **galvanic isolation**
between the IoT controller and the PC motherboard using an optocoupler.
The system emulates a physical power button press without injecting voltage into the motherboard.

---

## System Architecture

![System Architecture](/images/iot_pc_flow.png)

**Control Flow:**

Google Assistant → Cloud Automation → MQTT → ESP8266 → Optocoupler → PC Power Switch

---

## Hardware Design

### Circuit Diagram

![Circuit Diagram](/images/iot_pc_control.jpg)

### Key Hardware Components

- **ESP8266 D1 Mini**
- **4N35 Optocoupler**
- Series resistor for optocoupler LED current limiting
- Direct connection to PC motherboard **PWR_SW header**

### Electrical Isolation Strategy

- No shared ground between ESP8266 and PC motherboard
- Optocoupler output used as an isolated open-collector switch
- Motherboard power button pins treated strictly as a dry contact

---

## Firmware Implementation

The ESP8266 firmware listens for MQTT commands and generates a **timed momentary pulse**
that electrically mimics a physical power button press.

### Key Characteristics

- Stateless power control (ACPI handled by OS)
- Fixed-duration press to prevent latch-up
- Defensive defaults on boot
- No continuous drive of motherboard signals

### Firmware Code

```cpp
#include <ESP8266WiFi.h>
#include "Adafruit_MQTT.h"
#include "Adafruit_MQTT_Client.h"

// ===================== USER CONFIG =====================

// WiFi
#define WIFI_SSID "your-ssid"
#define WIFI_PASS "your-password"

// Adafruit IO (MQTT)
#define AIO_SERVER      "io.adafruit.com"
#define AIO_SERVERPORT  1883
#define AIO_USERNAME    "YOUR_AIO_USERNAME"
#define AIO_KEY         "YOUR_AIO_KEY"

// MQTT feed
#define POWER_FEED      AIO_USERNAME "/feeds/onoff"

// GPIO driving 4N35 optocoupler LED
#define PWR_BUTTON_PIN  D5      // GPIO14

// Button press duration (milliseconds)
#define PWR_PULSE_MS    300     // 200–500 ms recommended

// =======================================================

WiFiClient client;
Adafruit_MQTT_Client mqtt(
  &client,
  AIO_SERVER,
  AIO_SERVERPORT,
  AIO_USERNAME,
  AIO_KEY
);

Adafruit_MQTT_Subscribe powerCmd =
  Adafruit_MQTT_Subscribe(&mqtt, POWER_FEED);

void setup() {
  Serial.begin(115200);
  Serial.println("ESP8266 IoT PC Power Controller");

  pinMode(PWR_BUTTON_PIN, OUTPUT);
  digitalWrite(PWR_BUTTON_PIN, LOW);   // ensure released

  connectWiFi();
  mqtt.subscribe(&powerCmd);
}

void loop() {
  connectMQTT();

  Adafruit_MQTT_Subscribe *sub;
  while ((sub = mqtt.readSubscription(5000))) {
    if (sub == &powerCmd) {
      String cmd = String((char *)powerCmd.lastread);
      cmd.trim();
      cmd.toLowerCase();

      if (cmd == "on" || cmd == "off") {
        pressPowerButton();
      }
    }
  }

  if (!mqtt.ping()) {
    mqtt.disconnect();
  }
}

void pressPowerButton() {
  digitalWrite(PWR_BUTTON_PIN, HIGH);
  delay(PWR_PULSE_MS);
  digitalWrite(PWR_BUTTON_PIN, LOW);
}

void connectWiFi() {
  WiFi.mode(WIFI_STA);
  WiFi.begin(WIFI_SSID, WIFI_PASS);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
  }
}

void connectMQTT() {
  if (mqtt.connected()) return;

  uint8_t retries = 3;
  while (mqtt.connect() != 0) {
    mqtt.disconnect();
    delay(5000);
    if (--retries == 0) {
      ESP.restart();
    }
  }
}
```

## Engineering Considerations
- Electrical safety over convenience
- Avoided relays to eliminate mechanical wear
- Designed for noisy PC environments
- Defensive firmware to prevent stuck states
- No voltage injection into motherboard headers

## Key Learnings
- Electrical isolation is mandatory when interfacing consumer electronics
- PC motherboard headers are logic-level contacts, not power rails
- IoT automation must fail safely, not optimistically
- Simple hardware combined with disciplined firmware yields robust systems

## Outcome

This project demonstrates responsible embedded IoT design by combining
networked automation with proper electrical engineering discipline.
It serves as a foundation for more advanced remote management systems
such as BMC-style controllers or secure home automation platforms.