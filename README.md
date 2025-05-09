# Parking Management System

This project, developed by **cielo-b**, is an automated parking management system that uses computer vision for license plate recognition, an ultrasonic sensor for vehicle detection, and an Arduino for gate control. It also supports RFID-based payment processing for card registration, balance management, and parking fee deduction.

The system logs vehicle entries and exits in `plates_log.csv` and manages RFID card data in `cards.csv`, providing a complete solution for parking automation.

## Features

- **License Plate Recognition**: Detects and validates license plates (format: RA123A) using YOLOv8 and Tesseract OCR.
- **Vehicle Detection**: Uses an HC-SR04 ultrasonic sensor to detect vehicles within 50 cm.
- **Gate Control**: Automates gate opening/closing via an Arduino-connected mechanism (e.g., servo, relay).
- **RFID Payment Processing**: Registers RFID cards, tops up balances, and processes parking fees at 200/hour.
- **CSV Logging**:
  - `plates_log.csv`: Tracks vehicle entries/exits (Plate Number, Payment Status, In time, Out time).
  - `cards.csv`: Stores RFID card data (Card ID, Plate Number, Balance).

## Requirements

### Hardware

- Arduino (e.g., Uno, Nano) connected via USB (`/dev/ttyACM0` or `/dev/ttyUSB0`).
- HC-SR04 Ultrasonic Sensor:
  - TRIG: Arduino pin 7
  - ECHO: Arduino pin 8
  - VCC: 5V
  - GND: Arduino GND
- Gate Mechanism: Servo, relay, or motor driver connected to Arduino pin 6 (HIGH to open, LOW to close).
- Webcam: USB or built-in for license plate capture.
- RFID Reader (e.g., MFRC522):
  - Required for `payment_processor.py`.
  - Connect to Arduino SPI pins (refer to `rfid_manager.py` for pinout).

### Software

- Python 3.8+ with the following libraries:
  ```bash
  pip install opencv-python ultralytics pytesseract numpy pyserial