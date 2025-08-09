# C_MOS_INVERTER
### CMOS Layout Design using 90nm Technology
---

This project involves the complete design and verification of a CMOS layout using the GPDK 90 nm process technology in Cadence Virtuoso.  
The design process began with schematic creation, followed by layout implementation, and concluded with physical verification to ensure the design meets both functional and manufacturing requirements.  

Physical verification included:  
- **Design Rule Check (DRC)** – Ensures the layout follows all manufacturing rules specified in the PDK, confirming that the design can be fabricated without violations.  
- **Layout Versus Schematic (LVS)** – Confirms that the physical layout exactly matches the intended schematic in terms of connectivity and components.  

Passing both DRC and LVS indicates that the design is rule-compliant, functionally correct, and ready for fabrication, minimizing the risk of costly errors during manufacturing.

### Tools and Technology ------->
---
- **Cadence Virtuoso 6.1.7-64b** – Schematic and Layout Design  
- **Calibre v2016.1_14.11** – Physical Verification (DRC, LVS)  
- **GPDK 90 nm** – Process Design Kit (PDK) used for technology-specific parameters and rules  

### Introduction ------->
---
CMOS (Complementary Metal–Oxide–Semiconductor) integrates PMOS and NMOS transistors to build efficient, high-performance logic circuits with minimal static power dissipation. Using the 90 nm process node, where the minimum feature size is 90 nanometers, enables compact layouts, faster switching speeds, and lower power consumption. Layout design in VLSI translates a verified circuit schematic into a fabrication-ready physical representation that meets design rules, allowing for accurate verification, parasitic analysis, and eventual chip fabrication for real-world applications.

Virtuoso Layout Suite XL is a tool used to create custom IC layouts in a clear and organized way. It works together with a circuit’s schematic or netlist to help designers place and connect components correctly. The software can automatically create devices, arrange them, connect the wiring, and allow users to check and highlight parts in both the schematic and layout to find errors quickly.

In this project, a **CMOS inverter** is designed in Cadence Virtuoso, then tested through **Design Rule Check (DRC)** to ensure it follows manufacturing rules, **Layout Versus Schematic (LVS)** to confirm the layout matches the schematic.

![DRC Report Screenshot](https://github.com/Khushi119/C_MOS_INVERTER/blob/1efdcc1da1aaa88c63bab662d87fb14718f6cfa9/Fig%201_CMOS%20inverter%20schematic%20design.png)

As chip manufacturing becomes more advanced, **layout rules** are important to make sure designs can be built reliably. A correct schematic is essential before creating the layout, since any mistakes in the schematic will also appear in the layout. Consistent pin names between the schematic and layout help avoid mismatches during verification.

### Procedure ------->
---
### Step 1 – Launch Layout XL
In Virtuoso, go to the **top left corner** and locate the **Launch** option.  
Click **Launch → Layout XL**.  
A start-up options window will pop up.

### Step 2 – Create a New Layout
In the pop-up window, select **Create New** and click **OK**.

![DRC Report Screenshot](https://github.com/Khushi119/C_MOS_INVERTER/blob/04ac3accc8da00dcbd3bd78ed0c8f103e160bf17/Fig%202_Startup%20Option.png)

### Step 3 – File Form Verification
A **New File** form will appear.  
Check:
- **Library**: Must be the same as the one used for the schematic.
- **Cell name**: Must match the schematic name.
- **View name**: Preloaded by default; just verify it.  
If correct, proceed without changes.

![DRC Report Screenshot](https://github.com/Khushi119/C_MOS_INVERTER/blob/f5fd933363351e6326d2fef1acac0dc554fa5068/Fig%203_New%20File.png)

### Step 4 – Opening the Layout Workspace
Click **OK** to open:
- **LSW (Layer Select Window)**
- A **blank layout window** (black background = p-type substrate)
- The **schematic window** for reference.

## Adding Components to Layout

### Step 5 – Adjusting Display Settings
Before placing components, adjust display settings for better visibility.  
Go to **Options → Display Options**.  
In **Grid Control**:
- Set **X snap spacing** = `0.005`
- Set **Y snap spacing** = `0.005`  
In **Display Levels**:
- Start = `0`
- Stop = `10`

![DRC Report Screenshot](https://github.com/Khushi119/C_MOS_INVERTER/blob/f5fd933363351e6326d2fef1acac0dc554fa5068/Fig%204_Display%20Options.png)

### Step 6 – Generating Layout from Schematic
Go to **Connectivity → Generate → All from Source**.  
In the **Generate Layout** window:


![DRC Report Screenshot](https://github.com/Khushi119/C_MOS_INVERTER/blob/f5fd933363351e6326d2fef1acac0dc554fa5068/Fig%205_Generate%20Layout.png)

- Check **I/O Pins**
- Check **PR Boundary**
- Check **Extract Connectivity after Generation**  
Click **OK**.

### Step 7 – Initial Device Placement
The layout window now displays the **top view** of MOSFETs from the schematic.  
The layout is predesigned based on the technology file.  
Each MOSFET will have its **source**, **drain**, and **gate** marked along with net names.  
For the inverter:
- PMOS and NMOS layouts will appear
- Pins: `vdd`, `gnd`, `in`, `out` will be visible.

## Making Connections

### Step 8 – Routing Layout Connections
To move components: **select layout → press `m`**.  
To draw connections: **press `Ctrl + Shift + W`** to activate the line tool.  
Select the appropriate layer (**Metal**, **polySi**, etc.) from **LSW**.  
Merging the same nets is allowed.  
Additional shapes can be drawn via **Create → Shape**.

### Step 9 – Adding N-Well for PMOS
Since PMOS is built on **N-type substrate**, an **N-Well** is required for the `vdd` connection.  
Select **WN** from LSW.  
Use rectangle tool (**press `R`** or go to **Create → Shape → Rectangle**) to draw the N-Well region.

### Step 10 – Adding N-Well and P-Well Taps
For N-Well tap:
- Go to **Create → Multipart Path** (press `F3`)
- In **MPP Template**, select **NWELL Tap** and click **Hide**
- Click on the N-Well region and drag to create the tap.

![DRC Report Screenshot](https://github.com/Khushi119/C_MOS_INVERTER/blob/f5fd933363351e6326d2fef1acac0dc554fa5068/Fig%206_Create%20Multipart%20Path.png)

For P-Well tap (ground connection):
- Directly select **P-WELL Tap** from Multipart Path
- Draw on the p-type substrate (black area).

### Step 11 – Connecting PMOS and NMOS Gates
The **polySi** gates (red layer) of PMOS and NMOS must be connected for the inverter input.  
To add contact vias between polySi and Metal1:
- Go to **Create → Multipart Path** and press `F3`
- In **MPP Template**, select **GC_M1** and click **Hide**
- Draw vias on the polySi gate input.

### Step 12 – Labelling Ports
Labels must match schematic port names exactly (`in`, `out`, `vdd`, `gnd`).  
Press **`L`** to open the label tool.  

![DRC Report Screenshot](https://github.com/Khushi119/C_MOS_INVERTER/blob/f5fd933363351e6326d2fef1acac0dc554fa5068/Fig%207_Create%20Label.png)

Set **Layer** = `M1 Label`.  
Place the `+` symbol exactly on the **Metal layer** and **save the design**.

## Notes
- Maintain **identical pin names** between schematic and layout for smooth LVS verification.
- Save your layout regularly to avoid data loss.

![DRC Report Screenshot](https://github.com/Khushi119/C_MOS_INVERTER/blob/f5fd933363351e6326d2fef1acac0dc554fa5068/Fig%208_CMOS%20inverter%20Layout.png)


### Physical Verification  ------->
---
## Design Rule Check (DRC)

**Design Rule Check (DRC)** is performed to ensure that the layout follows the manufacturing design rules defined for the technology. These rules cover aspects like minimum width, spacing, and overlaps of different layers to guarantee that the design can be fabricated reliably.

### Running DRC in Calibre

1. **Open the DRC Tool**
   - In Virtuoso, go to **Calibre → Run nmDRC…**
   - A new window will pop up.

2. **Verify File Path**
   - The tool will prompt for the correct path of the layout file.
   - Ensure the path is correct, then click **OK**.

3. **Start the DRC Process**
   - Click **Run DRC** or **Start DRC**.
   - A new pop-up will appear displaying the DRC report.

4. **View and Interpret Results**
   - The report shows details based on the design rule file for the selected technology.
   - If errors are present:
     - **Double-click** the error number → Highlights the exact location of the error in the layout.
     - **Single-click** the error number → Displays a description of the error.

5. **Error Correction**
   - If errors are detected:
     - Go back to the layout.
     - Fix the highlighted violations.
     - Save the layout.
     - Re-run DRC until no errors remain.

6. **No Errors**
   - If the DRC report shows no errors, proceed to the next verification step such as LVS.

Run DRC every time changes are made in the layout to ensure it follows the required design rules.
## Layout Versus Schematic (LVS)

**Layout Versus Schematic (LVS)** is used to verify that the physical layout matches the transistors and connections defined in the schematic. It compares both the schematic and layout files to ensure that the circuit is logically correct before fabrication.

### Steps to Run LVS in Calibre

1. In Virtuoso, go to **Calibre → Run nmLVS…**.
2. A new window will appear. Verify that the correct file path is selected, then click **OK**.
3. Click **Run LVS** to start the comparison.
4. After the first run, the LVS result may show as incorrect.  
   - In this first run, the netlist is exported directly from the schematic.
   - Before running LVS for the first time, make sure the option **“Export from the Schematic view”** is checked under **Inputs → Netlist and Layout**.
5. Return to the LVS window. Under **Inputs → Netlist**, uncheck **“Export from the Schematic”**.
6. In the Netlist section, near the Spice files of the netlist, click **View**.  
   Edit the `*.SCALE METER` line to:  
This tells the LVS tool that all layout dimensions are in microns, ensuring correct scaling during comparison.  
Save the file and run LVS again.
7. If all ports in the layout and schematic match, the result will show **Correct**. If not, check:
- Layout port names
- Label placement
- The number of ports in both layout and schematic

