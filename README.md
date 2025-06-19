Sustainable Intelligent Irrigation System
A data-driven, IoT-based smart irrigation controller designed to optimize water usage in agriculture by leveraging real-time sensor data, weather forecasts, and crop-specific requirements.

Overview
This project addresses the critical issue of water inefficiency in traditional agriculture. By creating a closed-loop control system, it automates the irrigation process, ensuring that crops receive the precise amount of water needed, exactly when they need it. The system significantly reduces water waste, conserves energy, and promotes healthier plant growth, making it a sustainable solution for modern farming, particularly in water-scarce regions like Zambia.

The core of the system is a Raspberry Pi 4, which acts as the main brain, running a Python-based application with a Flask API. It processes data from an Arduino Uno that interfaces with a suite of environmental sensors. A Flutter mobile application serves as a user-friendly dashboard for remote monitoring and control.

✨ Key Features
💧 Real-time Environmental Monitoring: Continuously tracks soil moisture, ambient temperature, humidity, and water tank levels.

🌱 Crop-Specific Irrigation Logic: Utilizes a database with water requirements for different crops (Maize, Beans, Soybeans) at various growth stages.

🤖 Automated & Intelligent Control: The system's algorithm decides when and how much to water based on a daily water target (mm/day), evapotranspiration (ET) conditions, and real-time sensor feedback.

📱 Mobile Dashboard: A cross-platform Flutter app allows users to monitor system status, view historical data graphs, configure crop settings, and manually control the pump from anywhere.

☁️ Weather Forecast Integration: Fetches daily and hourly weather data from Open-Meteo to proactively delay irrigation if significant rain is forecasted.

📊 Historical Data Logging: Logs all sensor data and system decisions to a local database for analysis and performance tracking.

⚙️ Manual Override: Users can manually turn the pump on or off via the mobile app, overriding the automatic schedule when needed.

🏛️ System Architecture
The system is built on a distributed intelligence model to ensure both reliability and powerful data processing.

Arduino Uno: Dedicated to real-time tasks. It reliably reads data from all connected sensors (Soil Moisture, DHT22, Ultrasonic) and controls the water pump relay. It communicates with the Raspberry Pi via a serial connection.

Raspberry Pi 4: The central controller. It runs the main Python application, which includes:

The core decision-making logic.

A Flask web server to provide a REST API for the mobile app.

A data logger that saves historical data to a MySQL database.

A weather-fetching module.

Flutter Mobile App: The user's window into the system. It communicates with the Raspberry Pi's API to display data and send commands.

Data Flow Diagram (Level 1)

This diagram shows the flow of data between the system's core processes.

🛠️ Technology Stack
Hardware
Component

Function

Raspberry Pi 4

Main controller, runs Python server & logic

Arduino Uno

Sensor/actuator interface, real-time control

Capacitive Soil Moisture Sensor

Measures soil water content

DHT22 Sensor

Measures ambient temperature and humidity

Ultrasonic Sensor (HC-SR04)

Measures water level in the reservoir tank

5V Relay Module

Safely switches the high-voltage water pump

12V DC Water Pump

Delivers water to the irrigation pipes

16x2 LCD Display

Provides on-site system status display

Software & Libraries
Backend (Raspberry Pi): Python 3, Flask (for API), pyserial (for Arduino communication), requests (for weather API).

Database: MySQL.

Embedded (Arduino): C++ with Arduino libraries (DHT.h, NewPing.h, LiquidCrystal_I2C.h).

Mobile App: Flutter framework with Dart. Key packages: http, fl_chart, intl.

🚀 Setup and Installation
1. Hardware Setup
Connect all hardware components as shown in the circuit diagram.
[SUGGESTION: Insert a clear image of your circuit diagram here, like the one from your presentation slide 11.]


2. Raspberry Pi Setup
# 1. Update and install prerequisites
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install python3 python3-pip mariadb-server -y

# 2. Secure MySQL and create a database/user
sudo mysql_secure_installation
# Follow the prompts. Then, log in to create the database:
sudo mysql -u root -p
# In the MySQL prompt:
# CREATE DATABASE irrigation_system;
# CREATE USER 'irrigation_user'@'localhost' IDENTIFIED BY 'YourStrongPassword';
# GRANT ALL PRIVILEGES ON irrigation_system.* TO 'irrigation_user'@'localhost';
# FLUSH PRIVILEGES;
# EXIT;

# 3. Clone the repository
git clone [Your GitHub Repository URL]
cd [Your-Repository-Folder-Name]

# 4. Install Python dependencies
pip3 install -r requirements.txt 
# (You will need to create a requirements.txt file with Flask, pyserial, requests, etc.)

# 5. Run the main controller script
python3 main_controller.py

3. Arduino Setup
Open the arduino_firmware/arduino_firmware.ino file in the Arduino IDE.

Go to Sketch > Include Library > Manage Libraries....

Install the following libraries:

DHT sensor library by Adafruit

NewPing by Tim Eckel

LiquidCrystal I2C by Frank de Brabander

Connect the Arduino to your computer, select the correct board and port, and click Upload.

4. Flutter App Setup
Make sure you have the Flutter SDK installed.

Navigate to the flutter_app directory in your project.

Open the lib/main.dart file.

Update the IP address constant to match your Raspberry Pi's IP address on your local network:

const String RASPBERRY_PI_IP = "192.168.X.X"; // Your Pi's IP Address

Run the app on your connected device or emulator:

flutter pub get
flutter run

📈 Project Demo
Physical Prototype:
[SUGGESTION: Insert images of your assembled prototype here, like the ones from your presentation slide 12.]


Mobile Application Dashboard:
[SUGGESTION: Insert the screenshots of your mobile app here, like the ones from your presentation slide 13.]


👥 Authors & Acknowledgements
This project was developed by:

Musinje Phiri (202107144)

Joshua Chitaani (202003666)

This report is submitted in partial fulfilment for the award of Bachelor of Electrical and Electronics Engineering at Mulungushi University.

A special thank you to our supervisors, Mr. L. Simukonda and Mr. C. Kabanda, for their invaluable guidance and support throughout this project.

📄 License
This project is licensed under the MIT License. See the LICENSE.md file for details.
