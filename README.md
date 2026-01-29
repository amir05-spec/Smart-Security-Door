# 🛡️ Smart Security Door: Intelligent Access & Safety System

**Smart Security Door** is a high-performance embedded safety system built on the **STM32F446RE (Otak Kecil Board)**. [cite_start]It features real-time environmental monitoring, motion-based greetings, and an interrupt-driven emergency alert system—all managed through optimized register-level logic. [cite: 234, 369]

---

## ✨ Key Features

* [cite_start]**Multi-Sensor Intelligence** – Seamlessly integrates an MQ-2 Smoke Sensor and FC-51 IR Motion Sensor. [cite: 369, 372]
* [cite_start]**Priority-Based Emergency Logic** – Smoke detection takes absolute priority, triggering an immediate continuous alarm and "Fire" visual alert. [cite: 261, 344]
* [cite_start]**Interactive Human Detection** – Provides a friendly visual greeting ("HI") on the 7-segment display when motion is detected. [cite: 263, 350]
* [cite_start]**Interrupt-Driven Doorbell** – Utilizes **EXTI1** mapping to provide a manual calling bell that responds instantly to user interaction. [cite: 266, 356, 405]
* [cite_start]**Dual 7-Segment Feedback** – Custom-coded subroutines to display status codes like "F1" (Fire) and "H1" (Hi). [cite: 238, 386, 387]
* [cite_start]**Atomic Register Optimization** – Bypasses heavy libraries to use direct **MODER**, **IDR**, and **ODR** register access for ultra-fast response. [cite: 239, 251, 253]

---

## 🛠 How It Works

1. **Sensing Stage** – The system continuously polls PA0 (Smoke) and PA1 (Motion). [cite_start]Both sensors utilize internal pull-up resistors for active-low logic. [cite: 337, 341, 372]
2. **Priority Processing** – The STM32 evaluates inputs. If smoke is detected, it overrides all other states to enter Emergency Mode. [cite_start]If clear, it checks for motion or doorbell activity. [cite: 261, 349, 350]
3. [cite_start]**Actuation Stage** – The system executes modular subroutines to update the dual 7-segment displays (PC0–PC15), LEDs (PB12–PB15), and the active buzzer (PD2). [cite: 334, 335, 381]
4. [cite_start]**Interrupt Handling** – A push-button press on PB1 triggers an asynchronous interrupt (EXTI), updating a `button_pressed` flag to toggle the buzzer as a calling bell instantly. [cite: 345, 364, 411]



---

## 📊 Logic & Feedback Table

| Input Condition | Buzzer (PD2) Behavior | 7-Seg Display | LED Status |
| --- | --- | --- | --- |
| **🔥 Smoke Detected** | 🔊 Continuous Alarm | `F1` (Fire) | 🔴 ON |
| **🚶 Motion Detected** | 🔇 Silent | `H1` (Hi) | 🟢 ON |
| **🔔 Button Pressed** | 🎵 Calling Bell | (State Based) | (State Based) |
| **🏠 Idle Mode** | 🔇 Silent | 🌑 OFF | 🌑 OFF |

[cite_start][cite: 353]

---

## 🚀 Potential Upgrades

* **Biometric Authentication** – Integrate an R307 optical fingerprint sensor for secure, keyless entry.
* **IoT Remote Monitoring** – Add an **ESP8266** module to send "Fire Alert" notifications to a smartphone via MQTT.
* **Electronic Lock Actuation** – Connect a 12V Solenoid Door Bolt via a relay module to physically lock or unlock the door based on authentication.
* **LCD System Log** – Replace or supplement the 7-segment display with an I2C LCD to show detailed event timestamps.

---

## 🎯 Why This Project?

* [cite_start]**Embedded Mastery** – Demonstrates a deep understanding of the ARM Cortex-M4 architecture and register-level programming. [cite: 234, 242]
* [cite_start]**Real-Time Reliability** – Showcases the advantage of Interrupt-Based handling over Polling for critical user inputs. [cite: 418, 425]
* [cite_start]**Safety First Design** – Implements a logic hierarchy where life-safety (smoke detection) always takes precedence over convenience features. [cite: 261, 349]

---

## 💡 Ideal For

* [cite_start]**Engineering Students** studying SKEE 3223 Microprocessor course at UTM. [cite: 227, 228]
* **Security Developers** building high-speed, reliable hardware security prototypes.
* [cite_start]**STM32 Enthusiasts** exploring EXTI, Subroutine implementation, and GPIO Register control. [cite: 242, 248, 249]
