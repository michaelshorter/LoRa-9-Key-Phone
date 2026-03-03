# LoRaKeY 

A 'Phone' built on Arduino Nano that sends predefined words and custom sentences over LoRa  using a 12-button keypad and a small OLED display.

---

## Overview

LoRaKeY is a low-power, portable messaging node designed for off-grid or long-range communication scenarios. Press a key to instantly transmit a word, or build a short sentence using sentence mode — all without needing a phone, internet, or cell network.

---

## Hardware Required

Arduino Nano 
4×3 Matrix Keypad 
Heltec LoRa Module 
SSD1306 OLED Display 


---

## Wiring Summary

### Keypad
| Keypad Pin | Arduino Pin |
|---|---|
| Row 1–4 | D10, D9, D8, D7 |
| Col 1–3 | D6, D5, D4 |

### Heltec LoRa Module (SoftwareSerial)
| Heltec Pin | Arduino Pin |
|---|---|
| TX → RX | D3 |
| RX ← TX | D2 |

### OLED Display (I²C)
| OLED Pin | Arduino Pin |
|---|---|
| SDA | A4 |
| SCL | A5 |

---

## Dependencies

Install the following libraries via the Arduino Library Manager:

- [Keypad](https://github.com/Chris--A/Keypad)
- [Adafruit GFX Library](https://github.com/adafruit/Adafruit-GFX-Library)
- [Adafruit SSD1306](https://github.com/adafruit/Adafruit_SSD1306)
- `SoftwareSerial` *(built into Arduino IDE)*
- `Wire` *(built into Arduino IDE)*

---

## Key Mappings

### Instant Send (outside sentence mode)

| Key | Sends |
|---|---|
| `1` | I |
| `2` | go |
| `3` | now |
| `4` | you |
| `5` | come |
| `6` | later |
| `7` | yes |
| `8` | maybe |
| `9` | no |

### Control Keys

| Key | Function |
|---|---|
| `*` | Enter sentence mode — start building a message |
| `#` | Send the current sentence (in sentence mode) |
| `0` | Cancel / clear the current sentence |

---

## How to Use
1. Press `*` to enter sentence mode. The display will prompt you.
2. Press number keys `1`–`9` to append words to your sentence.
3. Press `#` to transmit the full sentence.
4. Press `0` at any time to cancel and clear the message.

### Receiving Messages
Incoming messages from the Heltec module are automatically displayed on the OLED and printed to the Serial monitor.

---

## Configuration

At the top of the sketch, you can adjust the following:

```cpp
const String NANO_ID = "03";  // Change this to uniquely identify each node
```

To add or change word mappings, edit the `convertToWord()` function:

```cpp
String convertToWord(char key) {
  switch (key) {
    case '1': return "I";
    case '2': return "go";
    // Add your own words here...
  }
}
```

---


