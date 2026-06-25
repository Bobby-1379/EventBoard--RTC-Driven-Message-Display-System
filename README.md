# Event Board: RTC-Driven Message Display System

An embedded system project based on the **LPC2148 ARM7 Microcontroller** that automatically displays scheduled event messages on a 16x2 LCD using the internal RTC (Real-Time Clock). The system supports secure administration through password-protected keypad access, allowing users to edit RTC settings and enable/disable event messages. 

---

## 📌 Features

* ⏰ RTC-based automatic event scheduling
* 📺 Scrolling message display on 16x2 LCD
* 🔒 Password-protected Admin Mode
* ⌨️ Keypad-based menu navigation
* 🕒 RTC Time and Date editing
* 📝 Enable/Disable scheduled messages
* 🌡️ Room temperature monitoring using LM35 sensor
* 🟢 Green LED indication during active event display
* 🔴 Red LED indication during idle mode
* 🔔 Optional buzzer support
* 📊 Digital clock display when no event is active

---

## 🛠 Hardware Requirements

* LPC2148 ARM7 Microcontroller
* 16x2 LCD Display
* Matrix Keypad
* LM35 Temperature Sensor
* LEDs (Red & Green)
* Push Button/Switch
* Buzzer (Optional)



---

## 💻 Software Requirements

* Embedded C
* Keil µVision Compiler
* Flash Magic



---

## 📂 Project Workflow

The system continuously reads the RTC and compares the current time with predefined event schedules.

### Event Active

When the RTC time matches an enabled event:

* Display event message on LCD
* Scroll long messages
* Turn ON Green LED
* Show countdown/remaining display time

### No Event Active

When no scheduled event is available:

* Display current time and date
* Display room temperature
* Turn ON Red LED




---

## 🔐 Admin Mode

Admin Mode is entered by detecting a long press on the switch.

### Admin Menu

```text
------ ADMIN MENU ------
1. RTC EDIT
2. EVENT MSG EDIT
3. EXIT
------------------------
```



---

## ⏲ RTC Edit Menu

```text
1.H  2.M  3.S  4.DATE
5.DAY 6.MONTH 7.YEAR
8.EXIT
```

Supported ranges:

| Parameter | Range     |
| --------- | --------- |
| Hour      | 0 - 23    |
| Minute    | 0 - 59    |
| Second    | 0 - 59    |
| Date      | 1 - 31    |
| Month     | 1 - 12    |
| Year      | 0 - 4095  |
| Day       | SUN - SAT |

The user selects a parameter, modifies its value through the keypad, validates the range, and updates the RTC registers.



---

## 📝 Event Configuration

Users can enable or disable any of the predefined event messages.

```text
------ EVENT SETTINGS ------
Enter Message Number (1–10)

1. ACTIVATE
2. DEACTIVATE
3. EXIT
```



---

## 📋 Predefined Events

The system contains 10 predefined messages stored in flash memory.

Example events:

| Time  | Message                             |
| ----- | ----------------------------------- |
| 07:45 | Good Morning! Classes Start Soon    |
| 09:45 | ARM Workshop on External Interrupts |
| 10:15 | C Module Theory Exam                |
| 12:45 | Lunch Break                         |
| 17:00 | Revise Today's Class Programs       |
| 17:45 | End of Day – See You Tomorrow       |

Initially, all messages are enabled by default. 

---

## 🔄 System Flow

```text
START
   |
Initialize RTC, LCD, ADC, GPIO
   |
Read RTC Time
   |
Compare with Event List
   |
+--------------------------+
| Event Matched ?          |
+--------------------------+
      |Yes          |No
      v             v
Display Event    Display Clock
Message          + Temperature
      |             |
Green LED ON    Red LED ON
      |
Check Admin Switch
      |
Long Press?
      |
     Yes
      |
Enter Admin Mode
      |
RTC Edit / Event Edit
      |
Return to Main Loop
```

---

## 📺 LCD Display Format

### Normal Mode

```text
12:45:30 MON
25/06/2026 T:28C
```

### Event Mode

```text
[Scrolling Message]

Time Left:
00:02:30
```



---

## 📁 Project Structure

```text
EventBoard/
│
├── main.c
├── rtc.c
├── rtc.h
├── lcd.c
├── lcd.h
├── keypad.c
├── keypad.h
├── adc.c
├── adc.h
├── admin.c
├── event.c
├── event.h
├── buzzer.c
├── buzzer.h
└── README.md
```

---

## 🎯 Learning Outcomes

* Real-Time Clock Programming
* LCD Interfacing
* ADC Programming with LM35
* Keypad Interfacing
* GPIO Control
* Menu-Driven Embedded Applications
* Secure User Access Design
* Event Scheduling Systems
* ARM7 LPC2148 Programming

---

## 🚀 Future Enhancements

* EEPROM storage for custom messages
* UART-based PC configuration
* GSM notification support
* SD Card event database
* Multiple user access levels
* Touchscreen interface

---

## 👨‍💻 Developed Using

* LPC2148 ARM7 MCU
* Embedded C
* Keil µVision
* Flash Magic

---

**Event Board: RTC-Driven Message Display System** provides a complete embedded solution that combines real-time scheduling, secure administration, environmental monitoring, and automated information display in a single ARM-based application. 

