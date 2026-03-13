# AC Dimmer Project

This project implements an **AC lamp dimmer** using an AVR microcontroller and TRIAC phase control.

The system allows the user to control the brightness of an incandescent lamp and run different lighting effects.

The firmware was developed as part of a **Microcontrollers course project** and demonstrates the use of interrupts, ADC reading, and AC phase control.

---

## Features

The dimmer has **four operating modes**.

### Manual Mode

- Manual brightness control  
- **5 intensity levels**  
- Can be controlled using **push buttons or a potentiometer**

### Fade Mode

- The brightness gradually increases to the maximum  
- Then gradually decreases to the minimum  
- Repeats continuously creating a **smooth lighting effect**

### Flash Mode

- The lamp alternates between **ON and OFF**  
- The user can select the interval time  
- Adjustable from **1 to 5 seconds**

### Timer Mode

- The lamp stays **ON for a selected time**  
- Adjustable from **5 to 10 seconds**  
- After the countdown, the system returns to **Manual Mode**

---

## Hardware

This project uses the following hardware components:

- **AVR Microcontroller — ATmega328P**
- **TRIAC** for AC power control
- **MOC3021 optocoupler** for TRIAC triggering
- **4N35 optocoupler** for zero-cross detection
- **16x2 LCD Display (HD44780 compatible)**
- **3 Push Buttons**
- **Potentiometer (Analog input)**
- **12 VAC Incandescent Lamp**
- **12 V Transformer**

---

### Project Schematic

The circuit used in this project was designed using **SimulIDE**, an open-source real-time electronic circuit simulator that allows the interaction between microcontroller firmware and hardware components.

Using SimulIDE, it was possible to simulate the entire dimmer system, including the microcontroller, TRIAC control circuit, and user interface components.

<p align="center">
  <a href="Circuit Schematic.png">
    <img src="Circuit Schematic.png" alt="Circuit Schematic" width="650">
  </a>
</p>

---

## Circuit Explanation

The circuit is composed of the following main blocks.

### Zero-Cross Detection

An optocoupler is used to detect the moment when the AC waveform crosses zero volts.

This signal is sent to the microcontroller as an interrupt, allowing precise synchronization with the AC cycle.

### TRIAC Driver

Another optocoupler is used to safely trigger the TRIAC gate.

When the microcontroller sends a pulse through the optocoupler, the TRIAC turns on and allows current to flow to the lamp.

### Phase Control

After detecting the zero-crossing, the microcontroller waits for a programmed delay before triggering the TRIAC.

This delay determines how much of the AC waveform will reach the lamp, controlling the brightness.

### User Interface

The system includes:

- A **16x2 LCD display** to show the current mode and system status
- **Push buttons** for mode selection and manual control
- A **potentiometer** connected to the ADC for analog brightness adjustment

### Load

The load used in the simulation is a **12 VAC incandescent lamp**, whose brightness varies according to the conduction angle controlled by the TRIAC.

<p align="center">
  <a href="Circuito-Dimmer-V1.sim1">
    <img src="https://img.shields.io/badge/Open%20SimulIDE%20Project-blue" alt="Open SimulIDE Project">
  </a>
</p>

---

## Libraries

This project uses two support libraries **provided by the course instructor**.

### LCD Library

- Provides functions to control the **16x2 LCD display**
- Handles LCD initialization, cursor positioning, and text printing
- Used to show the current operating mode and brightness level

### ADC Library

- Provides functions to read the **Analog-to-Digital Converter (ADC)** of the AVR
- Used to read the potentiometer value
- The ADC value is converted into brightness levels for the dimmer

<p align="center">
  <a href="ADC.h">
    <img src="https://img.shields.io/badge/ADC%20Library-blue" alt="ADC Library">
  </a>
  <a href="LCD.h">
    <img src="https://img.shields.io/badge/LCD%20Library-blue" alt="LCD Library">
  </a>
</p>

---

## Author

Developed by **Davi Han Ko**  
Microcontrollers Course Project