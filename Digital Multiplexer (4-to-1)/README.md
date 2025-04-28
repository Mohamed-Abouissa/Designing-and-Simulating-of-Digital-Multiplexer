<div align="center">
  
# Designing and Simulating of Digital Multiplexer (4-to-1)
</div>

This project focuses on the design, simulation, and implementation of a 4-to-1 digital multiplexer using 2-to-1 inverting multiplexers constructed from PMOS and NMOS transistors. A multiplexer (MUX) is a fundamental combinational logic circuit commonly used in digital systems to select one of several input signals and route it to a single output line based on control inputs. Understanding and building multiplexers is essential for developing more complex digital systems such as processors, communication devices, and embedded controllers.

To achieve a complete understanding of the multiplexer’s behavior, we designed the transistor-level circuit using Multisim software. This allowed us to visualize and simulate the behavior of the system at the CMOS transistor level, gaining insight into how logical operations are physically realized in hardware. After verifying the transistor-level design, we transitioned to implementing the system using VHDL (VHSIC Hardware Description Language) and tested it on the DE2-115 FPGA development board. This part of the project focused on writing structured VHDL code, creating testbenches for simulation, and finally uploading the design to the board for real-world verification using switches, LEDs, and seven-segment displays.

The project followed a hierarchical design methodology. First, we designed 2-to-1 inverting multiplexers, and then we combined them to build the full 4-to-1 multiplexer system. Throughout the project, special attention was paid to both the logic behavior and the hardware efficiency of the design. Simulation waveforms were analyzed to validate functionality across all input combinations, ensuring the design met the intended logic before hardware testing. Overall, this project provided valuable hands-on experience in transistor-level CMOS design, digital logic synthesis using VHDL, simulation analysis, and FPGA-based circuit implementation, strengthening both theoretical knowledge and practical skills essential for digital systems engineering.

##  PMOS, NMOS, and CMOS Transistors: Working Principles

In modern digital electronics, transistors play a vital role as the fundamental building blocks of all logic circuits. Among the different types of transistors, the MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor) is the most widely used due to its high switching speed and low power consumption. MOSFETs come in two main types: NMOS (N-type MOSFET) and PMOS (P-type MOSFET), each having distinct characteristics and operating principles.

- **NMOS (N-type MOSFET)**: In an NMOS transistor, electrons are the majority carriers, making it faster in switching operations. The transistor is turned on (conducting state) when a high voltage (logic 1) is applied to the gate terminal relative to the source. In this state, a conductive channel forms between the drain and the source, allowing current to flow easily. When the gate voltage is low (logic 0), the NMOS transistor is in the off state, and current does not flow.

- **PMOS (P-type MOSFET)**: In contrast, a PMOS transistor operates with holes as the majority carriers. A PMOS transistor is turned on when a low voltage (logic 0) is applied to the gate terminal relative to the source, creating a conductive channel. When a high voltage (logic 1) is applied to the gate, the PMOS device switches off. PMOS transistors typically have slower mobility compared to NMOS, leading to slower switching speeds, but they offer benefits like lower leakage currents.

- **CMOS (Complementary MOS)**: CMOS technology integrates both NMOS and PMOS transistors to build efficient logic gates. In a CMOS circuit, when one transistor (either PMOS or NMOS) is on, the other is off. This complementary behavior results in very low static power consumption because current only flows during switching transitions, not in a steady state.

The use of CMOS technology enables the development of dense, power-efficient, and highly reliable digital circuits. CMOS forms the backbone of modern microprocessors, memory chips, and virtually all integrated circuits used today.


