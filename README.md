# Real Time Sensor Monitoring Station using Periodic Task Scheduler

A real-time embedded system built on the **LPC2129 (ARM7)** microcontroller that continuously monitors multiple sensors and reports their readings to a serial terminal. A timer interrupt drives a periodic task scheduler so each sensor is serviced at a regular interval.

## Features

- Monitors temperature, light (LDR), flame and vibration sensors
- Periodic task scheduling using a hardware timer interrupt
- ADC-based analog sensor reading
- Live sensor output over UART to a serial terminal
- Continuous monitoring in the main loop

## Hardware Used

| Component | Purpose |
|-----------|---------|
| LPC2129 microcontroller | Main controller |
| Temperature sensor | Measures ambient temperature |
| LDR sensor | Measures light intensity |
| Flame sensor | Detects fire or flame |
| Vibration sensor | Detects vibration or shock |
| USB-to-serial / RS232 module | UART link to the PC |

## Software and Tools

- **Language:** Embedded C
- **IDE / Compiler:** Keil uVision
- **Serial terminal:** Any terminal (e.g. Tera Term, PuTTY)

## Project Structure

| File | Description |
|------|-------------|
| `main.c` | Main program with the monitoring loop |
| `header.h` | Common declarations, macros and function prototypes |
| `timer_intr.c` | Timer setup and interrupt handler for the periodic scheduler |
| `adc_driver.c` | ADC driver for reading analog sensors |
| `uart_driver.c` | UART driver for serial communication |

## How It Works

1. The system initializes the timer, ADC and UART
2. A hardware timer generates periodic interrupts that act as the scheduler tick
3. On each scheduled interval, the sensors are read
4. `main()` runs an infinite `while(1)` loop that continuously monitors the sensors
5. Sensor values and alerts are sent over UART to the serial terminal

## How to Build and Run

1. Open the project in **Keil uVision**.
2. Select the **LPC2129** device and add all the `.c` and `.h` files.
3. Build the project to generate the `.hex` file.
4. Flash the `.hex` file to the LPC2129 (for example with Flash Magic).
5. Connect the board to the PC through the UART serial module.
6. Open a serial terminal and set the baud rate to match your `uart_driver.c` settings (e.g. 9600).
7. Reset the board to see the live sensor readings.

## Author

**Abdul**  
GitHub: [abdul-embedded](https://github.com/abdul-embedded)
