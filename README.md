# ✈️ Automatic Baggage Handling System Using PLC

A PLC and HMI based **Automatic Baggage Handling System (ABHS)** designed to automate baggage transportation, weight checking, overweight handling, metal detection, routing, sorting, counting, and operator monitoring.

## 👨‍💻 Author

**Manthan Sabalpara**  
B.Tech. Electronics & Computer Engineering  
Nirma University

**University:** Nirma University
**Department:** Electronics & Computer Engineering
**Course:** Factory Automation (2EC604)
**Academic Year:** 2025–26

---

## 🎯 Project Objective

The objective of this project is to develop an automated airport baggage handling system using a **Mitsubishi FX5U PLC** and **GT Designer3 HMI**.

The system is designed to:

* Detect incoming baggage
* Count baggage automatically
* Measure baggage weight
* Detect overweight baggage
* Calculate overweight fines
* Handle overweight acceptance/rejection
* Perform metal detection
* Divert baggage using conveyor diverters
* Route baggage to three destination gates
* Maintain gate-wise baggage counts
* Detect baggage-count mismatch
* Provide real-time HMI monitoring
* Display conveyor and routing status

---

## ⚙️ Technologies Used

* **PLC:** Mitsubishi FX5U
* **PLC Programming:** GX Works3
* **HMI:** Mitsubishi GT Designer3
* **Simulation:** GX Simulator3 / GT Simulator3
* **Programming Languages:**

  * Ladder Diagram (LD)
  * Function Block Diagram (FBD)
  * Structured Text (ST)

---

## 🏭 System Workflow

```text
                    ┌───────────────┐
                    │ Baggage Entry │
                    └───────┬───────┘
                            ↓
                    ┌───────────────┐
                    │ Bag Detection │
                    └───────┬───────┘
                            ↓
                    ┌───────────────┐
                    │ Weight Check  │
                    └───────┬───────┘
                            ↓
                  ┌───────────────────┐
                  │ Weight > 20 kg ?  │
                  └───────┬─────┬─────┘
                         NO    YES
                          ↓      ↓
                       Continue Fine Calculation
                                ↓
                         Accept / Reject
                                ↓
                    ┌───────────────┐
                    │ Metal Detector│
                    └───────┬───────┘
                            ↓
                    ┌───────────────┐
                    │ Gate Selection│
                    └───────┬───────┘
                            ↓
                  ┌─────────┼─────────┐
                  ↓         ↓         ↓
               Gate 1    Gate 2    Gate 3
```

---

## 🔌 Main PLC I/O

| Address | Function                       |
| ------- | ------------------------------ |
| X0      | Start                          |
| X1      | Stop                           |
| X2      | Main baggage sensor            |
| X3      | Weight station sensor          |
| X4      | Weight/reset input             |
| X5      | Gate 1 sensor                  |
| X6      | Gate 2 sensor                  |
| X7      | Diverter/metal detection input |
| X8      | Overweight input               |
| X9      | Gate selection                 |
| X10     | Gate 1 counting sensor         |
| X11     | Gate 2 counting sensor         |
| X12     | Gate 3 counting sensor         |
| Y0      | Main conveyor                  |
| Y1      | Overweight indication          |
| Y2      | Diverter                       |
| Y9–Y14  | Gate routing                   |
| Y15     | Baggage mismatch alarm         |

---

## 💾 Important PLC Registers

| Device | Purpose                    |
| ------ | -------------------------- |
| D0     | Current baggage weight     |
| D1     | Destination gate number    |
| D2     | Excess weight              |
| D3     | Calculated fine            |
| D10    | Conveyor animation pattern |
| D11    | Total baggage count        |
| D15    | Gate 1 count               |
| D16    | Gate 2 count               |
| D17    | Gate 3 count               |
| C0     | Main baggage counter       |
| C1     | Gate 1 counter             |
| C2     | Gate 2 counter             |
| C3     | Gate 3 counter             |

---

## 🖥️ HMI

The HMI was developed using **GT Designer3**.

The interface provides:

* Main conveyor visualization
* Baggage weight display
* Fine calculation display
* Diverter direction indication
* Gate status
* Baggage counters
* Alarm indication
* Conveyor animation
* System monitoring

### HMI Preview

Add screenshots of your HMI here:

```text
Images/hmi_main.png
Images/hmi_weight.png
Images/hmi_sorting.png
```

---

## 🧠 PLC Programming

The same control system was implemented using three IEC 61131-3 programming languages:

### 1. Ladder Diagram

Used primarily for:

* Start/stop control
* Conveyor interlocks
* Sensor logic
* SET/RST operations
* Timers
* Counters
* Diverter control

### 2. Function Block Diagram

Used to represent the control system using interconnected functional blocks such as:

* AND / OR
* SET / RESET
* TON
* CTU
* EQ
* ADD
* SUB
* MUL
* CML

### 3. Structured Text

Used for:

* Conditional logic
* Weight calculations
* Fine calculation
* Gate selection
* Reconciliation logic
* Conveyor animation

---

## 🔄 Baggage Reconciliation

The system maintains:

* Main baggage count: `C0`
* Gate 1 count: `C1`
* Gate 2 count: `C2`
* Gate 3 count: `C3`

The PLC compares the total number of bags routed through the gates with the total detected baggage.

If a mismatch occurs, the system activates the baggage mismatch alarm.

---

## 🎨 Conveyor Animation

A PLC-generated bit pattern is used to create conveyor movement on the HMI.

The animation uses:

```text
H0AAAA → 1010 1010 1010 1010
```

The pattern is complemented periodically using the PLC clock bit and transferred to multiple output groups connected to the HMI conveyor indicators.

This creates a visual moving-conveyor effect without requiring a dedicated animation engine.

---

## 📂 Project Files

### PLC Programs

* [Ladder Diagram](PLC/Ladder/project.pdf)
* [Function Block Diagram](PLC/FBD/projectFBD.pdf)
* [Structured Text](PLC/Structured_Text/ProjectST.pdf)

### HMI

* [GT Designer3 HMI Screens](HMI/project_HMI.pdf)

### Documentation

* [Complete Project Report](Report/Airport_Baggage_Handling_System_Report.pdf)

---

## 📚 Literature Review

The project was developed with reference to research and technical literature related to:

* Airport baggage handling systems
* PLC-based conveyor automation
* Automated sorting systems
* Industrial HMI design
* PLC programming using IEC 61131-3 languages
* Baggage reconciliation systems

Detailed literature review and references are included in the project report.

---

## 🚀 Future Improvements

Possible future improvements include:

* RFID/barcode based automatic baggage identification
* SCADA integration
* IoT based monitoring
* Industrial communication using CC-Link/Ethernet
* Predictive maintenance
* Automatic baggage tracking
* Database-based baggage history
* Integration with airport baggage management systems

---

## 👥 Contributors

**Manthan Sabalpara**
B.Tech. Electronics & Computer Engineering
Nirma University

**Jenil Gabani**
B.Tech. Electronics & Computer Engineering
Nirma University

---

## ⭐ Project Highlights

> **PLC + HMI + Conveyor Automation + Weight Detection + Metal Detection + Diverter Sorting + Baggage Reconciliation**

This project demonstrates the application of industrial automation concepts to an airport baggage handling scenario.
