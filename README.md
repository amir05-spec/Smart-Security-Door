# 🛡️ Smart Security Door: Intelligent Access & Safety System

**Smart Security Door** is a high-performance embedded safety system built on the **STM32F446RE (Otak Kecil Board)**. It features real-time environmental monitoring, motion-based greetings, and an interrupt-driven emergency alert system—all managed through optimized register-level logic.

---

## ✨ Key Features

* **Multi-Sensor Intelligence** – Seamlessly integrates an MQ-2 Smoke Sensor and FC-51 IR Motion Sensor for comprehensive perimeter monitoring.
* **Priority-Based Emergency Logic** – Smoke detection takes absolute priority, triggering an immediate continuous alarm and "Fire" (F1) visual alert.
* **Interactive Human Detection** – Provides a friendly visual greeting ("HI") on the 7-segment display when motion is detected.
* **Interrupt-Driven Doorbell** – Utilizes **EXTI1** mapping for the push button (SW4) to ensure the calling bell responds instantly without polling lag.
* **Dual 7-Segment Feedback** – Custom-coded subroutines to manage multiplexed displays for status codes like "F1" (Fire) and "H1" (Hi).
* **Atomic Register Optimization** – Bypasses heavy abstraction layers to use direct **MODER**, **IDR**, and **ODR** register access for ultra-fast hardware response.

---

## 🛠 How It Works

1. **Sensing Stage** – The system continuously monitors PA0 (Smoke) and PA1 (Motion). Both sensors utilize active-low logic for high reliability.
2. **Priority Processing** – The STM32 evaluates inputs in real-time. If smoke is detected, it overrides all other states to enter Emergency Mode. If clear, it checks for motion or doorbell activity.
3. **Actuation Stage** – The system executes modular subroutines to update the dual 7-segment displays (PC0–PC15), LEDs (PB12–PB15), and the active buzzer (PD2).
4. **Interrupt Handling** – A push-button press on PB1 triggers an asynchronous interrupt (EXTI), ensuring the calling bell sounds immediately even if the main loop is processing other tasks.



---

## 📊 Logic & Feedback Table

| Input Condition | Buzzer (PD2) Behavior | 7-Seg Display | LED Status |
| --- | --- | --- | --- |
| **🔥 Smoke Detected** | 🔊 Continuous Alarm | `F1` (Fire) | 🔴 ON (PB12-15) |
| **🚶 Motion Detected** | 🔇 Silent | `H1` (Hi) | 🟢 ON (PB12-15) |
| **🔔 Button Pressed** | 🎵 Calling Bell | (State Based) | (State Based) |
| **🏠 Idle Mode** | 🔇 Silent | 🌑 OFF | 🌑 OFF |

---

## 🚀 Potential Upgrades

* **Biometric Authentication** – Integrate a fingerprint sensor or keypad for secure, keyless entry.
* **IoT Remote Monitoring** – Add an **ESP8266** module to send "Fire Alert" notifications to a smartphone via Wi-Fi.
* **Electronic Lock Actuation** – Connect a 12V Solenoid Door Bolt via a relay to physically lock/unlock the door based on authentication.
* **Analog Sensitivity** – Use **ADC (Analog-to-Digital Converter)** to detect precise smoke density levels for multi-stage warnings.

---

## 🎯 Why This Project?

* **Embedded Mastery** – Demonstrates a deep understanding of the ARM Cortex-M4 architecture and register-level programming.
* **Real-Time Reliability** – Showcases the advantage of Interrupt-Based handling over Polling for critical user inputs.
* **Safety First Design** – Implements a logic hierarchy where life-safety (smoke detection) always takes precedence over convenience features.

---

## 💡 Ideal For

* **Engineering Students** studying SKEE 3223 Microprocessor course at UTM.
* **Security Developers** building high-speed, reliable hardware security prototypes.
* **STM32 Enthusiasts** exploring EXTI, Subroutine implementation, and GPIO Register control.
