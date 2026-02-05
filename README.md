# Air-quality-checker
IoT air quality monitoring system using ESP32, MQ-135, DHT22,BMP280,
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
#include <DHT.h>

// OLED settings
#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64
#define OLED_RESET -1
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

// DHT settings
#define DHTPIN 4
#define DHTTYPE DHT22
DHT dht(DHTPIN, DHTTYPE);

// MQ135 simulated using potentiometer
#define MQ135_PIN 34

void setup() {
  Serial.begin(115200);
  dht.begin();

  // OLED init
  if (!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
    Serial.println("OLED not found");
    while (true);
  }

  display.clearDisplay();
  display.setTextColor(SSD1306_WHITE);
  display.setTextSize(1);

  display.setCursor(0, 0);
  display.println("Air Monitor");
  display.println("Initializing...");
  display.display();

  delay(2000);
}

void loop() {
  float temp = dht.readTemperature();
  float hum = dht.readHumidity();
  int air = analogRead(MQ135_PIN);

  display.clearDisplay();
  display.setCursor(0, 0);

  display.println("AIR QUALITY MONITOR");
  display.println("------------------");

  display.print("Temp: ");
  display.print(temp);
  display.println(" C");

  display.print("Hum : ");
  display.print(hum);
  display.println(" %");

  display.print("Air : ");
  display.println(air);

  // Air quality status
  display.print("Status: ");
  if (air < 300) display.println("GOOD");
  else if (air < 600) display.println("MODERATE");
  else display.println("POOR");

  display.display();

  // Serial Monitor output
  Serial.println("------ DATA ------");
  Serial.print("Temp: "); Serial.println(temp);
  Serial.print("Humidity: "); Serial.println(hum);
  Serial.print("Air Quality: "); Serial.println(air);

  delay(2000);
}
