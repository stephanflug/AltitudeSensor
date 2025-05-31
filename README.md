# 🛰️ Altitude Sensor

<img src="https://github.com/stephanflug/AltitudeSensor/blob/main/Bild.png?raw=true" alt="Logo" width="500" height="500"/>
---

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-ESP32-green.svg)]()
[![MQTT](https://img.shields.io/badge/Protocol-MQTT-orange.svg)]()

---

## 📋 Beschreibung

Firmware für einen IoT-Höhen- und Umweltsensor basierend auf ESP32c3

**Features:**

- Temperatur- und Luftfeuchtigkeitsmessung mit AHT20  
- Luftdruck- und Höhendaten mit BMP280  
- OLED-Display (SSD1306) zur Anzeige  
- WLAN mit konfigurierbarem Setup-Hotspot  
- MQTT-Protokoll zum Senden der Sensordaten  
- OTA-Updates per Button  
- Langdruck-Button zur Steuerung (Reset, Setup, Update)  
- Speicherung der Einstellungen & Maximalwerte im non-volatile Speicher (Preferences)  

---

## ⚙️ Hardwareanschluss

| Funktion        | GPIO-Pin |
|-----------------|----------|
| I2C SDA         | 5        |
| I2C SCL         | 6        |
| Boot Button     | 9        |
| Status LED      | 8        |

---

## 🚀 Installation & Nutzung

1. Verbinde Sensoren und Display mit den oben angegebenen Pins.  
2. Firmware auf den ESP32c3 flashen.  
3. Beim ersten Start öffnet sich ein WLAN-Hotspot `Altitude Sensor` für die Konfiguration.  
4. Im Browser WLAN-Hotspot aufrufen und SSID, Passwort, MQTT-Daten sowie Sensor-ID eingeben.  
5. Nach Speichern erfolgt automatischer Neustart und Verbindung zum WLAN.  
6. Sensordaten werden über MQTT gesendet und auf dem OLED angezeigt.

---

## 🔘 Bedienung des Buttons

- **Kurz drücken (< 3 Sek.):** Reset der gespeicherten Maximalwerte.  
- **Lang drücken (≥ 3 Sek.):** Start des Setup-Hotspots.  
- **Sehr lang drücken (≥ 10 Sek.):** OTA-Update starten.

---

## 📡 MQTT-Topic & Payload

**Topic:**


**Beispiel Payload (JSON):**
```json
{
  "temp": 22.5,
  "hum": 55.3,
  "alt": 250.1,
  "max_delta_alt": 103,4,
  "bootCount": 3
}
```

📚 Benötigte Bibliotheken

Adafruit AHTX0

Adafruit BMP280

U8g2 Display

PubSubClient MQTT

Preferences Library (Teil des ESP Arduino Cores)

### Unterstütze das Büro-Kaffeekonto!

Damit der Kaffee im Büro nie ausgeht, wäre eine kleine Spende super! 💰☕  
Jeder Beitrag hilft, die Kaffeemaschine am Laufen zu halten, damit wir alle produktiv bleiben können!

[**Spende für Kaffee**](https://www.paypal.com/donate/?business=ACU26RPTCA44S&no_recurring=0&item_name=Dieses+Projekt+und+der+Service+kann+nur+durch+eure+Spenden+finanziert+werden.&currency_code=EUR)

Vielen Dank für deine Unterstützung! 🙌

