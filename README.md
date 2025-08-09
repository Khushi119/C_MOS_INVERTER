# C_MOS_INVERTER
# Precision CMOS Layout Design using 90nm Technology

This project involves the complete design and verification of a CMOS layout using the GPDK 90 nm process technology in Cadence Virtuoso.  
The design process began with schematic creation, followed by layout implementation, and concluded with physical verification to ensure the design meets both functional and manufacturing requirements.  

Physical verification included:  
- **Design Rule Check (DRC)** – Ensures the layout follows all manufacturing rules specified in the PDK, confirming that the design can be fabricated without violations.  
- **Layout Versus Schematic (LVS)** – Confirms that the physical layout exactly matches the intended schematic in terms of connectivity and components.  

Passing both DRC and LVS indicates that the design is rule-compliant, functionally correct, and ready for fabrication, minimizing the risk of costly errors during manufacturing.

## Tools and Technology

- **Cadence Virtuoso 6.1.7-64b** – Schematic and Layout Design  
- **Calibre v2016.1_14.11** – Physical Verification (DRC, LVS)  
- **GPDK 90 nm** – Process Design Kit (PDK) used for technology-specific parameters and rules  

# CMOS Inverter, NAND, and NOR Layout Design

## Overview
This project demonstrates the **design, implementation, and verification** of CMOS logic gates — specifically an **Inverter**, **NAND**, and **NOR** — using **Cadence Virtuoso Layout Suite XL** and **Calibre** verification tools.  
The workflow covers:
- Schematic creation and functional verification
- Physical layout implementation
- Rule checking and netlist comparison
- Parasitic extraction for performance analysis

This experiment bridges **circuit design** and **VLSI physical design**, offering hands-on experience with industry-standard EDA tools.

---

## Aim
To design and study the layouts of:
- CMOS Inverter
- CMOS NAND gate
- CMOS NOR gate  
and perform **DRC**, **LVS**, and **PEX** to ensure manufacturability and performance accuracy.

---

## Tools Required
- **Cadence Virtuoso 6.1.7-64b** (Layout Suite XL, Schematic Editor)
- **Calibre v2016.1_14.11** (nmDRC, nmLVS, PEX)

---

## Theoretical Background

### CMOS Logic Basics
- **CMOS (Complementary Metal–Oxide–Semiconductor)** uses both **PMOS** and **NMOS** transistors to implement logic functions.
- **Advantages**: Low static power consumption, high noise immunity, scalability.
- **Inverter**: The simplest CMOS circuit — output is the logical NOT of input.
- **NAND/NOR**: Universal logic gates that can form any other logic function.

### Layout Design in VLSI
- **Schematic-to-Layout Flow**: The layout is a physical representation of the schematic, respecting technology rules.
- **Design Rules**: Specify minimum widths, spacings, and overlaps to ensure reliable fabrication.
- **Physical Verification**:  
  - **DRC** ensures geometry compliance.  
  - **LVS** checks logical equivalence between layout and schematic.  
  - **PEX** identifies parasitic effects that influence real-world performance.

---

## Procedure

### 1. Schematic Design
- Create the CMOS circuit schematic in **Virtuoso Schematic Editor**.
- Assign consistent **pin names** (`in`, `out`, `vdd`, `gnd`).
- Simulate to verify functional correctness before proceeding.

### 2. Layout Creation
1. Launch **Layout XL** from the schematic.
2. Configure:
   - Grid snap spacing: `0.005`
   - Display levels: start = 0, stop = 10
3. Use **Generate from Source** to auto-place devices and pins.
4. Align PMOS/NMOS transistors for compact routing.
5. Connect:
   - **PolySi gates** for inputs
   - **Metal layers** for interconnections
   - **N-Well** for PMOS with taps to `vdd`
   - **P-Well** (substrate) taps to `gnd`
6. Label ports exactly as in schematic.
7. Save layout.

### 3. Physical Verification
- **DRC**: Run nmDRC; fix spacing, width, or overlap violations.
- **LVS**:  
  - Export netlist from schematic.  
  - Ensure pin names and counts match between layout and schematic.  
  - Re-run until "Correct" status achieved.
- **PEX**: Extract parasitic resistances and capacitances to refine post-layout simulation.

---

## Observations
- All three layouts (Inverter, NAND, NOR) passed **DRC** with no violations.
- **LVS** confirmed logical equivalence between layout and schematic.
- **PEX** revealed parasitic capacitances which, if ignored, could degrade switching speed.

---

## Conceptual Insights
- **Why DRC matters**: Even functionally correct circuits may fail fabrication if spacing/width rules are violated.
- **Why LVS matters**: Prevents costly manufacturing errors by ensuring layout matches intended logic.
- **Why PEX matters**: Parasitics affect delay, power, and signal integrity; critical for high-speed designs.
- **Scalability**: The methodology for an inverter scales directly to complex digital blocks like adders and processors.
- **Design for Manufacturability (DFM)**: Good layout practices reduce yield loss and improve reliability.

---

## Conclusion
This experiment successfully:
- Implemented CMOS logic gate layouts in Cadence Virtuoso.
- Verified manufacturability and functional correctness using Calibre tools.
- Illustrated the importance of physical verification and parasitic analysis in VLSI design.

The approach here forms the foundation for more advanced ASIC and SoC designs.

---

## References
1. Cadence Design Systems – Virtuoso Layout Suite XL Documentation  
2. Rabaey, J. M., Chandrakasan, A., & Nikolic, B. *Digital Integrated Circuits: A Design Perspective*  
3. Calibre nmDRC and nmLVS User Guide  
4. Parasitic Extraction Techniques in Calibre PEX
