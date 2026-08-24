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
