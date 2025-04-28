<div align="center">
  
# Designing and Simulating of Digital Multiplexer (4-to-1)
</div>

This project focuses on the design, simulation, and implementation of a 4-to-1 digital multiplexer using 2-to-1 inverting multiplexers constructed from PMOS and NMOS transistors. A multiplexer (MUX) is a fundamental combinational logic circuit commonly used in digital systems to select one of several input signals and route it to a single output line based on control inputs. Understanding and building multiplexers is essential for developing more complex digital systems such as processors, communication devices, and embedded controllers.

To achieve a complete understanding of the multiplexer’s behavior, we designed the transistor-level circuit using Multisim software. This allowed us to visualize and simulate the behavior of the system at the CMOS transistor level, gaining insight into how logical operations are physically realized in hardware. After verifying the transistor-level design, we transitioned to implementing the system using VHDL (VHSIC Hardware Description Language) and tested it on the DE2-115 FPGA development board. This part of the project focused on writing structured VHDL code, creating testbenches for simulation, and finally uploading the design to the board for real-world verification using switches, LEDs, and seven-segment displays.

The project followed a hierarchical design methodology. First, we designed 2-to-1 inverting multiplexers, and then we combined them to build the full 4-to-1 multiplexer system. Throughout the project, special attention was paid to both the logic behavior and the hardware efficiency of the design. Simulation waveforms were analyzed to validate functionality across all input combinations, ensuring the design met the intended logic before hardware testing. Overall, this project provided valuable hands-on experience in transistor-level CMOS design, digital logic synthesis using VHDL, simulation analysis, and FPGA-based circuit implementation, strengthening both theoretical knowledge and practical skills essential for digital systems engineering.

###  PMOS, NMOS, and CMOS Transistors: Working Principles
