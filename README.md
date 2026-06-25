# Event Board - RTC Driven Message Display System using LPC2148

## Overview

Event Board is an embedded application developed on the **LPC2148 (ARM7TDMI-S)** microcontroller that automatically displays scheduled event messages on a **16x2 LCD** using the internal **Real-Time Clock (RTC)**.

The system continuously monitors the current time and displays predefined messages when their scheduled time occurs. When no event is active, the LCD shows the current date, time, day, and room temperature measured through an **LM35 temperature sensor**.

An **Admin Mode** can be accessed through an external interrupt and password-protected keypad interface, allowing authorized users to modify RTC settings and enable/disable event messages.

---

## Features

* RTC-based event scheduling
* Automatic event message display
* Scrolling LCD message support
* Password-protected Admin Mode
* RTC Time editing
* RTC Date editing
* Day-of-week editing
* Enable/Disable individual event messages
* LM35 temperature monitoring using ADC
* Red LED indication during idle mode
* Green LED indication during event display mode
* External Interrupt (EINT0) based admin access
* 4x4 Matrix Keypad interface
* 16x2 LCD interface

---

## Hardware Used

* LPC2148 ARM7 Microcontroller
* 16x2 LCD
* 4x4 Matrix Keypad
* LM35 Temperature Sensor
* Red LED
* Green LED
* Push Button (EINT0)
* RTC Crystal (32.768 kHz)

---

## Software Tools

* Embedded C
* Keil uVision
* Flash Magic

---

## Project Structure

```text
EventBoard/
│
├── Event_Board_Main.c      # Main application
├── rtc.c / rtc.h           # RTC driver
├── lcd.c / lcd.h           # LCD driver
├── kpm.c / kpm.h           # Keypad driver
├── adc.c / adc.h           # ADC driver for LM35
├── settings.c / settings.h # Admin menu & settings
├── delay.c / delay.h       # Delay routines
├── pin_connect_block.c     # Pin configuration
│
├── defines.h
├── types.h
├── rtc_defines.h
├── lcd_defines.h
├── kpm_defines.h
└── interrupts_defines.h
```

---

## System Workflow

```text
START
  |
Initialize LCD
Initialize RTC
Initialize Keypad
Initialize ADC
  |
Read Current RTC Time
  |
Compare Time with Event List
  |
+----------------------+
| Event Match Found ?  |
+----------------------+
      | Yes
      v
Display Scrolling Event
Green LED ON
Red LED OFF
      |
      No
      |
      v
Display:
Time
Date
Day
Temperature
Red LED ON
Green LED OFF
      |
Check Admin Interrupt
      |
Repeat
```

---

## Default Event Messages

The firmware contains 10 predefined events:

| Time  | Event                               |
| ----- | ----------------------------------- |
| 07:45 | Good Morning! Classes Start Soon    |
| 09:45 | ARM Workshop on External Interrupts |
| 10:00 | ARM Kit Issue Time                  |
| 10:15 | C Module Lab Exam                   |
| 11:15 | C Module Theory Exam                |
| 12:45 | Lunch Break                         |
| 13:45 | C Programming Session               |
| 15:15 | Break Reminder                      |
| 17:00 | Revise Today's Programs             |
| 17:45 | End of Day                          |

Each event can be enabled or disabled from Admin Mode.

---

## LCD Display

### Normal Mode

```text
12:30:45 MON

15/07/2025 28C
```

### Event Mode

```text
C Programming Session
in Classroom No.2
```

(Long messages automatically scroll across the LCD.)

---

## Admin Mode

Admin mode is entered through the **EINT0 external interrupt**.

### Default Password

```text
1234
```

### Admin Menu

```text
1.Time  2.Date
3.Day   4.Msg
5.Exit
```

---

## RTC Settings

Users can edit:

* Hour
* Minute
* Second
* Date
* Month
* Year
* Day of Week

Changes are written directly to LPC2148 RTC registers.

---

## Event Management

For each message:

```text
Select Message Number
       |
1.Enable
2.Disable
```

This allows individual event scheduling without modifying firmware.

---

## LED Status

| LED       | Status                          |
| --------- | ------------------------------- |
| Red LED   | No active event                 |
| Green LED | Event currently being displayed |

---

## Keypad Layout

```text
7 8 9 /
4 5 6 *
1 2 3 -
C 0 = +
```

Functions:

* Numeric entry
* Password input
* Menu navigation
* Data editing

---

## Build Instructions

1. Open project in Keil uVision.
2. Select LPC2148 target device.
3. Build the project.
4. Generate HEX file.
5. Flash using Flash Magic.
6. Connect LCD, Keypad, RTC crystal, LM35, and LEDs.
7. Reset the board.

---

## Future Improvements

* EEPROM-based message storage
* Custom message editing from keypad
* GSM notification support
* UART PC configuration
* SD Card event database
* Multiple user accounts
* RTC battery backup monitoring

---

## Author

**Event Board - RTC Driven Message Display System**
Developed using **LPC2148 ARM7**, Embedded C, RTC, LCD, ADC, Keypad, and External Interrupts for real-time event scheduling and display.
