
# ✨ AVR1: A Microcontroller is Just a Wardrobe with Switches

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Web Serial API](https://img.shields.io/badge/Web%20Serial-API-blue)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Serial_API)
[![AVR Assembly](https://img.shields.io/badge/AVR-Assembly-orange)](https://avr-libc.nongnu.org/)

**Program an Arduino (ATmega328P) directly from your browser. No IDE, no drivers, no installation. Just a USB cable and two lines of code.**

👉 **[Try it live: costycnc.it/avr1](https://costycnc.github.io/avr-compiler-js/)** 👈

![Hero Screenshot](https://raw.githubusercontent.com/costycnc/avr1/main/screenshot.png) <!-- You'll need to add a real screenshot -->

## 🗄️ The Core Idea

> A microcontroller is a wardrobe. Each drawer (register) controls something. Put a `1` in the right compartment (bit) — and a real LED lights up.

This project strips away all complexity. You don't learn abstract functions or libraries first. You directly manipulate the memory of an **ATmega328P** (Arduino Uno/Nano) using AVR assembly.

- **Drawer 4 (DDRB)** = Direction (Input or Output)
- **Drawer 5 (PORTB)** = Value (0V or 5V)

## 🚀 How It Works

1.  **Plug in** your Arduino (Uno or Nano) via USB.
2.  **Open** the web app (Chrome or Edge only).
3.  **Write** two instructions:
    ```asm
    sbi 4,5   ; Set bit 5 of drawer 4 -> PB5 as OUTPUT
    sbi 5,5   ; Set bit 5 of drawer 5 -> Set PB5 HIGH -> LED ON!
    ```
4.  **Click "Assemble & Upload"**.
5.  **Watch the LED** on pin 13 turn on. That's it.

## ✨ Features

- **⚡ Zero Installation:** Works entirely in the browser using the Web Serial API.
- **🧠 Visual Metaphor:** The "wardrobe with drawers" makes registers and bits intuitive, even for non-programmers.
- **📝 Real AVR Assembly:** Write actual `sbi`, `cbi`, `out`, `in` instructions. No pseudo-code.
- **🎮 Interactive Simulator:** Click the bits in the "Drawer 5" compartment to see the LED respond instantly.
- **📱 Responsive Design:** Works on desktop and tablets (requires Chrome/Edge for USB).

## 🛠️ What You Need

| Hardware | Software |
| :--- | :--- |
| Arduino Uno, Nano, or any ATmega328P board | Google Chrome or Microsoft Edge |
| USB Cable (Data, not charge-only) | An internet connection |
| Built-in LED (pin 13) or external + resistor | That's it! |

## 🧑‍🏫 For Absolute Beginners

If you've never programmed in your life, this is for you.

1.  **You don't need to know** what a variable, function, or loop is.
2.  **You just need to know** that `sbi 5,5` puts a `1` in the 5th compartment of the 5th drawer.
3.  **Result:** The LED turns on. You understand *why*.

The rest (timers, interrupts, PWM) will come naturally once you see the machine as a set of drawers.

## 🤔 Why ATmega328P?

- 📖 **Best documented chip in the world** – millions of examples and a huge community.
- 🏛️ **The DNA of all modern chips** – Once you learn UART, I2C, SPI, and Timers here, you know them everywhere.
- 🔍 **Transparent** – Every "drawer" is visible and editable. Modern MCUs hide everything.
- 💰 **Costs €2-3** – Buy an Arduino Nano clone; break it, buy another.
- 🏠 **Real hardware from day one** – LEDs, relays, motors, sensors. No theory-first.

## 📂 Project Structure

```
avr1/
├── index.html          # The complete web app (single file)
├── style.css           # (embedded) Wardrobe design & animations
├── script.js           # (embedded) Interactive slots & UI logic
└── README.md           # This file
```

## 🔧 Local Development

Since the app uses the Web Serial API, it must be served over HTTPS or `localhost`.

1.  Clone the repo:
    ```bash
    git clone https://github.com/costycnc/avr1.git
    cd avr1
    ```
2.  Serve locally (e.g., with Python):
    ```bash
    python3 -m http.server 8000
    ```
3.  Open `http://localhost:8000` in Chrome/Edge.

## 🧪 Testing

You can test the interactive drawer without an Arduino:
- Just click any compartment in the "Drawer 5 (PORTB)" view. The simulated LED will respond immediately.

## 🤝 Contributing

Contributions are welcome! Areas to explore:
- Support for more AVR instructions (`out`, `in`, `rjmp`).
- Add a visual "oscilloscope" for PWM pins.
- Translate the tutorial into other languages.

1.  Fork the project.
2.  Create your branch (`git checkout -b feature/amazing`).
3.  Commit your changes (`git commit -m 'Add something amazing'`).
4.  Push (`git push origin feature/amazing`).
5.  Open a Pull Request.

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

## 🌟 Acknowledgements

- The amazing [AVR-LibC](https://avr-libc.nongnu.org/) team.
- Web Serial API W3C specification.
- Arduino community for making hardware accessible.

---

## 💬 FAQ

**Q: I know nothing about programming. Can I do this?**
**A:** Yes. This tutorial was designed for carpenters, mechanics, artists, and kids. No prior knowledge required.

**Q: Do I need to memorize `DDRB`, `PORTB`, `PB5`?**
**A:** No. They're just the names of the drawers. You'll learn them naturally by using the system, not by studying a datasheet.

**Q: Does it work with Arduino UNO?**
**A:** Yes. Also Nano, Pro Mini, and any clone with the ATmega328P.

**Q: After this, can I still use the Arduino IDE?**
**A:** Absolutely. And you'll understand it much better. When you write `digitalWrite(13, HIGH)`, you'll know it's just putting a `1` in compartment 5 of drawer 5.

---

**Made with ❤️ by [costycnc.it](https://costycnc.it)** – *Unlocking the magic of microcontrollers, one drawer at a time.*
```

---

### 📸 Consiglio per l'immagine (screenshot)

Sostituisci il link `https://raw.githubusercontent.com/.../screenshot.png` con un'immagine reale. Ti consiglio di fare uno screenshot che mostri:

1.  Il "guardaroba" (wardrobe) con i cassetti.
2.  Il cassetto 5 ingrandito.
3.  Il LED che si illumina.
4.  Le due linee di codice.

Puoi caricare l'immagine nella root del repository e chiamarla `screenshot.png`.    rcall pause
    cbi 5,0          ; Set PB0 LOW
    ldi r17,11       ; Delay for 0.5ms
    rcall pause
    ret

pause:
    dec r16
    brne pause
    dec r17
    brne pause
    ret
```

---

## 🎮 Pulse Protocol Explained

| Pulse Type | HIGH Time | LOW Time | Purpose |
|------------|-----------|----------|---------|
| **W2** | 1500 µs | 500 µs | Start sequence / Sync |
| **W1** | 500 µs | 500 µs | Command data bits |

### What the code sends:

```
[W2][W2][W2][W2] ── [W1][W1][W1][W1][W1][W1][W1][W1][W1][W1]
     (sync)              (10 pulses = FORWARD)
```

---

## 🔌 Hardware Connection (IMPORTANT!)

The code uses `sbi 5,0` and `cbi 5,0` which control **PB0**.

| Assembly Code | Port | Bit | Arduino Pin |
|---------------|------|-----|-------------|
| `sbi 5,0` | PORTB | 0 | **Pin 8** |

### Connection Diagram:

```
┌───────────┐                    ┌─────────────┐
│  Arduino  │                    │  RC Car     │
│           │                    │  Receiver   │
│       8   ├────────────────────► Antenna     │
│     (PB0) │                    │  (Signal)   │
│           │                    │             │
│      GND  ├────────────────────► GND         │
└───────────┘                    └─────────────┘
```

> ⚠️ **NOT** pin 13. **NOT** the LED. The signal goes directly to the antenna!

---

## 📊 Command Reference

| W1 Pulses | Command |
|-----------|---------|
| 10 | Forward |
| 16 | Forward + Turbo |
| 22 | Turbo |
| 28 | Turbo + Forward + Left |
| 34 | Turbo + Forward + Right |
| 40 | Backward |
| 46 | Backward + Right |
| 52 | Backward + Left |
| 58 | Left |
| 64 | Right |

---

## 🔧 How to test it?

Use my **online ASM compiler**:

🔗 **https://costycnc.github.io/avr-compiler-js/**

Quick steps:
1. Go to the website
2. Copy-paste the ASM code
3. Click **"Assemble"**
4. Connect Arduino via USB
5. Click **"Upload"** (select Uno/Nano)
6. Connect Arduino Pin 8 to RC car antenna
7. The car goes FORWARD!

**No IDE installation. No drivers. No libraries. No magic.**

---

## ⚠️ Why stack, call/ret, push/pop are MANDATORY

| Disaster | Cause |
|----------|-------|
| **Boeing 737 MAX (2019)** – 346 deaths | Stack corruption. Push without pop, call without ret. |
| **Toyota Unintended Acceleration** | Stack exhausted from recursive calls. |

### The 4 commandments:

1. ✅ Every `call` must have a `ret`
2. ✅ Every `push` must have a `pop`
3. ✅ Know your stack limits
4. ✅ Otherwise, you're a **public hazard**

---

## 📊 Arduino IDE vs This Approach

| Feature | Arduino IDE | This ASM + Tool |
|---------|-------------|-----------------|
| Installation | Yes (IDE + drivers) | **No** - works in browser |
| Libraries | Many, hide everything | **None** - you see the registers |
| Control | digitalWrite() | Direct port access (`sbi`, `cbi`) |
| Learning | Softer, less transparent | **Direct** - learn how it REALLY works |
| File size | KBs | **Bytes** |

---

## 🎯 Summary

| What is this? | Assembly code that controls an RC car using pulses directly to the antenna |
|---------------|---------------------------------------------------------------------------|
| Which pin? | **Arduino Pin 8 (PB0)** → RC car antenna |
| Who is it for? | Beginners, students, hobbyists who want to learn how things REALLY work |
| Do I need to install anything? | **NO** – just a browser and a USB cable |

---

## 🔗 Related

- **[AVR online compiler](https://costycnc.github.io/avr-compiler-js/)** – write and upload AVR code from your browser
- **[GRBL 1.1 for unipolar motors](https://github.com/costycnc/grbl-1.1-unipolar)** – custom firmware for unipolar stepper motors
- **[Inkscape Hello World](https://github.com/costycnc/inkscape-1.0-python-hello-world-extension-costycnc)** – minimal Inkscape extension tutorial

---

🌐 **[costycnc website](https://costycnc.github.io/)** – didactic labs + production CNC tools

---

**Pure Assembly. No magic. Your RC car obeys your code.** 🎯🔥
```

