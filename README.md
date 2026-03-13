# {AC DIMMER PROJECT}

## First Version:

This project implements an **AC lamp dimmer** using an AVR microcontroller and TRIAC phase control.<br>
The system allows the user to control the brightness of an incandescent lamp and run different lighting effects.

The firmware was developed as part of a **Microcontrollers course project** and demonstrates the use of interrupts, ADC reading, and AC phase control.<br>

---

## Features

The dimmer has **four operating modes**:

**Manual Mode**
- Manual brightness control
- 5 intensity levels
- Can be controlled using buttons or a potentiometer

**Fade Mode**
- The brightness gradually increases to the maximum
- Then gradually decreases to the minimum
- Repeats continuously creating a smooth lighting effect

**Flash Mode**
- The lamp alternates between ON and OFF
- The user can select the interval time
- Adjustable from **1 to 5 seconds**

**Timer Mode**
- The lamp stays ON for a selected time
- Adjustable from **5 to 10 seconds**
- After the countdown, the system returns to manual mode

---

## Hardware

This project uses the following hardware components:

- **AVR Microcontroller**
- **TRIAC** for AC power control
- **Optocoupler for TRIAC triggering**
- **Optocoupler for zero-cross detection**
- **16x2 LCD Display**
- **3 Push Buttons**
- **Potentiometer (Analog input)**
- **12VAC Incandescent Lamp**
- **12V Transformer**

---

## How It Works

The brightness control is performed using **AC phase control**.

The system works as follows:

1. The circuit detects the **zero-crossing** of the AC waveform.
2. An interrupt is triggered in the microcontroller.
3. The firmware waits a specific delay.
4. After the delay, a pulse is sent to the **TRIAC gate**.
5. The delay determines how much power is delivered to the lamp.

Smaller delay → brighter lamp  
Larger delay → dimmer lamp

---

## Project Structure
<p align="center">
  <a href="main.c">
    <img src="https://img.shields.io/badge/main-blue" alt="main">
  </a>
</p>
<p align="center">
  <a href="ADC.h">
    <img src="https://img.shields.io/badge/ADC-blue" alt="ADC">
  </a>
</p>
<p align="center">
  <a href="LCD.h">
    <img src="https://img.shields.io/badge/LCD-blue" alt="LCD">
  </a>
</p>  
<br>

---

## Notes

The **LCD** and **ADC** libraries used in this project were provided by the course instructor and were not developed by the author of this repository.

---

## Author

Developed by **Davi Han Ko**  
Microcontrollers Course Project