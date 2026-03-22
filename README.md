# Automatic-fire-alarm-and-extinguishing-system-using-LabVIEW
# Automatic Fire Alarm and Extinguishing System using LabVIEW

## Project Overview
This project presents an automated fire detection and extinguishing system developed using NI LabVIEW and an Arduino Uno microcontroller. The system utilizes an MQ-2 gas sensor to continuously monitor the environment for smoke and combustible gases. 

The core feature of this project is the signal processing algorithm implemented in LabVIEW, which converts the raw analog voltage obtained from the MQ-2 sensor into a precise Parts Per Million (PPM) value. This allows for real-time, accurate hazard assessment and automated activation of extinguishing mechanisms when gas concentrations exceed a predefined safety threshold.

## Key Features
* **Real-time Data Acquisition:** Continuous monitoring of environmental conditions using the MQ-2 sensor.
* **PPM Calculation:** Advanced data processing in LabVIEW to map raw analog inputs (0-5V) to actual gas concentration levels (PPM) based on the sensor's characteristic curve.
* **Interactive Graphical User Interface (GUI):** A comprehensive LabVIEW Front Panel featuring waveform charts, numeric indicators, and visual alerts for real-time monitoring.
* **Automated Safety Response:** Automatic triggering of physical actuators (e.g., relays, water pumps, or ventilation fans) and audible alarms when the calculated PPM exceeds the user-defined threshold.
* **Configurable Parameters:** Users can dynamically adjust the safety threshold (PPM limit) directly through the LabVIEW interface.

## Hardware Requirements
1. **Arduino Uno R3:** Acts as the Data Acquisition (DAQ) interface and hardware controller.
2. **MQ-2 Gas/Smoke Sensor:** Connected via an analog input pin (e.g., A0).
3. **Relay Module:** Used to safely switch high-power loads (pumps/fans).
4. **Water Pump or DC Fan:** Serves as the automated extinguishing/ventilation mechanism.
5. **Buzzer and LEDs:** For local audible and visual warnings.
6. **Power Supply & Jumper Wires.**

## Software Requirements
* **NI LabVIEW** (Version 2018 or newer recommended).
* **NI-VISA** or **MakerHub LINX** toolkit (for serial communication between LabVIEW and Arduino).
* **Arduino IDE** (for uploading base firmware to the microcontroller).

## System Architecture
1. **Sensing Phase:** The MQ-2 sensor detects variations in gas concentration and outputs a proportional analog voltage to the Arduino.
2. **Transmission:** The Arduino digitizes the signal via its internal ADC and transmits the raw data to the PC via USB/Serial communication.
3. **Processing Phase:** LabVIEW receives the serial data stream, filters it, and applies the calibration formula to derive the precise PPM value.
4. **Logic & Actuation:** The system continuously compares the current PPM against the set threshold. If `Current PPM > Threshold`, LabVIEW transmits a high-level command back to the Arduino to activate the digital outputs connected to the alarm and relay module.

## Installation and Usage

**1. Hardware Setup**
* Connect the analog output (A0) of the MQ-2 sensor to the A0 pin on the Arduino.
* Connect the control pin of the Relay and the Buzzer to designated digital pins (e.g., D8, D9).
* Ensure all components share a common ground (GND).

**2. Firmware Installation**
* Open the Arduino IDE and upload the provided `.ino` communication script to the Arduino Uno.
* *(Alternative)* If using the LINX toolkit, open LabVIEW and navigate to `Tools -> MakerHub -> LINX -> LINX Firmware Wizard` to flash the board.

**3. Running the LabVIEW Application**
* Open the main `.vi` file in NI LabVIEW.
* On the Front Panel, select the correct COM Port corresponding to your Arduino.
* Input the desired safety limit in the `PPM Threshold` control box.
* Click the **Run** button.
* Test the system by introducing a safe amount of gas (e.g., from an unlit lighter) near the MQ-2 sensor to observe the PPM spike and subsequent relay activation.

## Author
* **phuongproduc**
* GitHub Profile: [https://github.com/phuongproduc](https://github.com/phuongproduc)

## License
This project is licensed under the MIT License - see the LICENSE file for details.
