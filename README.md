# SUBSTRATE-BLUEPRINTS │ Open Hardware Specifications

*"Documentation of the physical layer for reproducible manufacturing."*

---

## 📐 Project Scope

**SUBSTRATE-BLUEPRINTS** is a repository dedicated to Open Hardware documentation, Electronic Design Automation (EDA) files, and mechanical CAD models.

It provides the strict industrial specifications required to manufacture modular computing nodes, sensor interfaces, and ruggedized enclosures. The primary goal is **Hardware Sovereignty through reproducibility**: ensuring that any engineer with standard lab equipment can fabricate these devices using Commercial Off-The-Shelf (COTS) components.

### Operational Mandate

* **Reproducibility**: Optimized for fabrication via standard FDM 3D printing and SMD reflow processes.
* **Standardization**: All PCB designs adhere to IPC-2221 generic standards for printed board design.
* **Independence**: Designs minimize reliance on proprietary silicon or specialized supply chains.

---

## 🏗️ Hardware Modules (BOM Categories)

The repository is organized by physical assembly modules, independent of specific software implementations:

### 1. `module-bio-afe` (Analog Front End)

* **Function**: High-impedance signal acquisition for biopotential measurements (EEG/ECG/EMG).
* **Specifications**:

  * **Input Noise**: < 1µV peak-to-peak
  * **Isolation**: Active shielding layers and galvanic isolation barriers
  * **Interface**: SPI/I2C breakout for standard microcontrollers
  * **Assets**: KiCad Project, Gerber RS-274X, Pick-and-Place CSV

### 2. `module-iot-carrier` (Mesh Node)

* **Function**: A modular carrier board for low-power embedded SoCs (ESP32-S3 / nRF52) and LoRa transceivers (SX1262)
* **Specifications**:

  * **Power Management**: Onboard MPPT (Maximum Power Point Tracking) for solar harvesting
  * **Antenna Path**: Impedance matched 50Ω traces for 868/915MHz bands
  * **Expansion**: Qwiic/Stemma QT compatible headers
  * **Assets**: KiCad Project, BOM

### 3. `module-rugged-chassis` (Enclosures)

* **Function**: Protective mechanical housing for portable field operations
* **Specifications**:

  * **Material**: Optimized for PETG, ASA, or Nylon printing
  * **Thermal**: Passive airflow analysis included for fanless cooling of 5W-15W TDP loads
  * **Ergonomics**: Mounts for mechanical switches and standard 18650 battery holders
  * **Assets**: STEP (CAD), STL (Manufacturing), DXF (Laser Cutting)

---

## 🛠️ Manufacturing Stack

To edit or export these designs, the following open-source toolchain is recommended:

* **EDA (Electronics)**: KiCad 7.0+
* **CAD (Mechanical)**: OpenSCAD or FreeCAD (Parametric designs preferred)
* **Simulation**: NGSpice (for analog circuit verification)
* **Version Control**: Uses Git LFS (Large File Storage) for binary CAD assets

---

## 🚀 Fabrication Guide

### Printed Circuit Boards (PCBs)

1. Navigate to `/pcb/{module}/gerbers`
2. Verify stack-up: Standard 1.6mm FR4, 2oz Copper (recommended for power planes), ENIG finish (recommended for sensor pads)
3. Submit `.zip` to fabrication house (e.g., JLCPCB, PCBWay, OSH Park)

### Mechanical Parts

1. Load `.stl` files from `/mechanical/stl`
2. **Slicer Settings**:

   * **Perimeters**: 3+ (for structural rigidity)
   * **Infill**: 40% Gyroid (balance of strength/weight)
   * **Supports**: Minimal/Tree supports where necessary

---

## ⚖️ License

**CERN-OHL-W-2.0** (CERN Open Hardware Licence - Weakly Reciprocal)

* **Permissions**: You may manufacture, sell, and modify devices based on these blueprints
* **Conditions**: Any modifications to the schematic or physical design files must be made available under the same license if distributed
* **Liability**: These designs are provided "as is" without warranty. Users are responsible for electrical safety compliance in their jurisdiction

---

## ⚠️ Safety Disclaimer

These blueprints involve circuits handling lithium-polymer batteries and potential mains voltage interfaces. Adhere to standard electrical safety protocols during assembly and testing.

---
