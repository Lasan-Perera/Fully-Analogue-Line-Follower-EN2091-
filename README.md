# 🤖 Fully Analog Line Following Robot  
### EN2091 – Laboratory Practice and Projects  
**Department of Electronic & Telecommunication Engineering**  
**University of Moratuwa, Sri Lanka**

---

## 📌 Project Overview
This project presents the **design and implementation of a fully analog line-following robot** capable of tracking a **3 cm wide white line on a black surface** — **without using any microcontroller or software**.

Unlike typical digital implementations (Arduino, STM32, ESP32), this robot relies **entirely on analog signal processing**, shifting complexity from software to **hardware design and control theory**.

<img width="1536" height="1024" alt="IMG_0676" src="https://github.com/user-attachments/assets/6e78b79c-e1f7-468d-8f66-a1bdf9d60fc1" />
---

## 🎯 Key Objectives
- 🚫 No microcontrollers or programmable logic  
- 🔁 Continuous-time analog feedback control  
- 📐 Accurate line tracking using weighted sensor summation  
- ⚡ Smooth motor control using analog PWM generation  

---

## 🧠 System Architecture
The robot is composed of **three main analog subsystems**:

### 👁️ Optical Sensing
- **TCRT5000 IR sensor array (8 sensors)**
- Detects reflectivity differences between white line and black background
- Produces **analog voltage outputs proportional to line position**

### 🧮 Analog Signal Processing
- **LM324N quad operational amplifiers**
- Used for:
  - Signal amplification
  - Weighted summation
  - Error signal generation
  - PD control implementation

### ⚙️ Motor Actuation
- **L293D motor driver**
- Drives DC gear motors using analog PWM
- Internal clamp diodes protect against motor back-EMF

---

## 🧩 Control Methodology
### 📊 Error Signal Generation
- Sensors are symmetrically placed
- Error voltage is generated as:
  -Error = (Weighted Right Sensors) − (Weighted Left Sensors)
- Enables smooth proportional correction based on deviation

### 🎚️ PD Controller (Analog)
- **Proportional (P)**: Corrects position error
- **Derivative (D)**: Dampens oscillations
- Integral term omitted for dynamic motion system

---

## 🔄 PWM Generation (Fully Analog)
- 🟢 **Triangular Waveform Generator (TWG)** using:
- Non-inverting Schmitt Trigger
- Op-amp Integrator
- ⚖️ Comparator converts control voltage into PWM
- 🧷 Diode ensures unipolar PWM output for motor driver

---

## 🔋 Power Management
Multiple regulated voltage rails ensure stable operation:

| Rail | Purpose |
|----|----|
| +5V A | Sensor circuitry |
| +6V M | Motors |
| ±5V | Analog op-amps |
| ±6V | Motor driver & op-amps |

- LEDs indicate active rails
- Switches allow selective power enabling (debug-friendly)

---

## 🧱 PCB Design
- **4-layer PCB** for noise immunity and signal integrity

### 🧾 Layer Stackup
1. **Top** – High-speed signals  
2. **Inner 1** – Solid GND plane  
3. **Inner 2** – Power planes  
4. **Bottom** – Motor power routing  

This layout significantly reduces EMI and analog noise.

---

## 🛠️ Mechanical Design
- Compact four-legged chassis
- Custom motor brackets for precise alignment
- Top-mounted enclosure with:
- Potentiometers
- Switches
- External Li-Po battery holder

---

## 🧪 Simulation & Testing
- 🔬 **LTspice simulations** for:
- PWM generation
- TWG stability
- 🧰 Breadboard testing using:
- Oscilloscope
- Bench power supply
- 📈 Verified smooth PWM and stable tracking

---

## 👥 Team Neural Nexus
| Name | Contribution |
|----|----|
| **Lasan Perera** | Sensor array, soldering, power system |
| **Isitha Dinujaya** | PD controller, documentation, enclosure |
| **Dulana Pitiwaduge** | PCB design, power system, TWG |
| **Deneth Priyadarshana** | Motor control, debugging, TWG |

👨‍🏫 **Supervisor**: Mr. Tharusha Sihan  

---

  


