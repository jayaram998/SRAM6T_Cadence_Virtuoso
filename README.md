## Designing and Simulating a 6T SRAM Cell in Cadence Virtuoso

Designing a 6T Static Random-Access Memory (SRAM) cell is fundamental for those exploring advanced memory design concepts. The 6T SRAM cell, known for its stability and efficiency, comprises six transistors that allow storage of a single bit of data. In this article, we’ll guide you through the design, analysis, and simulation processes using Cadence Virtuoso, concluding with the butterfly curve—a key tool for analyzing stability and performance of SRAM cells.

## Step 1: Preparing Cadence Virtuoso for SRAM Design

**Launch Cadence Virtuoso:** Begin by opening Cadence Virtuoso. Ensure that your technology files are properly set up and configured based on your selected process technology (e.g., 65nm, 90nm).

**Create a New Library:** Go to File > New > Library, name it appropriately (e.g., SRAM_6T_Design), and attach the relevant technology file.

**Create the SRAM Cell Schematic:** In this library, create a new cell for the schematic (Cell > New > Schematic) and name it (e.g., 6T_SRAM).

## Step 2: Designing the 6T SRAM Cell Schematic

**Place Transistors:** Start by adding six transistors:

Four transistors form two cross-coupled inverters (two PMOS and two NMOS transistors).
Two additional NMOS transistors act as access transistors, connected to the bit lines (BL and BLB).

**Construct Cross-Coupled Inverters:**

The inverters are created by connecting the drain of each PMOS to the drain of an NMOS, forming two distinct inverting stages.
Cross-couple the inverters by connecting the output of one to the input of the other.

**Connect Access Transistors:**

The gates of these transistors are controlled by the word line (WL).
The sources connect to the storage nodes of the inverters, while the drains connect to the bit lines.

**Add Supply Connections:**

Connect the PMOS sources to VDD and NMOS sources to GND.
Label important nodes for easy identification, such as BL, BLB, WL, VDD, GND, and the storage nodes Q and QB.

![image](https://github.com/user-attachments/assets/52bead66-6116-4bcf-93ab-6a32b9cf5e2d)


## Step 3: Simulation Setup and SRAM Cell Verification

**Define Testbench Setup:**

Create a testbench to apply inputs for read and write operations.
Use pulses on the word line and appropriate voltage levels on the bit lines to emulate write operations.
Configure the bit lines to evaluate read operations.

**Run Transient Analysis:**

Use transient simulation to observe the behavior of the SRAM cell during write and read operations.
Ensure that the cell stores the intended data during write and retains it accurately during read.

**Assess Read Stability and Write Margin:**

Verify that data can be stored and read back correctly without disturbing the internal state.
If the data is not retained accurately, review transistor sizing to achieve proper read/write margins.

## Step 4: Generating the Butterfly Curve for Stability Analysis

The butterfly curve is crucial in analyzing the static noise margin (SNM) of the SRAM cell, which reflects the stability of the stored data. Here’s how to generate it:

![image](https://github.com/user-attachments/assets/41dfa4ed-6258-4167-b7ed-cccb2cbcf566)

**Set Up for DC Analysis:**

In your testbench, configure a DC sweep for the storage nodes, Q and QB.
The sweep will help to find the SNM by plotting Q versus QB voltages for various bit line and word line conditions.

**Plot the Butterfly Curve:**

Set one storage node (Q) to an incremental DC sweep.
Simultaneously, plot the voltage at QB.
The resulting plot should form a butterfly-like curve, indicating the bistable states of the SRAM cell.

**Calculate Static Noise Margin (SNM):**

The SNM is the maximum square that can fit between the two wings of the butterfly curve.
A larger SNM indicates a more stable cell. If the SNM is inadequate, you may need to adjust transistor dimensions or change the aspect ratios of NMOS and PMOS transistors.

## Step 5: Layout Design and Verification

Create the Layout: After schematic design and verification, proceed to layout the cell in Cadence Layout.

**DRC and LVS Checks:**

Perform Design Rule Check (DRC) to ensure compliance with fabrication guidelines.
Run Layout Versus Schematic (LVS) to confirm that the layout matches the schematic.

## Conclusion

Designing a 6T SRAM cell in Cadence Virtuoso offers hands-on experience in memory circuit design and simulation. By following these steps and analyzing the butterfly curve, you’ll gain a deep understanding of SRAM stability and performance. Completing this design process will not only refine your Cadence Virtuoso skills but also build a solid foundation in SRAM memory design principles, enhancing your overall proficiency in VLSI design.

