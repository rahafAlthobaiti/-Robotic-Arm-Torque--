# 🤖 Robotic Arm Torque Calculation and Servo Motor Selection

This document presents torque analysis and servo motor selection for a 3-joint robotic arm designed to lift payloads of 1–2 kg.

---

## 🧮 1. Torque Calculation for Each Joint

### ✅ Arm Specifications

| Component         | Length / Mass         |
|------------------|------------------------|
| Link 1           | 15 cm (0.15 m)         |
| Link 2           | 10 cm (0.10 m)         |
| Gripper Segment  | 4 cm (0.04 m)          |
| Payload          | 1 kg (then 2 kg)       |
| Arm Mass (est.)  | ~0.3 kg at 0.075 m     |

> 🔎 **Total reach from base to gripper:** 0.15 + 0.10 + 0.04 = **0.29 m**

---

### ⚙️ Case 1: Lifting a 1 kg Payload

#### 🔹 Joint 3 *(Gripper only lifts payload)*

\[
\text{Torque} = 1 \times 9.81 \times 0.04 = \boxed{0.3924\ \text{Nm}}
\]

#### 🔹 Joint 2 *(Lifts payload + gripper)*

\[
1 \times 9.81 \times 0.10 = \boxed{0.981\ \text{Nm}}
\]

#### 🔹 Joint 1 *(Lifts payload + entire arm)*

- Payload torque:  
  \[
  1 \times 9.81 \times 0.25 = 2.4525\ \text{Nm}
  \]
- Arm torque:  
  \[
  0.3 \times 9.81 \times 0.075 = 0.2207\ \text{Nm}
  \]
- **Total torque:**  
  \[
  2.4525 + 0.2207 = \boxed{2.6732\ \text{Nm}}
  \]

---

### ⚙️ Case 2: Lifting a 2 kg Payload

#### 🔹 Joint 3

\[
2 \times 9.81 \times 0.04 = \boxed{0.7848\ \text{Nm}}
\]

#### 🔹 Joint 2

\[
2 \times 9.81 \times 0.10 = \boxed{1.962\ \text{Nm}}
\]

#### 🔹 Joint 1

- Payload torque:  
  \[
  2 \times 9.81 \times 0.25 = 4.905\ \text{Nm}
  \]
- Arm torque (same):  
  \[
  = 0.2207\ \text{Nm}
  \]
- **Total torque:**  
  \[
  4.905 + 0.2207 = \boxed{5.1257\ \text{Nm}}
  \]

---

## 🔧 2. Suitable Servo Motor Selection

### ⚠️ Use **1.5× torque margin** to ensure dynamic safety and motor health.

| Joint     | Required Torque (Nm) | Suggested Torque | Recommended Servo                          |
|-----------|----------------------|------------------|---------------------------------------------|
| Joint 1 (2kg) | ~5.13              | ≥ 6–8 Nm         | [JX CLS-HV7346MG – 6.4 Nm](https://www.robotshop.com/products/jx-cls-hv7346mg-digital-servo-46kgcm) |
| Joint 2 (2kg) | ~1.96              | ≥ 3 Nm           | [ATO 30 kg·cm Servo – ~3 Nm](https://www.ato.com/30-kg-cm-high-torque-servo-motor-6v) |
| Joint 3 (2kg) | ~0.78              | ≥ 1 Nm           | [TowerPro MG995 – ~1.0 Nm](https://www.adafruit.com/product/1142) |

---

## ❓ 3. Can the Same Motors Be Used for 2 kg Payload?

✅ **Yes — with gear reduction.**

### 🌀 Gear Example:
- A **3 Nm servo** with **2:1 gear ratio** will deliver:
  \[
  3 \times 2 = 6 \text{ Nm (torque)},\ \text{but only 0.5× speed}
  \]

---

## ⚠️ 4. Drawbacks of Using Gears

| Drawback         | Explanation                                     |
|------------------|-------------------------------------------------|
| 🔥 Heat buildup  | Motors may overheat under prolonged torque load |
| 🐢 Slower motion | Gear reduction decreases joint speed            |
| ⚡️ Power usage  | Increased torque = higher current draw           |
| 🛠️ Wear         | Gears (especially plastic) degrade over time    |
| ⚖️ Heavier arm  | Gearboxes add structural mass                    |
| 🎯 Less precision | Backlash may reduce positioning accuracy       |

---

## 💡 5. Alternative Design Solutions

- Use **stronger servo motors** from the beginning
- **Shorten link lengths** to reduce required torque
- Build the arm with **lightweight materials**
- Use **planetary gearboxes** (compact, efficient)
- Add **counterweights** to reduce torque on base

---

## 📌 Formula Reference

\[
\text{Torque} = \text{Mass} \times \text{Gravity} \times \text{Distance}
\]

✅ All calculations ensure motors are selected with sufficient safety margin for both **static** and **dynamic** operation.

---

> ⚙️ *Proper torque calculation and servo selection lead to safer, more efficient, and longer-lasting robotic arm designs.*
