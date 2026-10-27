<img width="1536" height="1024" alt="ChatGPT Image 2025  okt  24  00_03_55" src="https://github.com/user-attachments/assets/d21d9aed-7023-44c4-a628-8dffebe2a87b" />
<img width="1289" height="768" alt="image" src="https://github.com/user-attachments/assets/5052bebf-a475-41b0-ab57-48fe65c8fd59" />

CHILI NEVELDE 1.0 — TELJES DOKUMENTÁCIÓ & ÚTMUTATÓ
ESP8266 Bekötési Rajz, Festési Útmutató, C++ Forráskód & Működési Elv

# Chili Nevelde 1.0 – ESP8266 Okos Növénygondozó Rendszer

Ez a tárhely egy ESP8266 (NodeMCU/Wemos D1 mini) mikrokontrollerre épülő, automatizált növénynevelő állomás forráskódját tartalmazza. A szoftver alkalmas a környezeti tényezők monitorozására, automatikus vagy manuális beavatkozásra, valamint az adatok távoli elérésére.

## Főbb funkciók és lehetőségek

*   **Többnyelvű reszponzív webfelület:** Beépített, mobilra optimalizált sötét módú (Dark Mode) HTML oldal grafikus kijelzőkkel (Canvas Gauges) az adatok élő követéséhez.
*   **Kétoldalú vezérlés:** Váltás a teljesen automatizált és a kézi (manuális) üzemmódok között.
*   **Periféria kezelés:** Vízpumpa időkorlátos működtetése és ventilátor vezérlése a határértékek alapján.
*   **Adafruit IO (MQTT) integráció:** A szenzoradatok percenkénti továbbítása felhőbe az adatok távoli naplózásához.
*   **Soros porti parancsértelmező:** A berendezés teljes körű konfigurálása és működtetése soros monitoron keresztül küldött parancsokkal.
*   **EEPROM alapú memóriakezelés:** A beállítások (küszöbértékek, kalibrációs offsetek, fix IP-címek, nyelvi beállítás) áramtalanítás után is megmaradnak.
*   **Biztonság és stabilitás:** Jelszóval védett beállítási felület, beépített hardveres újraindítás (Watchdog) a WiFi kapcsolat elvesztése esetén.

## Támogatott perifériák és lábkiosztás

*   **DHT22 Szenzor (D1 láb):** Hőmérséklet és relatív páratartalom mérése.
*   **Fényérzékelő modul (D2 láb):** Digitális fény/sötétség detektálás.
*   **Analóg talajnedvesség mérő (A0 láb):** A föld szárazságának ellenőrzése.
*   **Vízpumpa relé (D6 láb):** Aktív LOW vezérlésű kimenet a locsoláshoz.
*   **Ventilátor relé (D7 láb):** Aktív LOW vezérlésű kimenet a szellőztetéshez.

## Szükséges Arduino könyvtárak

A kód sikeres fordításához telepíteni kell az alábbi könyvtárakat az Arduino IDE-ben:
*   `ESP8266WiFi` és `ESP8266WebServer` (az ESP8266 alapcsomag része)
*   `DHT sensor library` (Adafruit)
*   `Adafruit MQTT Library`

## Soros porti (Serial) parancsok listája

A soros monitoron keresztül (115200 baud mellett) az alábbi főbb parancsok adhatóak ki:
*   `AM` / `MM`: Automata / Manuális mód bekapcsolása.
*   `P1` / `P0`: Pumpa kézi indítása és leállítása.
*   `F1` / `F0`: Ventilátor kézi indítása és leállítása.
*   `MTxxx`: Talajnedvesség küszöbérték beállítása (0-1023).
*   `TDxx.x`: Hőmérséklet küszöbérték beállítása Celsius-fokban.
*   `HMxx`: Páratartalom küszöbérték beállítása (%).
*   `PMxxx`: Maximális pumpálási idő másodpercben (biztonsági időkorlát).
*   `IPxxx.xxx.xxx.xxx`: Fix IP-cím beállítása (mentés után újraindul).
*   `LGHU` / `LGEN`: Rendszernyelv átváltása magyar vagy angol nyelvre.

## Telepítés és indítás

1.  Nyisd meg a `.ino` fájlt az Arduino IDE szoftverben.
2.  Írd át a kód elején található `ssid` és `password` változókat a saját WiFi hálózatod adataira.
3.  Add meg az `IO_USERNAME` és `IO_KEY` értékeit az Adafruit IO fiókod alapján.
4.  Vlaszd ki az ESP8266 alapú kártyádat, majd töltsd fel a kódot.
5.  A soros monitoron látható IP-címet beírva a böngészőbe érheted el a vezérlőfelületet (alapértelmezett adminisztrációs jelszó: `0331`).


Bekötés & Pinout
Működés & Használat
3D Festési Útmutató
Arduino C++ Forrás
ESP8266 (NodeMCU / Wemos D1 Mini) Lábkiosztás:
A hardver az alábbi szabványos mikrokontroller lábakat használja az érzékelők és az aktív LOW relék vezérlésére:

D1 (GPIO 5)
NodeMCU / D1
DHT22 Digitális Hő- és Páramérő
Hőmérséklet és relatív páratartalom (30 mp-es minta)
D2 (GPIO 4)
NodeMCU / D1
Fényérzékelő Modul (LDR Digitális)
Fény meglétének érzékelése (LOW = Világos, HIGH = Sötét)
D6 (GPIO 12)
NodeMCU / D1
Vízpumpa Relé Modul (Relay 1)
Aktív LOW (Relay ON = LOW, Relay OFF = HIGH), max 30s
D7 (GPIO 13)
NodeMCU / D1
Szellőztető Venti Relé (Relay 2)
Aktív LOW hűtés/párátlanítás (Temp > 28°C / Hum > 70%)
A0 (ADC 0)
NodeMCU / D1
Talajnedvesség Szenzor (Analóg)
Analóg olvasás (0-1023). Száraz: ~700, Nedves: ~300
VCC / 3.3V / 5V
NodeMCU / D1
Tápellátás & GND
Közös GND a relékkel és a mikrokontrollerrel

Hozzávalók - XPS lapok, hullámpala, ragasztó
<img width="864" height="1184" alt="Gemini_Generated_Image_px4bobpx4bobpx4b" src="https://github.com/user-attachments/assets/c6e7ee19-c22f-4fa6-9cc8-87337ee0a540" />

<img width="1536" height="1024" alt="ChatGPT Image 2025  okt  24  00_03_55" src="https://github.com/user-attachments/assets/d21d9aed-7023-44c4-a628-8dffebe2a87b" />
<img width="1289" height="768" alt="image" src="https://github.com/user-attachments/assets/5052bebf-a475-41b0-ab57-48fe65c8fd59" />

CHILI NURSERY 1.0 — COMPLETE DOCUMENTATION & GUIDE
ESP8266 Wiring Diagram, Enclosure Finishing Guide, C++ Source Code & Working Principle

# Chili Nursery 1.0 – ESP8266 Smart Plant Care System

This repository contains the source code for an automated plant nursery workstation based on an ESP8266 (NodeMCU / Wemos D1 mini) microcontroller. The firmware monitors ambient and soil conditions, provides automatic and manual actuator control, and supports remote telemetry access.

## Key Features & Capabilities

*   **Multilingual Responsive Web UI:** Built-in mobile-optimized dark mode HTML dashboard featuring graphical gauges (Canvas Gauges) for real-time telemetry tracking.
*   **Dual-Mode Operation:** Seamless toggling between fully automated and manual override modes.
*   **Actuator Control & Safety:** Timeout-protected water pump dosing and threshold-driven ventilation fan operation.
*   **Adafruit IO (MQTT) Integration:** Periodic (1-minute interval) cloud telemetry transmission for remote data logging and visualization.
*   **Serial CLI Interpreter:** Full system configuration, diagnostic inspection, and control via Serial Monitor commands.
*   **EEPROM Non-Volatile Storage:** System configuration (setpoints, calibration offsets, static IP parameters, language preferences) persists across power cycles and reboots.
*   **Safety & Stability:** Password-protected administrative settings interface and hardware Watchdog / auto-reboot recovery upon Wi-Fi connection loss.

## Supported Peripherals & Pinout

*   **DHT22 Sensor (Pin D1):** Ambient temperature and relative humidity measurement.
*   **Light Sensor Module (Pin D2):** Digital ambient light/darkness detection.
*   **Analog Soil Moisture Sensor (Pin A0):** Soil dryness / volumetric moisture level monitoring.
*   **Water Pump Relay (Pin D6):** Active LOW relay output for automated irrigation.
*   **Ventilation Fan Relay (Pin D7):** Active LOW relay output for forced-air cooling/dehumidification.

## Required Arduino Libraries

To successfully compile the project in the Arduino IDE, install the following libraries via the Library Manager:
*   `ESP8266WiFi` and `ESP8266WebServer` (included with the ESP8266 Arduino Core package)
*   `DHT sensor library` (Adafruit)
*   `Adafruit MQTT Library`

## Serial Command Reference

Via the Serial Monitor (baud rate: **115200 baud**), the following commands can be issued:
*   `AM` / `MM`: Switch to Automatic / Manual mode.
*   `P1` / `P0`: Manually start / stop the water pump.
*   `F1` / `F0`: Manually start / stop the ventilation fan.
*   `MTxxx`: Set soil moisture threshold (0–1023).
*   `TDxx.x`: Set temperature threshold in degrees Celsius.
*   `HMxx`: Set relative humidity threshold (%).
*   `PMxxx`: Maximum pump runtime limit in seconds (safety overflow cutoff).
*   `IPxxx.xxx.xxx.xxx`: Configure static IP address (triggers reboot upon saving).
*   `LGHU` / `LGEN`: Switch system language to Hungarian (`HU`) or English (`EN`).

## Installation & Setup

1.  Open the `.ino` project file in the Arduino IDE.
2.  Configure your local Wi-Fi credentials in the `ssid` and `password` variables at the beginning of the file.
3.  Enter your `IO_USERNAME` and `IO_KEY` credentials obtained from your Adafruit IO account.
4.  Select your ESP8266 board model and the appropriate COM port, then compile and flash the firmware.
5.  Check the assigned IP address printed in the Serial Monitor and open it in a web browser to access the control panel (default administrator password: `0331`).

---

## Wiring & Pinout

### ESP8266 (NodeMCU / Wemos D1 Mini) Pinout Table:
The system interfaces with sensors and active LOW relay modules using the following standard GPIO mapping:

| Pin | MCU Identifier | Connected Peripheral / Module | Technical Description & Parameters |
| :--- | :--- | :--- | :--- |
| **D1** (GPIO 5) | NodeMCU / D1 | DHT22 Digital Temperature & Humidity Sensor | Ambient temperature and RH% monitoring (30s sampling interval) |
| **D2** (GPIO 4) | NodeMCU / D1 | Digital Light Sensor (LDR Module) | Ambient light presence (`LOW` = Bright / Light, `HIGH` = Dark) |
| **D6** (GPIO 12) | NodeMCU / D1 | Water Pump Relay Module (Relay 1) | Active LOW (`Relay ON = LOW`, `Relay OFF = HIGH`), max runtime 30s |
| **D7** (GPIO 13) | NodeMCU / D1 | Exhaust Fan Relay Module (Relay 2) | Active LOW cooling/dehumidification (Temp > 28°C / Humidity > 70%) |
| **A0** (ADC 0) | NodeMCU / D1 | Analog Soil Moisture Sensor | 10-bit analog readout (0–1023). Dry: ~700, Wet: ~300 |
| **VCC / 3.3V / 5V** | NodeMCU / D1 | Power Rail & Common Ground (GND) | Shared common ground between MCU, relay channels, and power supply |

### Enclosure Construction Materials - XPS foam boards, corrugated plastic sheet, mounting adhesive
<img width="864" height="1184" alt="Gemini_Generated_Image_px4bobpx4bobpx4b" src="https://github.com/user-attachments/assets/c6e7ee19-c22f-4fa6-9cc8-87337ee0a540" />
