# CLOUD-CONNECTED SENSOR MONITORING AND ALERT SYSTEM FOR INDUSTRIAL APPLICATIONS

## 📌 Project Overview

This embedded system project enables **real-time monitoring of temperature and humidity** in industrial environments using **LPC2148 (ARM7)**. Sensor data is displayed locally on an LCD, stored in EEPROM, and uploaded to the **ThingSpeak cloud platform** via UART. The system also provides alerts through a **buzzer** when values exceed predefined thresholds and supports **remote or local updates** to these set points. An **RTC module** allows for time-based updates and editing of data logs.

---

## 🧠 Key Features

* Real-time temperature and humidity monitoring using **DHT11**
* Periodic data collection (every 5 seconds)
* Store data in **EEPROM (AT24C256)** using **I2C** protocol
* Upload data to **ThingSpeak** via **ESP01 Wi-Fi module** using **UART**
* **External interrupt** and **keypad** for setpoint configuration
* **RTC support** for time-based operations and data timestamping
* Real-time display using **20x4 LCD**
* **Buzzer alerts** on threshold exceedance
* Setpoint updates supported via **local (keypad)** or **remote (cloud)** input

---

## 🛠️ Hardware Requirements

* **LPC2148** Microcontroller (ARM7TDMI)
* **DHT11** Temperature and Humidity Sensor
* **AT24C256** EEPROM (I2C protocol)
* **RTC Module** (e.g., DS1307)
* **4x4 Matrix Keypad**
* **Switch** (for external interrupt)
* **20x4 LCD**
* **Buzzer**
* **ESP01 Wi-Fi Module** (UART interface)
* **DB-9 Cable or USB to UART Converter**

---

## 💻 Software Requirements

* **KEIL uVision IDE**
* **Embedded C Programming**
* **Flash Magic** for flashing code to LPC2148

---

## 📂 Folder Structure (Recommended)

```
CloudSensorMonitor_ARM7/
├── src/
│   ├── main.c
│   ├── lcd.c / lcd.h
│   ├── delay.c / delay.h
│   ├── keypad.c / keypad.h
│   ├── dht11_driver.c / dht11_driver.h
│   ├── esp01_driver.c / esp01_driver.h
│   ├── eeprom_driver.c / eeprom_driver.h
│   ├── rtc_driver.c / rtc_driver.h
│   └── interrupt_handler.c / interrupt_handler.h
├── docs/
│   └── readme.md
├── Makefile (optional for GCC-based builds)
```

---

## 🔄 System Workflow

1. **Initialize peripherals**: LCD, Keypad, UART, EEPROM (I2C), DHT11, RTC, ESP01
2. Load threshold values from EEPROM or set default ones if EEPROM is empty
3. In a loop:

   * Read temperature and humidity from DHT11 every 5 seconds
   * Display data on LCD
   * Store data to EEPROM with RTC timestamp
   * Send stored data to ThingSpeak using UART + ESP01
   * If temperature/humidity > threshold:

     * Trigger buzzer alert
   * On external interrupt:

     * Enter keypad-based menu for threshold editing
     * Save new values to EEPROM
   * Periodically (every 3–5 minutes), check cloud for remote setpoint updates

     * If updated, overwrite EEPROM values

---

## 📡 Cloud Integration (ThingSpeak)

* Field 1: Temperature
* Field 2: Humidity
* Field 3: Remote setpoint updates

---

## 🧪 Testing Instructions

* **LCD:** Display string/integer tests
* **Keypad:** Input key detection
* **UART Interrupt:** Verify with ESP01 AT commands
* **I2C EEPROM:** Test data write/read integrity
* **DHT11:** Sensor data verification
* **RTC:** Verify timestamp logging and time edits
* **External Interrupt:** Trigger threshold update mode via switch

---

## 📈 future Enhancements (Optional)

* Add mobile notifications via Twilio or Blynk
* Use OLED display for improved visibility
* Upgrade to **ESP32** for built-in Wi-Fi and Bluetooth
* Extend data logging with SD card module
* Web dashboard integration for cloud monitoring

---

## 🌐 Alternative IoT Platforms (FYR)

* ThingSpeak (Used)
* AWS IoT
* Microsoft Azure IoT
* Google Cloud IoT
* IBM Watson IoT
* Ubidots
* Cayenne
* Blynk

---

## ✅ Completion Criteria

* Accurate sensor data captured and stored in EEPROM
* Real-time display and alerts working
* Data uploads successfully to ThingSpeak via ESP01
* Local and cloud-based setpoint updates work reliably
* RTC integrated for time-aware data logging
* External interrupt + keypad allow seamless interaction

---

## 👏 All the Best!

Feel free to enhance or customize this system based on your needs.

> **Author**: \MOHD MOSHIR KHAN
> **Technologies**: Embedded C, KEIL, LPC2148, I2C, UART, IoT, RTC, ThingSpeak
