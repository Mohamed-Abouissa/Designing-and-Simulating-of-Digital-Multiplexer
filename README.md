<div align="center">
  
# Designing-and-Simulating-of-Digital-Multiplexer
</div>

This project presents the design and simulation of a 4-to-1 digital multiplexer using only 2-to-1 inverting multiplexers constructed from NAND and NOT gates at the transistor level. A 2-to-1 MUX was first built using three NAND gates and one NOT gate, and then used as a module to create the complete 4-to-1 multiplexer. The project involved deriving the logic expressions, creating truth tables, implementing VHDL code, drawing transistor- level circuits, and verifying the functionality through simulations. Special care was taken to ensure correct selection line behavior and accurate transistor connections. The final design requires 42 transistors and successfully operates as intended, demonstrating a modular, efficient, and expandable approach to digital system design.

For this project, we selected the DE1-115 FPGA development board from Intel (formerly Altera) as our main hardware platform. The DE1-115 board is built around the Cyclone IV EP4CE115 FPGA chip, offering a high number of logic elements, memory blocks, and multipliers, which made it highly suitable for complex digital system designs. In addition to the FPGA itself, the board includes a wide range of onboard peripherals such as SDRAM, Flash memory, Ethernet port, audio input/output, VGA output, USB ports, and an SD card slot, providing extensive options for developing and testing hardware and embedded systems. The presence of switches, push-buttons, LEDs, and seven-segment displays also made it easy to interact with and debug our designs during development.

Below is a photo of the DE1-115 FPGA board used in our project:

<div align="center">
  <img src="Photos/DE-115.png" alt="Digital Multiplexer Diagram" width="1050" height="600">
</div>
<br>

The DE1-115 board's rich feature set was crucial to the success of our work. It allowed us to implement, test, and verify our designs in real hardware, ensuring real-time performance and accurate behavior. The board’s SDRAM and Flash memory enabled us to store large datasets and configuration files, while the VGA output allowed us to display system outputs graphically when needed. Furthermore, the abundant general-purpose I/O pins provided flexibility to connect external sensors and devices if required. Overall, the DE1-115 board offered a powerful and versatile development environment that significantly contributed to the project's efficiency and reliability.


