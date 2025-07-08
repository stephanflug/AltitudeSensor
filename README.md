# 🛰️ Altitude Sensor

<p align="center"> <img src="https://github.com/stephanflug/AltitudeSensor/blob/main/Logo.png?raw=true" alt="Altitude Sensor Logo" width="300"/> </p> <p align="center"> <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License"/> <img src="https://img.shields.io/badge/Platform-ESP32-green.svg" alt="Platform"/> <img src="https://img.shields.io/badge/Protocol-MQTT-orange.svg" alt="MQTT"/> </p> <p align="center"> <img src="https://github.com/stephanflug/AltitudeSensor/blob/main/Bild.png?raw=true" alt="Sensor Hardware" width="1000" height="500"/> </p>

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

## ✨ Coole Features auf einen Blick

🧠 **Smart Setup via WLAN-Hotspot**  
> Kein Hardcoding nötig! Einfach Gerät einschalten, Hotspot öffnen und SSID + MQTT-Zugang im Browser konfigurieren.

📡 **Live MQTT-Datenübertragung**  
> Temperatur, Luftfeuchtigkeit, Luftdruck und Höhe – alles in Echtzeit über MQTT an dein Smart-Home-System.

🖥️ **OLED-Anzeige integriert**  
> Die wichtigsten Sensordaten immer direkt im Blick – auch ohne Smartphone oder PC.

🔄 **OTA-Updates per Tastendruck**  
> Firmware-Updates direkt per WLAN – ganz ohne Kabel oder PC-Verbindung. Nur lange drücken, fertig.

📏 **Automatisches Höhendelta-Tracking**  
> Das Gerät misst und speichert automatisch die maximale Höhenänderung seit dem letzten Reset.

💾 **Speicher für Maximalwerte und Einstellungen**  
> Alle wichtigen Daten bleiben erhalten – auch nach Stromverlust oder Neustart.

🧰 **Super einfacher Web-Flasher**  
> Keine IDE, keine Treiberprobleme. Flash direkt im Browser:  
> [➡️ Zum Flasher](https://flugbuch.gltdienst.home64.de/flasher/)

🪛 **Open Hardware – Platinen-Layout inklusive**  
> Platine selbst bauen oder bestellen – die Gerber-Dateien sind bereits vorbereitet!

---
## 📐 Neues Platinen-Layout

Ein eigenes **Platinen-Layout** wurde erstellt!  
Du kannst jetzt ganz einfach die **Gerber-Datei** verwenden und die gewünschte Anzahl der Platinen direkt und bequem online bei [JLCPCB](https://jlcpcb.com/) bestellen. 🚀

### 📁 Gerber-Dateien zum Download  
[📦 Gerber_HoehensensorV4.zip](https://github.com/stephanflug/AltitudeSensor/blob/main/Platinen%20Layout/Gerber_HoehensensorV4.zip)

### 🖼️ Vorschau der Platine

![Platine Vorschau](https://github.com/stephanflug/AltitudeSensor/raw/main/Platinen%20Layout/Bilder/3.png)

---

💡 **Tipp:**  
- Einfach die ZIP-Datei bei JLCPCB hochladen und die Platinen individuell konfigurieren.  
- JLCPCB bietet schnelle Fertigung zu günstigen Preisen.  
- Ideal, um schnell und unkompliziert deine Platinen in professioneller Qualität zu erhalten.


## ⚙️ Hardwareanschluss

| Funktion        | GPIO-Pin |
|-----------------|----------|
| I2C SDA         | 5        |
| I2C SCL         | 6        |
| Boot Button     | 9        |
| Status LED      | 8        |

---

## 🚀 Installation & Nutzung

1. **Verbinde Sensoren und Display** mit den oben angegebenen Pins.

2. **Firmware auf den ESP32c3 flashen**  
   👉 Dafür kann bequem der **Web ESP Flasher** verwendet werden:  
   [https://flugbuch.gltdienst.home64.de/flasher/](https://flugbuch.gltdienst.home64.de/flasher/)

   ### 🛠️ Hinweis zum Flash-Vorgang(nur wenn das Gerät nicht angezeigt wird)

   - Halte während des Verbindungsaufbaus im Flasher-Tool die **Boot-Taste** gedrückt.  
   - Drücke **kurz die Reset-Taste** am ESP32, während die Boot-Taste weiterhin gedrückt ist.  
   - Danach kannst du die **Boot-Taste loslassen**.  
   - Nun sollte die Verbindung hergestellt und die Firmware übertragen werden.

3. Beim ersten Start (Lang drücken (≥ 3 Sek.):** Start des Setup-Hotspots.)öffnet sich ein WLAN-Hotspot **„Altitude Sensor“** für die Konfiguration.

4. Im Browser den Hotspot aufrufen und **SSID**, **Passwort**, **MQTT-Daten** sowie **Sensor-ID** eingeben.

5. Nach dem Speichern erfolgt ein automatischer Neustart und die Verbindung zum WLAN.

6. Die **Sensordaten werden über MQTT gesendet** und auf dem **OLED-Display angezeigt**.

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

