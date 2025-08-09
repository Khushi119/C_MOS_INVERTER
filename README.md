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

Once the **CMOS inverter schematic** is completed and **functionally verified** in the Virtuoso Schematic Editor, the layout creation process can begin.  
The following section provides a detailed **step-by-step procedure** for creating the layout in **Virtuoso Layout Suite XL**.

---

## Step-by-Step Procedure

### Step 1 – Launch Layout XL
- In Virtuoso, go to the **top left corner** and locate the **Launch** option.
- Click **Launch → Layout XL**.
- A start-up options window will pop up.

---

### Step 2 – Create a New Layout
- In the pop-up window, select **Create New**.
- Click **OK**.

---

### Step 3 – File Form Verification
- A **New File** form will appear.
- Check:
  - **Library**: Must be the same as the one used for the schematic.
  - **Cell name**: Must match the schematic name.
  - **View name**: Preloaded by default; just verify it.
- No changes are required if values are correct.

---

### Step 4 – Opening the Layout Workspace
- Click **OK**.
- This opens:
  - **LSW (Layer Select Window)**
  - A **blank layout window** (black background representing the p-type substrate)
  - The **schematic window** for reference.

---

## Adding Components to Layout

### Step 5 – Adjusting Display Settings
- Before placing components, adjust display settings for better visibility.
- Go to **Options → Display Options**.
- Under **Grid Control**:
  - Set **X snap spacing** = `0.005`
  - Set **Y snap spacing** = `0.005`
- Under **Display Levels**:
  - Set **Start** = `0`
  - Set **Stop** = `10`

---

### Step 6 – Generating Layout from Schematic
- Go to **Connectivity → Generate → All from Source**.
- In the **Generate Layout** window:
  - Check:
    - **I/O Pins**
    - **PR Boundary**
    - **Extract Connectivity after Generation**
- Click **OK**.

---

### Step 7 – Initial Device Placement
- The layout window now displays the **top view** of the MOSFETs from the schematic.
- The layout is predesigned based on the selected technology file.
- Each MOSFET will have its **source**, **drain**, and **gate** marked along with net names.
- For the inverter example:
  - PMOS and NMOS layouts will appear
  - Pins will be labeled `vdd`, `gnd`, `in`, and `out`.

---

## Making Connections

### Step 8 – Routing Layout Connections
- To move components: **select layout → press `m`**.
- To draw connections: **press `Ctrl + Shift + W`** to initialize the line tool.
- Select appropriate layers (Metal, polySi, etc.) from **LSW**.
- **Merging** of the same nets is allowed.
- Additional shapes can be drawn from **Create → Shape**.

---

### Step 9 – Adding N-Well for PMOS
- Since PMOS is built on **N-type substrate** in CMOS technology, an **N-Well** is required for the `vdd` connection.
- Select **WN** from LSW.
- Use rectangle tool (**press `R`** or go to **Create → Shape → Rectangle**) to draw the N-Well region.

---

### Step 10 – Adding N-Well and P-Well Taps
- **N-Well Tap**:
  - Go to **Create → Multipart Path** (press `F3`).
  - In **MPP Template**, select **NWELL Tap** and click **Hide**.
  - Click on the N-Well region and drag to create the tap.
- **P-Well Tap** (for g

