# Custom ESP32 Development Board with Integrated USB-to-UART Bridge

## 📌 Project Overview
This project features a production-ready, compact development board designed around the **ESP32-WROOM-32** MCU module. It is engineered specifically for low-power IoT applications, integrating a modern **USB-C interface** for unified power delivery and programming, an ultra-low-dropout (LDO) linear regulator, and a discrete auto-flashing circuit.

---

## 🛠️ Technical Specifications & Architecture

| Parameter | Specification | Engineering Purpose |
| :--- | :--- | :--- |
| **Core Microcontroller** | ESP32-WROOM-32 (Dual-Core) | Dual-channel Wi-Fi & Bluetooth processing power |
| **Interface Port** | USB-C (USB 2.0 Signaling) | Modern, durable power injection and data line |
| **USB-UART Bridge** | CP2102N (QFN-24 Package) | High-speed translation; internal clock saves PCB space |
| **Voltage Regulator** | AP2112K-3.3V (600mA LDO) | Prevents brownouts during active wireless transmission bursts |
| **PCB Constraints** | 2 Layers, 1.6 mm FR-4, ENIG | Industrial standard optimization for high-density routing |

---

## 📐 Critical Engineering Design Decisions

### 1. RF Keep-Out Isolation Zone
To protect wireless communication range, an absolute multi-layer copper clearance (Keep-Out Void) was implemented directly beneath the ESP32’s onboard PCB trace antenna. This eliminates nearby ground plane absorption or detuning of the 2.4GHz signals.

*🖼️ [Insert: 02_Bare_PCB_Production.png]*

### 2. Impedance-Controlled High-Speed Data Pairing
The `USB_D+` and `USB_D-` data traces are routed as a tightly matched differential pair directly from the USB-C pads to the transceiver pins. Running them completely parallel on the top layer preserves characteristic impedance and prevents high-frequency data corruption.

*🖼️ [Insert: 03_X_Ray_Trace_Routing.png]*

### 3. High-Transient Decoupling Matrix
The power distribution network relies on a parallel decoupling array ($10\mu\text{F}$ bulk energy storage paired with low-ESR $1\mu\text{F}$ and $100\text{nF}$ surface-mount ceramic capacitors) placed as physically close to the LDO and MCU supply pins as possible to suppress high-frequency ripple ripples.

*🖼️ [Insert: 04_Premium_Matte_Black.png]*

---

## 📂 Documentation & Manufacturing Packages
* **Schematics:** Complete vector schematic maps are available inside the `/documentation/schematics/` directory.
* **Engineering Design Log:** For a granular, step-by-step breakdown of every passive component value justification (`R1-R7`, `C1-C3`), see the comprehensive [Interactive Engineering Log Spreadsheet](./hardware/design_log/ESP32_Hardware_Design_Portfolio_Log.xlsx).