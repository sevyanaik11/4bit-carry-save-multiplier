# 4bit-carry-save-multiplier
The 4-bit Carry Save Multiplier performs fast binary multiplication using carry-save addition to minimize delay. Implemented in Verilog and verified on FPGA, it uses switches for inputs and LEDs for outputs. This design achieves high speed, making it ideal for VLSI and DSP applications.
# 🎯 Overview

This project presents the FPGA-based implementation of a 4-bit Carry Save Multiplier (CSM) — a high-speed arithmetic unit that enhances multiplication performance using the carry-save addition technique. The design efficiently computes partial products and reduces propagation delay by storing intermediate carries instead of propagating them immediately. This project demonstrates the design, simulation, synthesis, and implementation of the CSM on an FPGA using Xilinx Vivado with switches as inputs and LEDs as output.

✨ Key Highlights

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
💡 Working Principle

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
┌────────────────────────────────────────────┐
│               SPECIFICATION                │
│        (4-Bit Carry Save Multiplier)       │
└────────────────────────┬───────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────┐
│                RTL DESIGN (Verilog)        │
│    • Partial Product Generation            │
│    • Carry-Save Adder Structure            │
└────────────────────────┬───────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────┐
│          FUNCTIONAL VERIFICATION           │
│    • Testbench Simulation (GTKWAVE)        │
│    • Output Product Verification            │
└────────────────────────┬───────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────┐
│             LOGIC SYNTHESIS (Yosys)        │
│    • Timing Optimization                   │
│    • Area Estimation                        │
└────────────────────────┬───────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────┐
│          PHYSICAL DESIGN (OpenLane)        │
│    • Floorplanning, Placement, Routing      │
│    • Layout and Timing Closure              │
└────────────────────────┬───────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────┐
│        VERIFICATION & SIGNOFF              │
│    • STA (Static Timing Analysis)          │
│    • Power and Area Estimation             │
└────────────────────────────────────────────┘


📊 Results and Performance
Parameter	Value	Unit / Description
Technology Node	130 nm	SkyWater Open-Source PDK
Total Area	1500	µm²
Critical Path Delay	5.10	ns
Maximum Frequency	190	MHz
Total Power	1.15	mW
Total Cell Count	~180	—

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

📚 References

J. M. Rabaey, Digital Integrated Circuits: A Design Perspective.

SkyWater 130nm Open-Source PDK Documentation.

OpenLane and Yosys User Manuals.

FPGA Implementation Guide for Arithmetic Circuits.
