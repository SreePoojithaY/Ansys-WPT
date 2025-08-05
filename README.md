This file explains the process of designing a coil using ANSYS Maxwell 3D simulation software. The goal is to model an air core inductor using a helical structure. This design is often used in high-frequency applications, where air-core inductors are preferred due to their efficient performance at high frequencies. The tutorial walks through the steps of setting up the simulation environment, designing the coil, and preparing it for electromagnetic analysis.
The goal is to complete the setup by energizing the coil and ensuring that it is properly connected to the boundary conditions in the simulation environment. Also, to create a simple circuit for transmitting (TX) and receiving (RX) coils, integrate inductance values calculated from Maxwell simulations, and assess coil efficiency and power transfer in the system.

Key Steps 
1. Setting Up the Simulation Environment
Software Required: The tutorial uses ANSYS Electronics Desktop, specifically the Maxwell 3D package. It is essential that the correct version of the software is installed for the simulation to work.

Creating a New Project: The tutorial begins with creating a new project in ANSYS. A new Maxwell 3D design is inserted into the project. This sets the stage for designing the coil.

2. Designing the Coil
Helical vs. Spiral Coil:

The tutorial covers the design of two types of coils: helix and spiral.

The helical coil is achieved using the polygon helix feature. A parameter called radius change is used to convert a standard helical coil into a spiral design. This allows for a better understanding of the geometric differences between the two types of coils.

Setting Parameters:

Parameters for the coil are defined, including the start helix radius (which determines the inner radius of the coil) and pitch (the gap between turns).

The wire diameter is set to 3mm, and the number of turns is chosen to be 25.

Pitch and Radius Change:

The pitch is set to a value slightly higher than the wire diameter to avoid overlapping coils in the simulation. For instance, a pitch of 6.01mm is used instead of 6mm to ensure proper spacing between the turns.

3. Meshing and Material Assignment
Meshing the Coil: The polygon helix is used to generate the coil structure. The mesh is an essential part of the simulation to ensure accurate results. A coarse mesh is initially used for faster simulations, with refinement options available for higher accuracy.

Material Assignment: Initially, the coil is created with a vacuum material. It is later changed to copper as the material for the coil to reflect real-world conditions.

4. Creating the Air Region (Surrounding the Coil)
To simulate the coil's behavior in a realistic environment, an air region is created using a cuboid. This cuboid surrounds the coil and provides the necessary space to simulate the coil as if it were in an actual laboratory setup.

Creating the Cuboid: The cuboid's size is chosen to be 500mm in height, with appropriate measurements for the X and Y dimensions.

The cuboid is then moved to position the coil inside it, simulating an air-core inductor where the coil is surrounded by air.

5. Exciting the Coil
To calculate values such as inductance, the coil needs to be excited with a current source. The excitation will be applied within the coil's environment to simulate real-world operation.

6. Final Adjustments and Simulation Setup
View Adjustments: Various views such as isometric and top view are used to position the coil correctly in the simulation space. This is crucial for ensuring the accuracy of the simulation results.

Material Properties for Air: The material for the surrounding region is set to air to match the simulation environment.

7. Boundary Condition Setup
Problem with Boundary Conditions: The initial coil design is surrounded by an air region (box), but the coil doesn't touch the boundary of the air region, which is essential for setting up a correct simulation. For the simulation to work, the coil needs to be properly connected to the boundary surface.

Solution:

Two leads (copper wires) are drawn to connect the coil terminals to the boundary surface of the air region. These leads are kept small in diameter to avoid affecting the results of the coil's performance.

The leads are created using the "Draw Line" option and extended from the coil terminals to the boundary. The design is adjusted to ensure the leads are aligned with the coil’s terminals and connect to the selected boundary face.

8. Drawing the Leads
Lead Creation:

The leads are created by drawing lines from the coil’s terminals to the boundary face (perpendicular to the X-axis).

The lines are drawn in an arbitrary direction, and later adjusted to match the exact position and alignment with the coil and boundary.

Adjusting Line Coordinates:

The X, Y, and Z coordinates of the lines are adjusted to ensure that the leads are positioned exactly where they need to be. The final coordinates are set based on the dimensions of the coil and the selected boundary surface.

9. Creating the Polyline
The drawn leads are then converted into polylines, and their diameter is set to 2mm to simulate the current-carrying leads accurately.

The leads are connected to the coil using the Unite operation. This combines the coil and the leads into a single air-core inductor component, ensuring that both parts are treated as one object in the simulation.

10. Subtracting the Leads from the Air Region
The coil leads extend beyond the boundary box, so the leads must be subtracted from the region to meet the boundary condition.

A second box (Box 2) is created, which will subtract the leads from the air region. This ensures that the leads are properly confined to the boundary and prevents unnecessary simulation errors.

11. Exciting the Coil
Current Excitation:

With the boundary conditions met, the coil can now be excited. The first terminal is selected as the input terminal, and the second terminal as the output terminal.

A current of 5 Amps is applied to the input terminal. The direction of current flow is specified, ensuring that the coil is energized correctly.

Terminal Settings:

The input and output terminals are assigned their respective excitation currents, ensuring that the coil is energized for further analysis.

12. Meshing the Design
Mesh Creation: A mesh is created for both the air region and the coil. The mesh is set to a coarse level to speed up simulation times. The mesh settings can be refined later for more accuracy.

Finite Element Method (FEM): The coil and the surrounding region are divided into smaller elements using the finite element method. The size of these elements is adjusted based on the geometry of the coil and the surrounding air region.

The air region mesh is set to a length of 80 mm, and the coil mesh is set to a finer mesh with 30 mm elements to better capture the coil’s electromagnetic properties.

13. Analysis Setup
Solution Setup:

The simulation is set to run with adaptive passes (10 iterations), allowing the software to refine the solution progressively. The convergence criteria are set to 10% error to balance speed and accuracy.

The alternating solver is selected for the analysis to optimize computation time and memory usage.

Output Configuration:

The results are configured to output inductance values. A data table is used to extract the self-inductance of the coil after the simulation runs.

14. Running the Simulation
The simulation is started, and the software performs several passes to refine the solution and compute the inductance of the coil. The simulation may take some time, depending on the complexity of the model and the available computational resources.

Once the simulation is completed, the inductance value is calculated and displayed in the results.

15. Post-Simulation Analysis
Inductance Calculation:

The final inductance value is calculated as 25 microhenry for the given coil design. This is based on the coil's geometry, material properties, and excitation current.

Further Design Optimization:

we can modify the coil design to achieve a target inductance value (e.g., 60 microhenry). This can be done by adjusting parameters like the number of turns, wire diameter, and the helix radius.

Parameter Sweeps: For more advanced simulations, parameter sweeps can be performed to vary specific design variables and observe their effect on the coil’s performance (e.g., inductance or coupling).

we can use the magnetic Static solution type for faster simulation;

Simulation and Analysis Setup
Solution Setup:

The adaptive pass is set to 10 for better accuracy in results, with the convergence criteria set to 10% error.

The iterative solver is chosen for better computational efficiency.

Parameter Sweep:

A parametric sweep is performed to vary the distance between the TX and RX coils, from 35mm to 65mm, to analyze how the coupling coefficient and inductance vary with distance.

16. Running the Simulation
The simulation is executed, and the results are generated for various distances between the coils.

Inductance and Coupling Coefficient: The simulation calculates the mutual inductance and coupling coefficient between the coils for each of the specified distances.

17. Result Generation
Once the simulation is completed, results are generated by creating a magnetic static report. The report includes inductance values (both self-inductance and mutual inductance) for the TX and RX coils.

Coupling Coefficient is also calculated to observe how it changes with varying distances between the coils. The coupling coefficient tends to decrease as the distance increases.

18. Post-Simulation Results
Inductance Calculation:

The self-inductance and mutual inductance for the transmitting and receiving coils are calculated. The results are visualized using data tables and field overlays to display the magnetic flux and other electromagnetic parameters.

Coupling Coefficient:

To see how the coupling coefficient between the TX and RX coils changes based on the distance between them.

19. Analyzing Mutual Inductance
The mutual inductance between the TX and RX coils is observed to decrease with increasing distance:

At 35mm distance, mutual inductance is 217nH.

As the distance increases, mutual inductance decreases, indicating that coupling strength diminishes with distance.

The coupling coefficient is also calculated, showing a similar trend. At 35mm, the coupling coefficient is around 0.21, while it drops to 0.06 at 65mm.

20. Magnetic Field Visualization
The magnetic field intensity around the coils is visualized for different distances. At 35mm, the magnetic field intensity is higher, whereas at 65mm, it significantly drops, which is expected as the distance increases.

The vector form of the magnetic field is also visualized to better understand how the field interacts with the coils.

21. Design Optimization
Based on the results, you can optimize the coil parameters (such as wire diameter, number of turns, etc.) for better performance, especially if you want to achieve a specific inductance value or optimize for the best coupling coefficient.

22. Next Steps in Circuit Design
The next step will involve integrating the coil design into a circuit simulation to calculate the power transfer efficiency and resonance tuning using external capacitors.

The tutorial hints at the use of Twin Builder or Simplorer for circuit-level simulation of the WPT system to evaluate the complete power transfer setup.

Series-Parallel Topologies will be explored for optimal resonance and power transfer.

ANSYS SIMPLORER

1. Project Setup
Open the ANSYS Maxwell Coil Design file (previously created in Tutorial-4) and import it into Simplorer (Twin Builder) to build the circuit model.

Create a new Twin Builder project, then insert the Maxwell component (Magnetic Static) to connect the coil model.

2. Circuit Design
Build a simple series resonance circuit:

Voltage Source: Set to a specific frequency (6.7 MHz for example).

Coil Model: Import the inductance matrix from ANSYS Maxwell.

Capacitors: Add series capacitors to the TX and RX coils to ensure resonance at the desired frequency.

The objective is to tune the circuit for magnetic resonance coupling, which is key to wireless power transfer.

3. Component Libraries
Use Simplorer's component library to access necessary components like:

Capacitors

Inductors

Voltage sources

Voltage Source: Set to 6.7 MHz for the TX coil, ensuring correct resonance frequency with the capacitors.

4. Resonance and Tuning
Tuning Process: The capacitors (C1 and C2) are tuned to resonate with the coils at 6.7 MHz. Adjust the capacitor values to achieve resonance.

Use the theoretical formula 
𝜔𝐿=1/𝜔𝐶 to calculate the required capacitance.

Variable Capacitors: Assign C1 and C2 as variables for easy tuning.

5. AC Solution Setup
Set up the AC solution type for frequency sweeps. The frequency range is set from 6 MHz to 7 MHz.

The efficiency of the power transfer is calculated by dividing the output power by the input power.

6. Analysis and Results
Efficiency Calculation: The goal is to achieve maximum efficiency at the resonance frequency (6.7 MHz).

Results:

Plot the efficiency vs frequency for the range 6 MHz to 7 MHz.

At 6.78 MHz, the efficiency reaches 92.89%, indicating successful resonance tuning.

Data Table: Create a data table to record output and input power at different frequencies.

7. Transient Solution
A transient solution is applied to observe time-domain behavior.

Phase Analysis: Ensure that the voltage and current on the secondary side are in phase, which is crucial for efficient power transfer.

8. Practical Insights
In real-world applications, achieving 100% efficiency is practically impossible due to various losses (e.g., skin effect, eddy current losses, parasitic effects).

However, in simulation, 100% efficiency can be achieved under ideal conditions, and the results provide a benchmark for designing efficient systems.

9. Advanced Tuning
Further tuning of the capacitor values and other components can be done to achieve better efficiency and power transfer in a practical system.

The frequency splitting phenomenon and bifurcation effects in WPT systems are explored, and minor adjustments can help optimize the system’s performance.

Conclusion
This project provides a comprehensive guide to building, simulating, and analyzing a Wireless Power Transfer (WPT) system. By combining the powerful simulation tools of ANSYS Maxwell and Simplorer (Twin Builder), we cover the fundamental steps involved in designing a WPT system from coil design to power transfer optimization.

summary:

Design and simulate helical coils with ANSYS Maxwell for WPT applications.

Address boundary conditions and excite the coil models for proper simulation.

Integrate the simulation results into Simplorer (Twin Builder), creating a complete circuit for wireless power transfer.

Tune the system for resonance and optimize efficiency using AC and transient analysis.

Perform practical power efficiency calculations, showing how to achieve high efficiency under ideal simulation conditions and how to approach real-world hardware limitations.

Final Changes to the design and observed results:
Designed a 2-coil WPT system with 80 mm diameter, 6 mm thickness, and 3 turns per coil using Ansys Maxwell 3D; excited Tx coil with 5 A DC for magnetostatic analysis.

Extracted self-inductance of 1.02 μH per coil and observed mutual inductance drop from 224 nH to 67 nH as spacing increased from 35 mm to 65 mm, reducing coupling coefficient from 0.22 to 0.09.

Visualized magnetic field strength using B-field plots; measured maximum B = 138.32 μT at 35 mm spacing, showing strong near-field coupling and minimal stray flux.

Co-simulated Maxwell field results in Simplorer (Twin Builder) with matching capacitor network (C1, C2) to tune for resonance at 6.7 MHz.

Excited the system with a 320 V sinusoidal source at 6.78 MHz and conducted AC sweep and transient (TR) analysis to evaluate steady-state performance.

Generated power efficiency vs frequency plot showing 99.9% peak efficiency at 6.78 MHz; maintained >90% efficiency across the 6.68–6.94 MHz bandwidth.

Validated coupling behavior, power gain, and waveform stability using voltage/current probes and simulation post-processing; confirmed performance with exported inductance/coupling tables and field plots.
