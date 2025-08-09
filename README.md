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

## Introduction
CMOS (Complementary Metal–Oxide–Semiconductor) integrates PMOS and NMOS transistors to build efficient, high-performance logic circuits with minimal static power dissipation. Using the 90 nm process node, where the minimum feature size is 90 nanometers, enables compact layouts, faster switching speeds, and lower power consumption. Layout design in VLSI translates a verified circuit schematic into a fabrication-ready physical representation that meets design rules, allowing for accurate verification, parasitic analysis, and eventual chip fabrication for real-world applications.

Virtuoso Layout Suite XL is a tool used to create custom IC layouts in a clear and organized way. It works together with a circuit’s schematic or netlist to help designers place and connect components correctly. The software can automatically create devices, arrange them, connect the wiring, and allow users to check and highlight parts in both the schematic and layout to find errors quickly.

In this project, a **CMOS inverter** is designed in Cadence Virtuoso, then tested through **Design Rule Check (DRC)** to ensure it follows manufacturing rules, **Layout Versus Schematic (LVS)** to confirm the layout matches the schematic.

As chip manufacturing becomes more advanced, **layout rules** are important to make sure designs can be built reliably. A correct schematic is essential before creating the layout, since any mistakes in the schematic will also appear in the layout. Consistent pin names between the schematic and layout help avoid mismatches during verification.

