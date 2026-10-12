# CNC Milling Table | Servo Motor Sizing & Electrical Design

**Academic project — Electromechanical Engineering, ENSAM Meknès (2025–2026)**  
*Dimensionnement et commande du servomoteur d'une table de fraiseuse à commande numérique*

## Overview

This project covers the **theoretical sizing and electrical design of a servo-driven linear axis** for a CNC milling machine. It combines motion and load calculations, servomotor/drive selection, and AutoCAD electrical documentation for the power circuit, command circuit, and terminal connections.

The objective is to select a servo system capable of moving a **567 kg milling table** during cutting and rapid return, while accounting for cutting forces, friction, acceleration, and the motor's thermal duty cycle.

### Mechanical architecture

```text
Delta ASDA-B3-L servo drive
              |
              v
      BLAC servomotor
              |
              v
      Gear reducer (3:1)
              |
              v
 Ball screw (12.7 mm/rev)
              |
              v
      CNC milling table
```

## Design specifications

| Parameter | Value |
| --- | ---: |
| Table mass | 567 kg |
| Travel distance | 0.40 m |
| Cutting feed speed | 0.08 m/s |
| Return speed | 0.20 m/s |
| Cutting force | 11,340 N |
| Friction coefficient | 0.10 |
| Acceleration / deceleration time | 0.02 s |
| Dwell time | 3.0 s |
| Gear reduction ratio | 3:1 |
| Ball-screw lead | 12.7 mm/rev |
| Ball-screw efficiency | 90% |

## Engineering workflow

1. **Motion analysis:** Determine required motor speeds for the cutting and return strokes.
2. **Inertia calculation:** Refer the rotor, reducer, ball screw, and translating table inertias to the motor shaft.
3. **Torque calculation:** Evaluate load torque, friction torque, acceleration torque, and peak torque.
4. **Thermal sizing:** Compute the RMS torque over the complete operating cycle.
5. **Component selection:** Compare the calculated requirements with the selected Delta servomotor and drive ratings.
6. **Electrical documentation:** Prepare the power/drive wiring, relay-based command circuit, and terminal schedule in AutoCAD.

## Key sizing results

| Calculated quantity | Result |
| --- | ---: |
| Motor speed during cutting | 1,134 rpm |
| Motor speed during return | 2,835 rpm |
| Equivalent inertia at motor shaft | 1.496 × 10⁻³ kg·m² |
| Cutting-direction resisting torque | 8.914 N·m |
| Return-direction resisting torque | 0.424 N·m |
| Peak required torque | 22.62 N·m |
| RMS torque over the cycle | 6.46 N·m |
| Total cycle time | 10.08 s |
| Maximum calculated angular acceleration | 14,844 rad/s² |

### Selected servomotor and drive

| Component | Selection / rating |
| --- | --- |
| Servomotor | **Delta ECMA-L11320**, B3 series |
| Nominal torque | 7.50 N·m |
| Maximum torque | 22.7 N·m |
| Maximum speed | 3,000 rpm |
| Servo drive | **Delta ASDA-B3-L**, 2 kW, 220 V AC single-phase |

The selection in the report satisfies the calculated **RMS torque**, **peak torque**, and **maximum speed** requirements. The peak-torque margin is small (22.7 vs. 22.62 N·m); additional engineering verification would be necessary before implementation.

## Electrical design (AutoCAD)

### 1. Power and servo-drive connections

The drawing documents the servo drive's power and motor connections, encoder interface, and control/communication terminals.

![Servo drive and motor wiring](assets/servo_drive_wiring.png)

**[Open the power schematic (.dwg)](schema_de_puissance.dwg)**

### 2. Command circuit

A relay/timer-based command design including enable, forward/reverse commands, initial-position detection, emergency-stop and overload contacts, and status indicators.

![Command circuit](assets/control_circuit.png)

**[Open the command schematic (.dwg)](schema_de_commande.dwg)**

### 3. Terminal schedule

Terminal-by-terminal wiring reference identifying the connected devices and their corresponding connections.

![Terminal schedule](assets/terminal_schedule.png)

**[Open the terminal schedule (.dwg)](tableau_de_borniers.dwg)**

## Repository contents

```text
.
├── README.md
├── QASSAB_ABDERRAHMANE_NOUREDDINE_QARAFI.pdf  # Calculations + report
├── schema_de_puissance.dwg                      # Power / servo wiring
├── schema_de_commande.dwg                       # Command circuit
├── tableau_de_borniers.dwg                      # Terminal schedule
└── assets/
    ├── servo_drive_wiring.png                   # Drawing preview
    ├── control_circuit.png                      # Drawing preview
    └── terminal_schedule.png                    # Drawing preview
```

**[Read the complete technical report (PDF)](QASSAB_ABDERRAHMANE_NOUREDDINE_QARAFI.pdf)**  
The drawings are provided in **DWG** format for use with AutoCAD or another compatible CAD application. PNG previews are included for quick viewing on GitHub.

## Project scope

This is an **academic calculation and electrical design project**. The provided materials document the sizing study and CAD schematics; they do not establish that a physical machine was built, commissioned, or experimentally validated.

## Authors and academic context

- **Noureddine Qarafi** and **Abderrahmane Qassab**
- **ENSAM Meknès — Université Moulay Ismaïl**, Electromechanical Engineering
- **Module:** GEE-MCI47 — Architecture & Technologie des Systèmes
- **Supervisor:** B. Bououlid
- **Academic year:** 2025–2026
