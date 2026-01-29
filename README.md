# Smart Security Door System (STM32F4)

[cite_start]An intelligent, microcontroller-based security system designed for real-time monitoring of home safety conditions[cite: 242]. [cite_start]This project integrates smoke detection, human motion sensing, and a manual calling bell using register-level programming on the **STM32F4** platform[cite: 234, 237].

---

## 🚀 Key Features
* [cite_start]**Prioritized Safety:** Smoke detection (MQ-2) takes highest priority, triggering a continuous emergency alarm and a "Fire" (F1) visual alert[cite: 261, 344, 349].
* [cite_start]**Motion Awareness:** Detects human presence (FC-51) and provides a friendly "HI" (H1) greeting on the 7-segment display[cite: 263, 350].
* [cite_start]**Responsive Calling Bell:** Uses **External Interrupts (EXTI)** for the push button (SW4) to ensure immediate response without polling[cite: 241, 405].
* [cite_start]**Modular Codebase:** Implements subroutines for organized control of LEDs, buzzers, and dual 7-segment displays[cite: 240, 335].

---

## 🛠️ Hardware Configuration
[cite_start]The system is built using the **Otak Kecil board** (STM32F446)[cite: 369, 437].

| Component | GPIO Port & Pin | Signal Type | Function |
| :--- | :--- | :--- | :--- |
| **MQ-2 Smoke Sensor** | PA0 | Active Low | [cite_start]Detects fire/hazardous smoke [cite: 372] |
| **FC-51 IR Sensor** | PA1 | Active Low | [cite_start]Detects human presence [cite: 374] |
| **Push Button (SW4)** | PB1 | Active Low (EXTI) | [cite_start]Manual calling bell [cite: 375] |
| **Dual 7-Seg Display** | PC0 - PC15 | Active High | [cite_start]Visual status output (F1, H1) [cite: 380] |
| **Active Buzzer** | PD2 | Active High | [cite_start]Emergency alarm & calling bell [cite: 377, 378] |
| **On-board LEDs** | PB12 - PB15 | Active High | [cite_start]Status indicators [cite: 379] |

---

## ⚙️ Program Logic
[cite_start]The firmware is developed using register-level GPIO configuration for maximum efficiency[cite: 239].

### Operation Modes
1. [cite_start]**Emergency Mode:** If smoke is detected, the buzzer sounds continuously and the display shows **"F1"**[cite: 344, 349].
2. [cite_start]**Greeting Mode:** If no smoke but motion is detected, the display shows **"H1"**[cite: 263, 350].
3. [cite_start]**Manual Mode:** Pressing the button triggers the buzzer (calling bell) immediately via EXTI1[cite: 346, 364].
4. [cite_start]**Idle Mode:** If no inputs are active, the system turns off all displays and indicators[cite: 268, 269].

---

## 📂 Project Structure
* [cite_start]**`/Core`**: Contains the C language source files for Keil uVision[cite: 234].
* [cite_start]**`/Diagrams`**: Circuit schematics designed in KiCad 9.0[cite: 368].
* [cite_start]**`main.c`**: Main program loop and EXTI interrupt handler[cite: 340, 364].

---

## 🎓 Academic Context
* [cite_start]**Course:** SKEE 3223 Microprocessor [cite: 227, 228]
* [cite_start]**Institution:** Universiti Teknologi Malaysia (UTM) [cite: 221]
* **Instructor:** Ir. Ts. [cite_start]Dr. Fauzan Khairi Bin Che Harun [cite: 231]

---

## 📜 License
[cite_start]This project is for educational purposes as part of the Bachelor of Electronic Engineering program[cite: 225].
