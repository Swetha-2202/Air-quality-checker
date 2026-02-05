# Air-quality-checker
IoT air quality monitoring system using ESP32, MQ-135, DHT22,BMP280.
 ESP32 Air Quality Monitoring System

 Description
This project monitors environmental conditions using an ESP32.
It displays Temperature, Humidity, and Air Quality on an OLED display.

Due to simulation limitations, a potentiometer is used to simulate
the MQ-135 gas sensor in Wokwi.

 Components
- ESP32 Development Board
- DHT22 Temperature & Humidity Sensor
- OLED Display (SSD1306, I2C)
- Potentiometer (MQ-135 Simulation)

 Pin Connections
 DHT22
- VCC → 3.3V
- DATA → GPIO 4
- GND → GND

 OLED
- VCC → 3.3V
- GND → GND
- SDA → GPIO 21
- SCL → GPIO 22

 Potentiometer (MQ-135)
- VCC → 3.3V
- GND → GND
- OUT → GPIO 34

 Simulation
Wokwi simulator is used.
Potentiometer rotation represents change in air quality.

 Output
- OLED shows live values
- Serial Monitor logs sensor readings

Author

Swetha
