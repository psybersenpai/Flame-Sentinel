# Flame Sentinel

**Flame Sentinel** is a real-time embedded fire alarm detection and notification system built on a Raspberry Pi Zero W 2. This project captures ambient audio using an Adafruit I2S MEMS Microphone, processes the audio in real time with modern C++ digital signal processing, and detects the signature sound of a fire alarm. When a fire alarm is detected, a REST API integration triggers push notifications for immediate alerts.

---

## Table of Contents

- [Features](#features)
- [Hardware Requirements](#hardware-requirements)
- [Software Requirements](#software-requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Integration](#api-integration)
- [Future Enhancements](#future-enhancements)
- [License](#license)
- [Acknowledgements](#acknowledgements)

---

## Features

- **Real-Time Audio Processing:**  
  Utilizes digital signal processing (DSP) techniques to apply a FIR filter for isolating fire alarm frequencies.

- **Embedded Systems Integration:**  
  Interfaces with an I2S MEMS Microphone on the Raspberry Pi Zero W 2 for live audio capture.

- **REST API & Push Notifications:**  
  Sends detection events to a REST API endpoint which triggers push notifications to alert users.

- **Modular Design:**  
  Structured for easy expansion (e.g., multi-sensor integration, advanced analytics).

---

## Hardware Requirements

- **Raspberry Pi Zero W 2** with headers
- **Adafruit I2S MEMS Microphone Breakout**
- MicroSD Card (8GB minimum recommended)
- 5V Power Supply (2.5A recommended)
- Jumper wires, breadboard (if needed)
- (Optional) Enclosure for the Raspberry Pi

---

## Software Requirements

- **Operating System:** Raspberry Pi OS Lite (or a PREEMPT_RT patched version if real-time performance is critical)
- **Development Tools:**  
  - GCC (g++ supporting C++11 or higher)
  - CMake
  - Git
- **Libraries:**  
  - ALSA development libraries (`libasound2-dev`)
- **Additional Tools:**  
  - A tool for testing REST APIs (e.g., Postman or curl)

---

## Installation

1. **Update and Upgrade the System:**

   ```bash
   sudo apt update && sudo apt upgrade -y
2. **Install Required Packages:**
   ```bash
   sudo apt install -y build-essential cmake git libasound2-dev
3. **Clone the Repository:**
   ```bash
   git clone https://github.com/<your-username>/Flame-Sentinel.git
   cd Flame-Sentinel
4. **Configure and Build the Project:**
   ```bash
   mkdir -p build && cd build
   cmake ..
   cmake --build .

---

## Usage

  **Audio Capture & Processing:**
        Connect your Adafruit I2S MEMS Microphone to the Raspberry Pi Zero W 2.
        Run the application executable generated in the build process.
        The application will start capturing audio and process it in real time to detect fire alarm signatures.

  **REST API Trigger:**
        When a fire alarm is detected, the system sends a POST request to your configured REST API endpoint.
        Ensure your API server is running and correctly configured to accept detection events.

  **Push Notifications:**
        The REST API is responsible for triggering push notifications using your chosen service (e.g., Firebase, Pushover, etc.).

---

## Project Structure
```
Flame-Sentinel/
├── build/                # Build directory for compiled binaries
├── docs/                 # Documentation files
├── include/              # Header files
├── src/                  # Source code files
│   ├── main.cpp          # Main application file
│   └── audio_processor.cpp/h   # Audio capture and DSP routines
├── CMakeLists.txt        # CMake build configuration file
└── README.md             # This file
```
---

## API Integration

**REST API Endpoint:**

  * The application sends a POST request to a predefined URL when a fire alarm is detected.
  * **Payload Example:**
    ```bash
    {
    "timestamp": "2025-03-04T12:00:00Z",
    "event": "fire_alarm_detected",
    "signal_strength": 85
    }
  * **Configuration:**
    Configure the API endpoint URL and any necessary authentication parameters in the project configuration files before deployment.

---

## Future Enhancements

  **Multi-Sensor Integration:**
    Add temperature and smoke sensors to corroborate fire alarm detection.

  **Advanced Notification System:**
    Expand the notification system to include SMS, email, or mobile app push notifications.

  **Machine Learning:**
    Implement machine learning algorithms to reduce false positives and better differentiate between alarm sounds and ambient noise.

  **Web Dashboard:**
    Develop a web interface to monitor detection events and analyze historical data.

---

## License

This project is licensed under the MIT License. See the **LICENSE** file for details.

---

## Acknowledgements

  * Thanks to the Adafruit Industries team for the I2S MEMS Microphone Breakout.
  * Inspired by real-time embedded systems and safety-critical applications.
  * Contributions from the open source community that made this project possible.
