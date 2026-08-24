CHILI NEVELDE 1.0 — TELJES DOKUMENTÁCIÓ & ÚTMUTATÓ
ESP8266 Bekötési Rajz, Festési Útmutató, C++ Forráskód & Működési Elv


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
