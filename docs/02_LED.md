# LEDs 

Die LEDs und den Adafruit Metro ESP32-S3 folgendermaßen verbinden.

- Grau auf GND (0V)
- Lila auf Vin (USB 5V)
- Blau auf 5 (Digital Pin D5)

![verbindungLED-Metro](pics/verbindungLED-Metro.png)

Die LEDs können vom Adafruit Metro ESP32-S3 programmiert und daher verändert werden.
Sie werden auch NeoPixel genannt oder mit der bezeichnung WS2812b. 

## LED - simple eine Farbe

Den Code im Browser Fenster löschen und folgenden code einfügen.
Jetzt sollten alle LEDs in Rot leuchten. 
Wir können in der letzten Zeile alle Farben ausprobieren (255,0,0) mit (0,255,0) oder (0,0,255) ersetzen. 

````python
# ===============================
# NeoPixel Grundbeispiel
# Ein Strip – eine Farbe
# ===============================

import board          # Zugriff auf die Pins des Boards
import neopixel       # NeoPixel Bibliothek
import time           

# -------------------------------
# KONFIGURATION
# -------------------------------

PIXEL_PIN = board.D5      # Pin, an dem der Strip angeschlossen ist
NUM_PIXELS = 4            # Anzahl der LEDs im Strip
BRIGHTNESS = 0.3          # Helligkeit (0.0 – 1.0)

# -------------------------------
# NEOPIXEL OBJEKT ERSTELLEN
# -------------------------------

pixels = neopixel.NeoPixel(
    PIXEL_PIN,
    NUM_PIXELS,
    brightness=BRIGHTNESS,
    auto_write=True       # LEDs aktualisieren sich sofort
)

# -------------------------------
# FARBE SETZEN
# -------------------------------

pixels.fill((255, 0, 0))  # Alle LEDs Rot (Rot, Grün, Blau), die Zahlen 0-255. 
````

## LED - mehre Farben

Hier wird für jede LED eine eigene Farbe angegeben. 
Statt `pixels.fill((255, 0, 0))` also füllen aller LEDs wird jede LED angesporchen mit `pixels[0] = (255, 0, 0)`. 
Die Zahl in den eckicgen klammern [0] ist die Position mit den LEDs, sie startet mit 0 und geht bis 3 (eine weniger als die gesamtanzahl in `NUM_PIXELS = 4`)

````python
# ===============================
# NeoPixel Grundbeispiel
# Ein Strip – eine Farbe
# ===============================

import board          # Zugriff auf die Pins des Boards
import neopixel       # NeoPixel Bibliothek
import time           

# -------------------------------
# KONFIGURATION
# -------------------------------

PIXEL_PIN = board.D5      # Pin, an dem der Strip angeschlossen ist
NUM_PIXELS = 4            # Anzahl der LEDs im Strip
BRIGHTNESS = 0.3          # Helligkeit (0.0 – 1.0)

# -------------------------------
# NEOPIXEL OBJEKT ERSTELLEN
# -------------------------------

pixels = neopixel.NeoPixel(
    PIXEL_PIN,
    NUM_PIXELS,
    brightness=BRIGHTNESS,
    auto_write=True       # LEDs aktualisieren sich sofort
)

# -------------------------------
# FARBE SETZEN
# -------------------------------

pixels[0] = (255, 0, 0)     # LED 0 → Rot
pixels[1] = (0, 255, 0)     # LED 1 → Grün
pixels[2] = (0, 0, 255)     # LED 2 → Blau
pixels[3] = (255, 255, 0)   # LED 3 → Gelb
````

## LED - mehrere Farben mit Schleife

In diesem beispiel geben wir nicht jede LED einzeln an sondern sagen von bis welche LED geändert werden soll.

````python
# ===============================
# NeoPixel Grundbeispiel
# Ein Strip – eine Farbe
# ===============================

import board          # Zugriff auf die Pins des Boards
import neopixel       # NeoPixel Bibliothek
import time           

# -------------------------------
# KONFIGURATION
# -------------------------------

PIXEL_PIN = board.D5      # Pin, an dem der Strip angeschlossen ist
NUM_PIXELS = 4            # Anzahl der LEDs im Strip
BRIGHTNESS = 0.3          # Helligkeit (0.0 – 1.0)

# -------------------------------
# NEOPIXEL OBJEKT ERSTELLEN
# -------------------------------

pixels = neopixel.NeoPixel(
    PIXEL_PIN,
    NUM_PIXELS,
    brightness=BRIGHTNESS,
    auto_write=True       # LEDs aktualisieren sich sofort
)

# -------------------------------
# FARBE SETZEN MIT SCHLEIFE
# -------------------------------

for b in range(1, 3):         # Schleife: b ist eine Variable, "range" is der Bereich mit der 2. und 3. LED. 
    pixels[b] = (0, 255, 0)   # Variable b wird hier eingesetzt Wert für die Position der LED.

````

## LED - Dimmen / Atmen

Mit diesem Code sollen alle LEDs langsam heller werden bis zur maximalen stärke und dann wieder dimmen bis sie ausgehen. 

Den Code im Browser Fenster löschen und folgenden code einfügen.

````python
import board
import neopixel
import time

pixels = neopixel.NeoPixel(
    board.D5,
    NUM_PIXELS = 4
    brightness=0.0,   # Start mit 0 Helligkeit
    auto_write=True
)

while True:
    # Helligkeit hochfahren
    for b in range(0, 100):
        pixels.brightness = b / 100
        pixels.fill((0, 0, 255))  # Blau
        time.sleep(0.02)

    # Helligkeit runterfahren
    for b in range(100, 0, -1):
        pixels.brightness = b / 100
        pixels.fill((0, 0, 255))
        time.sleep(0.02)
````
