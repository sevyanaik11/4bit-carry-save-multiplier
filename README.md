# 4bit-carry-save-multiplier
The 4-bit Carry Save Multiplier performs fast binary multiplication using carry-save addition to minimize delay. Implemented in Verilog and verified on FPGA, it uses switches for inputs and LEDs for outputs. This design achieves high speed, making it ideal for VLSI and DSP applications.
# 🎯 Overview

This project presents the FPGA-based implementation of a 4-bit Carry Save Multiplier (CSM) — a high-speed arithmetic unit that enhances multiplication performance using the carry-save addition technique. The design efficiently computes partial products and reduces propagation delay by storing intermediate carries instead of propagating them immediately. This project demonstrates the design, simulation, synthesis, and implementation of the CSM on an FPGA using Xilinx Vivado with switches as inputs and LEDs as output.

#✨ Key Highlights

⚡ High Speed: Reduced delay due to parallel carry-save addition

💡 FPGA Implementation: Verified using Xilinx Vivado on a real FPGA board

🧠 Optimized Design: Efficient 4-bit multiplication with fewer gate levels

🔍 Full Verification: RTL simulation and on-board testing with LEDs

🛠 Modular Verilog: Clean, parameterized RTL design and testbench
🏗 Architecture

# Design Overview

The 4-bit Carry Save Multiplier performs multiplication of two 4-bit binary numbers using partial product generation and carry-save addition. Instead of waiting for carry propagation at every stage, the carries are stored and added in the next stage, improving speed compared to ripple-carry designs.

         A3 A2 A1 A0
           ×
         B3 B2 B1 B0
         ---------------
         Partial Products → Added Using Carry Save Adders
         Final Sum + Carry → Final Product (8 bits)
Internal Flow

Generate partial products using AND gates

Align partial products based on bit significance

Perform carry-save additions in stages

Propagate final sum and carry to get the 8-bit result
#💡 Working Principle

The multiplier accepts two 4-bit binary inputs (A and B) and produces an 8-bit output (P). The process involves:

Partial Product Generation – AND gates create partial products for each bit of B.

Carry Save Addition – Partial products are summed using Carry Save Adders (CSAs) which generate two outputs: a “sum” and a “carry” vector without propagating the carry.

Final Addition – The saved carry is finally added to the sum vector using a Ripple Carry Adder (RCA) to produce the final 8-bit product.

This method significantly reduces the time complexity of multiplication because carry propagation occurs only once, in the final stage.

🧮 Advantages of the 4-Bit Carry Save Multiplier
Feature	Advantage
Parallel Computation	Carries are saved instead of propagated, increasing speed.
Reduced Delay	Final carry propagation occurs only once at the end.
Scalability	Can be extended easily to N-bit multipliers.
Efficiency	Ideal for pipelined and high-performance VLSI systems.
Area Utilization	Simple structure with balanced resource usage.
🧠 Comparative Insight

Compared to a traditional ripple-carry or array multiplier, the Carry Save Multiplier demonstrates:

2–3× faster computation due to parallel carry handling.

Shorter critical path delay, leading to higher clock frequency.

Lower dynamic power because fewer transitions occur in intermediate adders.

Better suitability for complex systems like MAC units and DSP blocks.

# 🔄 Complete ASIC / FPGA Design Flow
<img width="321" height="593" alt="image" src="https://github.com/user-attachments/assets/33c96875-2377-4ac2-8dbd-fbe151aa9a5d" />


📊 Results and Performance
<img width="886" height="382" alt="image" src="https://github.com/user-attachments/assets/bec95d0b-67d9-459b-9217-c8b692483601" />

Performance Summary:
The post-layout implementation achieved clean timing closure with a 5.10 ns critical path, operating reliably at 190 MHz. Power consumption remains minimal, making it efficient for small-scale arithmetic accelerators.

🧩 Design Analysis

Timing: Positive slack indicates successful timing closure.

Power: Dominated by dynamic power; leakage is negligible.

Area Efficiency: Compact layout with balanced routing and minimal congestion.

Scalability: Architecture can be extended to 8-bit or 16-bit systems with minor modifications.

🖼 Visual Gallery

Figure 1: Block diagram of 4-bit Carry Save Multiplier
Figure 2: Internal Carry Save Adder architecture
Figure 3: Simulation waveform showing correct product generation
Figure 4: Synthesized layout (SkyWater 130nm Technology)

🧱 Observations

Carry Save design reduces critical path delay compared to sequential adders.

Balanced adder tree ensures uniform propagation across bit levels.

Verilog simulation confirmed correctness for all input combinations (00–15 × 00–15).

Layout achieved high density with efficient use of routing layers.
Design Methodology

The design of a 4-bit Carry Save Multiplier includes three main stages:

Partial Product Generation: Each bit of the multiplier is ANDed with each bit of the multiplicand to generate partial products.

Carry-Save Addition: The partial products are then added using a series of full adders that store the carry outputs separately.

Final Summation: The stored carries and sums are combined using a ripple-carry adder to produce the final 8-bit product.

Implementation

The project was implemented using Verilog HDL in Xilinx Vivado.
The structural design was simulated and synthesized for FPGA implementation. The design achieves optimized area, power, and delay performance suitable for real-time applications.

#Results

The simulation waveform confirms correct multiplication for all 4-bit input combinations. The layout and FPGA output validate the accuracy of the design.
Below are the corresponding implementation results:

Figure 1: Block Diagram of 4-bit Carry Save Multiplier

Figure 2: Simulation Waveform

Figure 3: Layout Design

Figure 4: FPGA Implementation Output
#Performance Analysis

The 4-bit Carry Save Multiplier was synthesized and implemented on the Xilinx Artix-7 FPGA board using Vivado. The following parameters were analyzed — area utilization, timing delay, and power consumption.
<img width="819" height="415" alt="image" src="https://github.com/user-attachments/assets/6f98df19-f219-4ad1-8376-9c671ab908c7" />

Comparative Analysis

To evaluate the efficiency of the Carry Save Multiplier, it was compared with conventional multiplier architectures such as Array Multiplier and Carry Lookahead Multiplier (CLA).

<img width="936" height="247" alt="image" src="https://github.com/user-attachments/assets/1f56868b-7fd8-4b8c-8086-61e6a01acd99" />


Future Scope

The design can be expanded to support 8-bit or 16-bit multipliers. It can also be optimized for power consumption and integrated into ALUs, DSP processors, and cryptographic hardware.

📚 References

J. M. Rabaey, Digital Integrated Circuits: A Design Perspective.

SkyWater 130nm Open-Source PDK Documentation.

OpenLane and Yosys User Manuals.

FPGA Implementation Guide for Arithmetic Circuits.


#Figure 1: Schematic Diagram
The synthesized design was mapped onto an FPGA board using Vivado. Switches were
assigned to inputs A[3:0] and B[3:0], and LEDs were connected to output P[7:0].

![WhatsApp Image 2025-10-30 at 13 06 58_ce3f9c43](https://github.com/user-attachments/assets/6cbbac73-bfa5-4701-9db0-810dc160d4fe)

Figure 1: RTL Schematic of the Multiplier Design
Schematic Diagram

#The schematic of the 4-bit Carry-Save Multiplier shows the interconnection of AND gates and full adders that generate and combine the partial products.
Each bit of the multiplicand and multiplier contributes to the partial product, which is then added using Carry-Save Adders (CSAs).
This arrangement eliminates the need for immediate carry propagation, improving the overall computation speed.
The schematic confirms that the design structure follows the modular approach with minimal delay and reduced logic complexity.




Figure 2: Simulation Waveform

![WhatsApp Image 2025-10-30 at 13 09 50_1bc1dca4](https://github.com/user-attachments/assets/3d46f834-b415-4b6e-9f7a-817069be67c7)
Simulation Waveform

#The simulation waveform illustrates the working of the CSM when various input combinations are applied.
Inputs A and B (each 4-bit) are given, and the product P (8-bit) is observed at the output.
For every change in input, the output corresponds exactly to the expected product value, confirming the correctness of the Verilog code.
The waveform validates the parallel carry-save addition technique, showing reduced delay compared to conventional multiplication methods.
#layout
![WhatsApp Image 2025-10-30 at 13 07 53_081e27a6](https://github.com/user-attachments/assets/1a4d02bd-4495-4671-bede-2f27fdb9e6d2)
#figure3;layout
The layout diagram represents the physical implementation of the multiplier circuit at the transistor or standard cell level.
This layout is generated after synthesis, placement, and routing in the VLSI design flow.
It shows the actual arrangement of gates, interconnections, and metal layers.
The design successfully passed DRC (Design Rule Check) and LVS (Layout vs. Schematic) verification, ensuring that the layout matches the schematic and follows fabrication rules.
The compact design and proper routing indicate optimized area utilization.


#hardware

![WhatsApp Image 2025-11-02 at 23 04 11_93eb470e](https://github.com/user-attachments/assets/3021c0c4-ff87-4fb6-af9d-84408ae3de3c)

Figure 3: FPGA Implementation Output on Hardware
#Hardware Implementation

#The hardware implementation was carried out on an FPGA board.
The Verilog code was synthesized using Xilinx Vivado, and the bitstream was loaded onto the FPGA.
Switches were used to provide the 4-bit inputs for A and B, while LEDs displayed the 8-bit output product.
When tested practically, the FPGA output matched the simulated results, confirming the successful working of the 4-bit Carry-Save Multiplier in real-time hardware.
This validates the design’s efficiency, accuracy, and suitability for high-speed arithmetic operations.
Example Calculation

#To verify the functionality of the Carry-Save Multiplier, the following example was tested:

Input	Binary Value	Decimal Value
A	1010	10
B	0101	5

Expected Output:
Product = A × B = 10 × 5 = 50
Binary Output = 0011 0010

#Simulation Output:
Observed Binary Output = 0011 0010 ✅
Hence, the Carry-Save Multiplier provides the correct 8-bit product output, confirming the design’s accuracy.
#Result Summary

The Carry-Save Multiplier achieved a higher operating frequency with reduced delay due to the elimination of carry propagation at intermediate stages.

The hardware implementation validated the design’s functional correctness and efficiency.

Power and area optimization were achieved while maintaining accurate multiplication results.

The final post-synthesis results confirm that the design is well-suited for high-speed arithmetic units in DSP and VLSI applications.

#Conclusion

The 4-bit Carry Save Multiplier effectively demonstrates a faster and area-efficient multiplication technique using the carry-save approach. It can be extended to higher bit-width multipliers for VLSI and digital processor applications where high-speed arithmetic operations are critical
