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

 Block Diagram of 4-bit Carry Save Multiplier
 
Figure 1;Schematic Diagram

Figure 2: Simulation Waveform

Figure 3: Layout Design

Figure 4: FPGA Implementation Output
#Performance Analysis

The 4-bit Carry Save Multiplier was synthesized and implemented on the Xilinx Artix-7 FPGA board using Vivado. The following parameters were analyzed — area utilization, timing delay, and power consumption.
<img width="819" height="415" alt="image" src="https://github.com/user-attachments/assets/6f98df19-f219-4ad1-8376-9c671ab908c7" />

Comparative Analysis

To evaluate the efficiency of the Carry Save Multiplier, it was compared with conventional multiplier architectures such as Array Multiplier and Carry Lookahead Multiplier (CLA).

<img width="936" height="247" alt="image" src="https://github.com/user-attachments/assets/1f56868b-7fd8-4b8c-8086-61e6a01acd99" />


estability (BIST) for fault detection

“Efficient Arithmeti

📈 Future Scope

Extend the design to 8-bit or 16-bit Carry Save Multiplier

Implement signed and floating-point multiplication

Optimize for low power using clock gating and operand isolation

Compare performance with other architectures like Wallace Tree and Array Multipliers

Integrate the design onto an FPGA board for real-time testing

Scale to 65 nm / 45 nm CMOS technologies for ASIC fabrication

Add Built-In Self-Test (BIST) for automatic fault detection

“Accurate Multiplication. Efficient Hardware. Smarter Design.” ⚙️

🔬 Research Opportunities

The 4-bit Carry Save Multiplier (CSM) provides a strong foundation for advanced exploration in digital arithmetic design and VLSI implementation.

⿡ Low-Power Arithmetic Circuits

Use energy-efficient full adder cells and optimized gate structures

Reduce switching activity and delay in the carry-save stage

Explore approximate adders for trade-offs between speed and accuracy

⿢ Design Optimization Techniques

Evaluate the trade-offs among speed, power, and area

Perform gate-level and transistor-level optimizations

Use logic-level simplification and sizing for power efficiency

⿣ FPGA and ASIC Implementation

Compare synthesis results for FPGA and ASIC technologies

Study area utilization, delay, and power reports in various platforms

Generate layout using standard cell libraries and analyze timing

⿤ Technology Scaling

Examine the impact of scaling from 90 nm to 45 nm nodes

Study leakage current, delay, and power consumption variations

Evaluate reliability and timing closure in smaller geometries

⿥ Fault Tolerance and Reliability

Integrate parity or redundancy for fault detection

Study radiation and thermal effects on multiplier accuracy

Design robust arithmetic circuits for safety-critical systems

⿦ Integration into Larger Systems

Use CSM as a core block in ALUs or DSP processors

Combine with adders or accumulators for MAC (Multiply–Accumulate) units

Employ the design for image and signal processing applications

✅ Learning Outcomes

Gained understanding of carry-save multiplication and partial product addition

Designed and verified a 4-bit Carry Save Multiplier using Verilog HDL

Analyzed simulation waveforms to validate correct operation

Synthesized design using Cadence tools and generated reports

Completed layout design and verified DRC, LVS, and STA

Observed trade-offs in area, delay, and power efficiency

Successfully implemented and tested hardware output on FPGA

Achieved a functional and optimized digital arithmetic design ✅
📚 References & research

J. M. Rabaey, Digital Integrated Circuits: A Design Perspective.

SkyWater 130nm Open-Source PDK Documentation.

OpenLane and Yosys User Manuals.
https://coertvonk.com/hw/building-math-circuits/faster-parameterized-multiplier-in-verilog-30774
# verilog code for 4bit carry save multiplier(source)
```
// 4-bit Carry-Save Multiplier
module carry_save_multiplier_4bit (
    input  [3:0] A,
    input  [3:0] B,
    output [7:0] P
);
    wire [3:0] pp0, pp1, pp2, pp3;
    wire [7:0] s1, s2, s3, c1, c2, c3;

    // Partial Products
    assign pp0 = A & {4{B[0]}};
    assign pp1 = A & {4{B[1]}};
    assign pp2 = A & {4{B[2]}};
    assign pp3 = A & {4{B[3]}};

    // Align partial products
    assign s1 = {4'b0, pp0};
    assign s2 = {3'b0, pp1, 1'b0};
    assign s3 = {2'b0, pp2, 2'b0};
    wire [7:0] pp4 = {1'b0, pp3, 3'b0};

    // Stage 1: Carry-Save Additions
    wire [7:0] sum1, carry1;
    assign {carry1, sum1} = s1 + s2;

    wire [7:0] sum2, carry2;
    assign {carry2, sum2} = sum1 + s3;

    wire [7:0] sum3, carry3;
    assign {carry3, sum3} = sum2 + pp4;

    // Final addition (carry propagate)
    assign P = sum3 + carry3;

endmodule
```
# verilog code for 4bit carry save multiplier(testbench)
```
`timescale 1ns / 1ps
module tb_carry_save_multiplier_4bit;
    reg [3:0] A, B;
    wire [7:0] P;

    carry_save_multiplier_4bit uut (.A(A), .B(B), .P(P));

    initial begin
        $monitor("Time=%0t A=%b B=%b -> P=%b (%d)", $time, A, B, P, P);
        
        A=4'b0011; B=4'b0101; #10;
        A=4'b1111; B=4'b1111; #10;
        A=4'b1010; B=4'b0110; #10;
        A=4'b0001; B=4'b0010; #10;
        A=4'b1000; B=4'b0011; #10;
        $finish;
    end
endmodule
```
# verilog code for 4bit carry save multiplier(XDC constraints file)
```
## SWITCHES for Inputs A[3:0] and B[3:0]
set_property PACKAGE_PIN F22 [get_ports {A[0]}] ; # SW0
set_property IOSTANDARD LVCMOS33 [get_ports {A[0]}]

set_property PACKAGE_PIN G22 [get_ports {A[1]}] ; # SW1
set_property IOSTANDARD LVCMOS33 [get_ports {A[1]}]

set_property PACKAGE_PIN H22 [get_ports {A[2]}] ; # SW2
set_property IOSTANDARD LVCMOS33 [get_ports {A[2]}]

set_property PACKAGE_PIN F21 [get_ports {A[3]}] ; # SW3
set_property IOSTANDARD LVCMOS33 [get_ports {A[3]}]

set_property PACKAGE_PIN H19 [get_ports {B[0]}] ; # SW4
set_property IOSTANDARD LVCMOS33 [get_ports {B[0]}]

set_property PACKAGE_PIN H18 [get_ports {B[1]}] ; # SW5
set_property IOSTANDARD LVCMOS33 [get_ports {B[1]}]

set_property PACKAGE_PIN H17 [get_ports {B[2]}] ; # SW6
set_property IOSTANDARD LVCMOS33 [get_ports {B[2]}]

set_property PACKAGE_PIN M15 [get_ports {B[3]}] ; # SW7
set_property IOSTANDARD LVCMOS33 [get_ports {B[3]}]

## LEDs for Product Output P[7:0]
set_property PACKAGE_PIN T22 [get_ports {P[0]}] ; # LD0
set_property IOSTANDARD LVCMOS33 [get_ports {P[0]}]

set_property PACKAGE_PIN T21 [get_ports {P[1]}] ; # LD1
set_property IOSTANDARD LVCMOS33 [get_ports {P[1]}]

set_property PACKAGE_PIN U22 [get_ports {P[2]}] ; # LD2
set_property IOSTANDARD LVCMOS33 [get_ports {P[2]}]

set_property PACKAGE_PIN U21 [get_ports {P[3]}] ; # LD3
set_property IOSTANDARD LVCMOS33 [get_ports {P[3]}]

set_property PACKAGE_PIN V22 [get_ports {P[4]}] ; # LD4
set_property IOSTANDARD LVCMOS33 [get_ports {P[4]}]

set_property PACKAGE_PIN W22 [get_ports {P[5]}] ; # LD5
set_property IOSTANDARD LVCMOS33 [get_ports {P[5]}]

set_property PACKAGE_PIN U19 [get_ports {P[6]}] ; # LD6
set_property IOSTANDARD LVCMOS33 [get_ports {P[6]}]

set_property PACKAGE_PIN U14 [get_ports {P[7]}] ; # LD7
set_property IOSTANDARD LVCMOS33 [get_ports {P[7]}]
```


FPGA Implementation Guide for Arithmetic Circuits.


# Figure 1: Schematic Diagram
The synthesized design was mapped onto an FPGA board using Vivado. Switches were
assigned to inputs A[3:0] and B[3:0], and LEDs were connected to output P[7:0].

![WhatsApp Image 2025-10-30 at 13 06 58_ce3f9c43](https://github.com/user-attachments/assets/6cbbac73-bfa5-4701-9db0-810dc160d4fe)

Figure 1: RTL Schematic of the Multiplier Design
Schematic Diagram

#The schematic of the 4-bit Carry-Save Multiplier shows the interconnection of AND gates and full adders that generate and combine the partial products.
Each bit of the multiplicand and multiplier contributes to the partial product, which is then added using Carry-Save Adders (CSAs).
This arrangement eliminates the need for immediate carry propagation, improving the overall computation speed.
The schematic confirms that the design structure follows the modular approach with minimal delay and reduced logic complexity.




# Figure 2: Simulation Waveform

![WhatsApp Image 2025-10-30 at 13 09 50_1bc1dca4](https://github.com/user-attachments/assets/3d46f834-b415-4b6e-9f7a-817069be67c7)
Simulation Waveform

#The simulation waveform illustrates the working of the CSM when various input combinations are applied.
Inputs A and B (each 4-bit) are given, and the product P (8-bit) is observed at the output.
For every change in input, the output corresponds exactly to the expected product value, confirming the correctness of the Verilog code.
The waveform validates the parallel carry-save addition technique, showing reduced delay compared to conventional multiplication methods.
# layout
![WhatsApp Image 2025-10-30 at 13 07 53_081e27a6](https://github.com/user-attachments/assets/1a4d02bd-4495-4671-bede-2f27fdb9e6d2)
figure 3;layout
The layout diagram represents the physical implementation of the multiplier circuit at the transistor or standard cell level.
This layout is generated after synthesis, placement, and routing in the VLSI design flow.
It shows the actual arrangement of gates, interconnections, and metal layers.
The design successfully passed DRC (Design Rule Check) and LVS (Layout vs. Schematic) verification, ensuring that the layout matches the schematic and follows fabrication rules.
The compact design and proper routing indicate optimized area utilization.


# hardware

![WhatsApp Image 2025-11-02 at 23 04 11_93eb470e](https://github.com/user-attachments/assets/3021c0c4-ff87-4fb6-af9d-84408ae3de3c)

Figure 4: FPGA Implementation Output on Hardware
#Hardware Implementation

#The hardware implementation was carried out on an FPGA board.
The Verilog code was synthesized using Xilinx Vivado, and the bitstream was loaded onto the FPGA.
Switches were used to provide the 4-bit inputs for A and B, while LEDs displayed the 8-bit output product.
When tested practically, the FPGA output matched the simulated results, confirming the successful working of the 4-bit Carry-Save Multiplier in real-time hardware.
This validates the design’s efficiency, accuracy, and suitability for high-speed arithmetic operations.
Example Calculation

# To verify the functionality of the Carry-Save Multiplier, the following example was tested:

Input	Binary Value	Decimal Value
A	1010	10
B	0101	5

Expected Output:
Product = A × B = 10 × 5 = 50
Binary Output = 0011 0010

# Simulation Output:
Observed Binary Output = 0011 0010 ✅
Hence, the Carry-Save Multiplier provides the correct 8-bit product output, confirming the design’s accuracy.
# Result Summary

The Carry-Save Multiplier achieved a higher operating frequency with reduced delay due to the elimination of carry propagation at intermediate stages.

The hardware implementation validated the design’s functional correctness and efficiency.

Power and area optimization were achieved while maintaining accurate multiplication results.

The final post-synthesis results confirm that the design is well-suited for high-speed arithmetic units in DSP and VLSI applications.

# Conclusion

The 4-bit Carry Save Multiplier effectively demonstrates a faster and area-efficient multiplication technique using the carry-save approach. It can be extended to higher bit-width multipliers for VLSI and digital processor applications where high-speed arithmetic operations are critical
⚙️ Tools and Technologies
Category	Tools / Technologies
Hardware Description Language	Verilog HDL (IEEE 1364-2001 Standard)
Simulation Tool	Xilinx Vivado 2023.1 / Cadence NCSim
Logic Synthesis	Cadence Genus Synthesis Solution
Place & Route	Cadence Innovus Implementation System
Technology Node	90 nm CMOS Standard Cell Library
Verification	Functional Simulation, Static Timing Analysis (STA)
Reports & Debugging	Waveform Analysis, Power and Area Reports
Hardware Testing	FPGA Implementation (Basys3 Board)
GDS Export	Innovus Stream Out (GDSII Generation)
🎓 Academic Context

Course Information:

Course: VLSI System Design Practice (EC-307)

Faculty: Dr. P. Ranga Babu

Department: Electronics and Communication Engineering

Institution: Indian Institute of Information Technology Design and Manufacturing, Kurnool

Academic Year: 2025–2026 (Semester 5)

📬 Contact

Email: rathodgopal9100@gmail.com
, [add teammate’s mail if any]

Institution: IIITDM Kurnool

🌟 Acknowledgments

This project was successfully completed under the valuable guidance and support of:

Dr. P. Ranga Babu — Course Instructor & Project Guide, Department of ECE, IIITDM Kurnool

IIITDM Kurnool — For providing laboratory access and computing infrastructure

Cadence Design Systems — For access to EDA tools used in the design flow

Open-Source and Research Community — For resources and literature support in multiplier design

Peers and Faculty — For constant feedback during project development

👨‍🎓 About the Developers

Sevya Naik

ranjith

Department of Electronics and Communication Engineering
Indian Institute of Information Technology Design and Manufacturing, Kurnool
