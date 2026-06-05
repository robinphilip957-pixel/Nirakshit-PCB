# Nirakshit - Tunnel Mapping & Inspection PCB
<p align="center">
  <img src="Docs/3D PCB.png" alt="3D PCB" height="300"/> &nbsp;&nbsp;&nbsp;
  <img src="Docs/3D PCB Top.png" alt="3D PCB Top" height="300"/>
</p>

<p align="center">
  <img src="Docs/Reboot Certificate.png" alt="Reboot 2.0 Certificate - 2nd Place" width="600"/>
</p>

> 🏆 **2nd Place — Reboot 2.0 Hackathon, Riviera 2025, VIT Vellore**

Nirakshit is a custom drone-mounted PCB fully designed and developed in EasyEDA Pro for the Reboot 2.0 Hackathon, hosted during Riviera 2025 at VIT Vellore, by Team Nirakshit. The team secured **2nd place** at the competition.

The core concept behind Nirakshit is autonomous tunnel inspection — the PCB is mounted on a drone that navigates inside man-made or natural tunnels. A 2D LiDAR combined with an IMU and barometer generates a real-time 3D map of the tunnel environment. The board is further equipped with environmental sensors (DHT11, MQ135, and flame sensor) for detecting temperature, humidity, air quality, and fire hazards. LoRa provides long-range telemetry to a ground station, an SD card logs all sensor data onboard, and an ESP32-CAM module performs visual inspection of tunnel walls for cracks and structural defects. ESP32-S3 was the chosen microcontroller for its powerful dual-core performance, rich peripheral support, and native USB capabilities.



## Component ICs Used
- ESP32-S3 (Main Microcontroller — Xtensa LX7 Dual-Core, Wi-Fi + Bluetooth)
- ESP32-CAM (Visual Inspection Module — Camera + Wi-Fi, connected via UART)
- MPU6050 (6-Axis IMU — Accelerometer + Gyroscope, I2C)
- ATK-NEO-6M (GPS Module — UART)
- RFM95W (LoRa Transceiver — SPI, 915MHz, with SMA antenna connector)
- DHT11 (Temperature and Humidity Sensor)
- MQ135 (Air Quality / Gas Sensor — Analog)
- Flame Sensor (Fire Detection — Digital)
- 2D LiDAR (Tunnel Mapping — UART + PWM)
- TF-115Y-BCP9 (Micro SD Card Slot — SPI)
- HT7833 (3.3V LDO Voltage Regulator)
- 74LVC125APW (Quad Bus Buffer / Logic Level Shifter — 5V ↔ 3.3V)
- XT30AW-M (Battery Power Connector)



## Pinout and Address

**_Communication Interface:_**
| **SDA** | **SCL** | **MOSI** | **MISO** | **SCK** |
| ------- | ------- | -------- | -------- | ------- |
|   IO21  |   IO22  |   IO23   |   IO19   |  IO18   |


**_I2C Peripheral Addresses:_**
| **MPU6050 (IMU)** |
| :---------------: |
| 0x68              |


**_SPI Peripherals:_**

| **RFM95W (LoRa)** | **GPIO**  | **Micro SD Card** | **GPIO** |
|:-----------------:|:---------:|:-----------------:|:--------:|
|        SCK        |   IO18    |        SCK        |  IO18    |
|       MISO        |   IO19    |       MISO        |  IO19    |
|       MOSI        |   IO23    |       MOSI        |  IO23    |
|        NSS        |   IO4     |        CS         |  IO21    |
|       RESET       |   IO16    |         -         |    -     |
|       DIO0        |   IO17    |         -         |    -     |


**_UART Peripherals:_**

_NEO-6M GPS:_
| **GPS TX → ESP RX** | **GPS RX → ESP TX** |
|:-------------------:|:-------------------:|
|        IO16         |        IO17         |

_ESP32-CAM:_
| **CAM TX → ESP RX** | **CAM RX → ESP TX** |
|:-------------------:|:-------------------:|
|        IO35         |        IO14         |

_2D LiDAR:_
| **LiDAR RX** | **LiDAR PWM** |
|:------------:|:-------------:|
|     IO32     |      IO33     |


**_Sensor Pinout:_**
| **DHT11** | **MQ135 (Analog)** | **Flame Sensor** |
|:---------:|:------------------:|:----------------:|
|   IO12    |        IO27        |      IO26        |


**_General Pinout:_**
| **Battery Voltage ADC** |
|:-----------------------:|
|          IO34           |



## References
- [ESP32-S3 Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf)
- [ESP32-S3 Hardware Design Guidelines](https://docs.espressif.com/projects/esp-idf/en/latest/esp32s3/hw-reference/index.html)
- [ESP32-CAM Datasheet](https://loboris.eu/ESP32/ESP32-CAM%20Product%20Specification.pdf)
- [MPU6050 Datasheet](https://invensense.tdk.com/wp-content/uploads/2015/02/MPU-6000-Datasheet1.pdf)
- [NEO-6M GPS Datasheet](https://content.u-blox.com/sites/default/files/products/documents/NEO-6_DataSheet_%28GPS.G6-HW-09005%29.pdf)
- [RFM95W LoRa Datasheet](https://cdn.sparkfun.com/assets/learn_tutorials/8/0/4/RFM95_96_97_98W.pdf)
- [DHT11 Datasheet](https://www.mouser.com/datasheet/2/758/DHT11-Technical-Data-Sheet-Translated-Version-1143054.pdf)
- [MQ135 Datasheet](https://www.olimex.com/Products/Components/Sensors/SNS-MQ135/resources/SNS-MQ135.pdf)
- [HT7833 Datasheet](https://www.holtek.com/documents/10179/116711/HT78xx-1v175.pdf)
- [74LVC125A Datasheet](https://assets.nexperia.com/documents/data-sheet/74LVC125A.pdf)
- [GreatScott YouTube](https://www.youtube.com/@greatscottlab)
- [Robert Feranec YouTube](https://www.youtube.com/@RobertFeranec_)
- [Phill's Lab YouTube](https://www.youtube.com/watch?v=_Hfzq1QES-Q)

Author: Robin Philip | Team Nirakshit — Reboot 2.0, Riviera 2025, VIT Vellore 🏆 2nd Place
