# Adaptive Multi-Cell Battery Intelligence System

An ESP32-based embedded battery management system (BMS) for a simulated four-cell lithium pack, built and validated in Wokwi. The firmware performs real-time cell analytics, non-blocking safety protection, local HMI diagnostics, fault-tolerant sensing, and event-driven cloud telemetry to Blynk, with an executive-level dashboard on top.

Developed as a combined six-task project during an Embedded Systems Engineer internship at ElevanceSkills.

Features
| Task | Capability |
|---|---|
| 1. Battery Intelligence Engine | Per-cell voltage, pack average, imbalance %, weakest/strongest cell, four-tier health classification |
| 2. Safety Protection Kernel | Non-blocking, millis()-based relay/buzzer/LCD protection with anti-chatter debouncing |
| 3. Embedded HMI | Fault-priority LCD status display |
| 4. Fault-Tolerant Runtime | Frozen-ADC, out-of-range, and fluctuation fault isolation |
| 5. Cloud Telemetry | Event-driven Blynk telemetry with offline queueing and reconnect handling |
| 6. Executive Dashboard | Pack analytics, severity colour coding, trend charts, and plain-language operator recommendations on Blynk |

Hardware (simulated in Wokwi)

| Signal | ESP32 Pin | Function |
|---|---|---|
| Cell 1–4 voltage | GPIO 34, 35, 32, 33 (ADC1) | Analog input, simulated cell voltage (potentiometers) |
| Relay control | GPIO 26 | Pack cutoff contactor |
| Buzzer | GPIO 25 | Audible fault alert |
| LCD SDA / SCL | GPIO 21 / 22 | I2C bus to 16x2 LCD |


BLYNK DATASTREAMS

| Pin | Data | Type |
|---|---|---|
| V0 | Health state (enum) | Integer |
| V1 | Active fault (enum) | Integer |
| V2 | Relay state | Integer |
| V3 | RSSI at last event | Integer |
| V4–V7 | Cell 1–4 voltage | Double |
| V8 | Event timestamp | Integer |
| V9 | Pack average voltage | Double |
| V10 | Imbalance percentage | Double |
| V11 | Weakest cell (pin id) | Integer |
| V12 | Strongest cell (pin id) | Integer |
| V13 | Operator recommendation | String |
| V14 | Signal strength (RSSI, periodic) | Integer |

