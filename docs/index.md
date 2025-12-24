# 🟢 NeoPixel Einsteiger-Tutorial mit CircuitPython  
## Adafruit Metro ESP32-S3

Dieses Dokument ist ein **vollständiges, eigenständiges Markdown-Tutorial**  
und kann direkt mit einem **Static Site Generator** (z. B. MkDocs, Docusaurus, Hugo)  
verwendet werden.

Zielgruppe: **Absolute Anfänger**

---

## 📌 Überblick

In diesem Tutorial lernst du:

- Wie NeoPixel-LEDs grundsätzlich funktionieren
- Wie man sie mit **CircuitPython** steuert
- Wie man
  - 🔹 einen Strip mit **einer Farbe**
  - 🔹 einen Strip mit **mehreren Farben**
  - 🔹 **zwei Strips gleichzeitig**
  - 🔹 **Blinkeffekte**
  - 🔹 **Breathing-/Atmeffekte**
  umsetzt

### Verwendete LEDs
- **Externer NeoPixel-Strip mit 4 LEDs**
- **Eingebaute NeoPixel-LED (1 LED) auf dem Metro ESP32-S3**

👉 **Regel:**  
Wenn nur **ein Strip** verwendet wird, ist es **immer der externe Strip mit 4 LEDs**.  
Die eingebaute LED wird nur **zusätzlich** oder **separat** genutzt.

---

## 🧰 Voraussetzungen

### Hardware
- Adafruit **Metro ESP32-S3**
- NeoPixel-LED-Strip mit **4 LEDs**
- USB-Kabel

### Software
- **CircuitPython** auf dem Board installiert
- Datei `neopixel.mpy` im Ordner `/lib`

```text
CIRCUITPY/
│
├── code.py
└── lib/
    └── neopixel.mpy
````

---

## 🔌 Anschlüsse

| Bauteil                 | Pin      |
| ----------------------- | -------- |
| Externer NeoPixel-Strip | GPIO5    |
| Eingebaute NeoPixel-LED | NEOPIXEL |

---

## 🧠 Grundlagen: Was ist ein NeoPixel?

* Jede LED enthält einen eigenen Controller
* LEDs werden **in Reihe** angesteuert
* Farben werden mit **RGB-Werten** gesetzt

### RGB-Farben

| Farbe | RGB               |
| ----- | ----------------- |
| Rot   | `(255, 0, 0)`     |
| Grün  | `(0, 255, 0)`     |
| Blau  | `(0, 0, 255)`     |
| Weiß  | `(255, 255, 255)` |
| Aus   | `(0, 0, 0)`       |

---

# 1️⃣ Ein Strip – eine Farbe (4 LEDs)

Alle LEDs des externen Strips leuchten in derselben Farbe.

```python
import board
import neopixel
import time

PIXEL
```
