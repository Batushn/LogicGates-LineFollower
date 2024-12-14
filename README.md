# **4-Sensor Line-Following Robot using Logic Gates**

This repository contains the circuit design and logic implementation for a **Line-Following Robot** built using 4 sensors, logic gates, and DC motors. The robot uses basic **digital logic gates** to determine motor speeds based on sensor input and follows a line efficiently.

---

## **Overview**

This line-following robot utilizes:
- **4 QTR sensors** to detect the position of the line.
- Logic gates (AND, OR, NOT) to process the sensor signals.
- Two **DC motors** controlled via an **H-Bridge Motor Driver** (L293D).
- Two **555 Timer ICs** to generate PWM signals for motor speed control.

The logic gates are implemented using **74HC series ICs**, and the robot adjusts motor speed dynamically to align itself with the line.

---

## **Components**

| Item                      | Quantity |
|---------------------------|----------|
| 10 kΩ Potentiometer        | 2        |
| Diodes (LN4148)           | 4        |
| 74HC04 (NOT Gate IC)       | 1        |
| 74HC32 (OR Gate IC)        | 2        |
| 74HC11 (AND Gate IC)       | 2        |
| DC Motors                 | 2        |
| L293D (H-Bridge Driver)    | 1        |
| 5V Power Input (Or regulate from 12V)           | 1        |
| 12V Power Input           | 1        |
| 5 kΩ Resistor              | 2        |
| 1 kΩ Resistor              | 2        |
| 5 nF Capacitors            | 2        |
| 100 nF Capacitors          | 2        |
| 555 Timer ICs             | 2        |
| Single Channel Cables      | 1m        |


---

## **Circuit Design**
![image](https://github.com/user-attachments/assets/3fbfad0c-2ef7-4000-b345-9272e9a0d539)

The robot consists of two main sections:
1. **Sensor Processing Unit**: 
   - **4 QTR sensors** detect line position and output **binary signals** (0 or 1).
   - These sensor signals are fed into **NOT gates** (inverters), **AND gates**, and **OR gates** to implement the decision-making logic.

2. **Motor Control Unit**:
   - Two **555 Timer ICs** generate PWM signals to control the motor speeds:
     - **33% PWM** for slow speed.
     - **66% PWM** for medium speed.
     - **100% PWM** for full speed.
   - The H-Bridge Motor Driver (L293D) controls the direction and speed of the motors based on the logic output.

---

## **Truth Table**

The robot's logic is designed based on the following truth table:
| S1 | S2 | S3 | S4 | Left Motor | Right Motor | Explanation                        |
|----|----|----|----|------------|-------------|------------------------------------|
| 0  | 0  | 0  | 0  | 0%         | 0%        | No input - robot stops          |
| 0  | 1  | 1  | 0  | 100%       | 100%         | Robot moves forward straight|
| 0  | 0  | 1  | 0  | 100%       | 66%         | Robot adjusts slightly to the right  |
| 0  | 1  | 0  | 0  | 66%       | 100%         | Robot adjusts slightly to the left  |
| 0  | 0  | 1  | 1  | 100%        | 33%        | Robot turns slowly to the left    |
| 1  | 1  | 0  | 0  | 33%        | 100%        | Robot turns slowly to the left    |
| 1  | 1  | 1  | 0  | 0%       | 100%          | Robot turns sharply left           |
| 0  | 1  | 1  | 1  | 100%       | 0%          | Robot turns sharply right           |
| 1  | 0  | 0  | 0  | 0%       | 100%          | Robot turns sharply left           |
| 0  | 0 | 0  | 1  | 100%       | 0%          | Robot turns sharply right           |
| 1  | 1  | 1  | 1  | 0%       | 0%        | Robot stops   |
| 1  | 0  | 0  | 1  | 100%       | 100%        | Robot moves forward straight       |
| 1  | 0  | 1  | 0  | 100%       | 100%        | Robot moves forward straight     |
| 0  | 1  | 0  | 1  | 100%       | 100%        | Robot moves forward straight     |
| 1  | 1  | 0  | 1  | 100%       | 100%        | Robot moves forward straight  |
| 1  | 0  | 1  | 1  | 100%       | 100%        | Robot moves forward straight |


---

## **Working Principle**

1. **Sensor Input**: 
   - The 4 QTR sensors detect the black line and provide binary outputs.
   - Sensor values are processed through logic gates to determine motor actions.

2. **Logic Processing**:
   - **74HC04** ICs (NOT gates) invert signals where necessary.
   - **74HC11** ICs (AND gates) and **74HC32** ICs (OR gates) combine inputs to produce control signals.

3. **Motor Speed Control**:
   - Based on the truth table, the two **555 Timer ICs** generate PWM signals at different duty cycles.
   - These PWM signals adjust motor speeds to steer the robot and keep it aligned with the line.

4. **Motor Driving**:
   - The **L293D H-Bridge Driver** receives the control signals and drives the motors in the desired direction with the appropriate speed.

---

## **How to Build**

### **Steps**:
1. Connect the **4 QTR sensors** to the breadboard and configure them to detect the line.
2. Wire up the **NOT gates (74HC04)**, **AND gates (74HC11)**, and **OR gates (74HC32)** according to the truth table.
3. Implement the **555 Timer ICs** to generate PWM signals for motor speed control.
4. Connect the **L293D Motor Driver** to the motors and integrate it with the PWM outputs.
5. Power the circuit with:
   - **5V** for logic gates and sensors.
   - **12V** for the motors.

6. Test the circuit:
   - Adjust the potentiometers to fine-tune motor speeds.
   - Verify the sensor logic and motor responses against the truth table.

---


## **Usage**

1. Power on the robot with the **5V** and **12V** power lines. You can use a regulator (like LM7805) or L298n's regulator.
2. Place the robot on a line (black tape or track).
3. The robot will:
   - Adjust motor speeds based on sensor inputs.
   - Follow the line smoothly using the predefined logic.

---

## **Features**

- **No Microcontroller**: This robot relies purely on **logic gates** and analog electronics.
- **Dynamic Speed Control**: Motors adjust speeds to correct alignment deviations with potantiometers.
- **Modular Design**: Easily customizable for additional sensors or motors.

---

## **Future Improvements**

- Add more sensors for better precision.
- Turning to the last direction with a flip-flop circuit to prevent crossing the line.

---

## **License**

This project is licensed under the **MIT License**.

---
