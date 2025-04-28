<div align="center">
  
# Designing and Simulating of Digital Multiplexer (4-to-1)
</div>

This project focuses on the design, simulation, and implementation of a 4-to-1 digital multiplexer using 2-to-1 inverting multiplexers constructed from PMOS and NMOS transistors. A multiplexer (MUX) is a fundamental combinational logic circuit commonly used in digital systems to select one of several input signals and route it to a single output line based on control inputs. Understanding and building multiplexers is essential for developing more complex digital systems such as processors, communication devices, and embedded controllers.

To achieve a complete understanding of the multiplexer’s behavior, we designed the transistor-level circuit using Multisim software. This allowed us to visualize and simulate the behavior of the system at the CMOS transistor level, gaining insight into how logical operations are physically realized in hardware. After verifying the transistor-level design, we transitioned to implementing the system using VHDL (VHSIC Hardware Description Language) and tested it on the DE2-115 FPGA development board. This part of the project focused on writing structured VHDL code, creating testbenches for simulation, and finally uploading the design to the board for real-world verification using switches, LEDs, and seven-segment displays.

The project followed a hierarchical design methodology. First, we designed 2-to-1 inverting multiplexers, and then we combined them to build the full 4-to-1 multiplexer system. Throughout the project, special attention was paid to both the logic behavior and the hardware efficiency of the design. Simulation waveforms were analyzed to validate functionality across all input combinations, ensuring the design met the intended logic before hardware testing. Overall, this project provided valuable hands-on experience in transistor-level CMOS design, digital logic synthesis using VHDL, simulation analysis, and FPGA-based circuit implementation, strengthening both theoretical knowledge and practical skills essential for digital systems engineering.

<details>
  <summary>PMOS, NMOS, and CMOS Transistors: Working Principles</summary>
<br>

In modern digital electronics, transistors play a vital role as the fundamental building blocks of all logic circuits. Among the different types of transistors, the MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor) is the most widely used due to its high switching speed and low power consumption. MOSFETs come in two main types: NMOS (N-type MOSFET) and PMOS (P-type MOSFET), each having distinct characteristics and operating principles.

- **NMOS (N-type MOSFET)**: In an NMOS transistor, electrons are the majority carriers, making it faster in switching operations. The transistor is turned on (conducting state) when a high voltage (logic 1) is applied to the gate terminal relative to the source. In this state, a conductive channel forms between the drain and the source, allowing current to flow easily. When the gate voltage is low (logic 0), the NMOS transistor is in the off state, and current does not flow.

- **PMOS (P-type MOSFET)**: In contrast, a PMOS transistor operates with holes as the majority carriers. A PMOS transistor is turned on when a low voltage (logic 0) is applied to the gate terminal relative to the source, creating a conductive channel. When a high voltage (logic 1) is applied to the gate, the PMOS device switches off. PMOS transistors typically have slower mobility compared to NMOS, leading to slower switching speeds, but they offer benefits like lower leakage currents.

- **CMOS (Complementary MOS)**: CMOS technology integrates both NMOS and PMOS transistors to build efficient logic gates. In a CMOS circuit, when one transistor (either PMOS or NMOS) is on, the other is off. This complementary behavior results in very low static power consumption because current only flows during switching transitions, not in a steady state.

The use of CMOS technology enables the development of dense, power-efficient, and highly reliable digital circuits. CMOS forms the backbone of modern microprocessors, memory chips, and virtually all integrated circuits used today.

<div align="center">
  <img src="Pics/2.png" alt="PMOS, NMOS, and CMOS" width="1050" height="500">
</div>
<br>

Understanding how PMOS and NMOS transistors behave individually and together in CMOS is critical to designing complex circuits like multiplexers at the transistor level.

</details>

<details>
  <summary>Multiplexer (MUX): Definition and Function</summary>
<br>

A multiplexer (MUX) is a fundamental combinational logic device that selects one of several input signals and forwards the selected input to a single output line. It functions as a digital data selector, making it possible for multiple input signals to share a single communication line or resource. The selection process is controlled by selection inputs (also called control lines), and the number of these selection lines depends on the number of inputs. In general, an N-to-1 multiplexer requires log(N) selection lines. For example, a 2-to-1 multiplexer requires one select line, a 4-to-1 multiplexer requires two select lines, and an 8-to-1 multiplexer requires three select lines.

In a 4-to-1 multiplexer specifically, there are four data inputs (usually labeled D0, D1, D2, and D3), two select lines (S1 and S0), and one output (Y). The select lines determine which data input is connected to the output. The functionality can be described as follows: when the select lines are set to (S1, S0) = (0, 0), the output Y will follow input D0. If the select lines are (0, 1), the output will be D1; if they are (1, 0), the output will be D2; and if they are (1, 1), the output will be D3. This mechanism allows a single output line to dynamically switch between multiple inputs based on control signals.

<div align="center">
  <img src="Pics/3.png" alt="4-to-1 MUX" width="1050" height="500">
</div>
<br>

Multiplexers are essential components in digital systems and have wide applications in areas such as data routing, communication systems, arithmetic operations, and control unit design. They help to simplify circuit design by reducing the number of required components. Instead of having separate wiring for each input, a multiplexer enables efficient use of hardware resources by controlling multiple inputs through a smaller number of control lines. Their ability to selectively manage data paths makes them critical in optimizing system performance and circuit scalability in modern electronics.

</details>

<details>
  <summary>Justification for Using 2-to-1 Inverting MUX for Designing a 4-to-1 MUX</summary>
  <br>

Designing a 4-to-1 multiplexer directly at the transistor level can quickly become complex and inefficient, especially when working with PMOS and NMOS devices. To address this, a more organized and modular approach is to first design a 2-to-1 inverting multiplexer and then use these building blocks to construct the 4-to-1 MUX. This method not only simplifies the design process but also improves the clarity and manageability of the circuit during analysis and simulation. 

The main reasons for choosing a 2-to-1 inverting MUX as the base unit include:

- **Simplicity in Design**: A 2-to-1 inverting MUX is straightforward to implement using a small number of transistors, making it easier to draw, simulate, and debug.

- **Reduction of Transistor Count**: By reusing a simple 2-to-1 block multiple times, the overall transistor count remains optimized, which is critical for minimizing chip area and power consumption.

- **Ease of Analysis**: It is much easier to analyze the behavior of a small, predictable building block than to handle a large, complex circuit all at once.

- **Hierarchy and Scalability**: Using smaller modules allows for a hierarchical design structure, where multiple 2-to-1 MUXes are combined logically to form larger multiplexers, enhancing scalability and reusability.

By first constructing 2-to-1 inverting MUXes and then connecting them appropriately, the final 4-to-1 multiplexer can be realized efficiently with minimal design overhead. Additionally, the inversion introduced by the inverting MUX can be systematically corrected either logically or at later stages in the circuit, offering flexibility in achieving the desired final output behavior.

<div align="center">
  <img src="Pics/4.png" alt="4-to-1 MUX Using 2-to-1 MUX" width="1050" height="500">
</div>
<br>

Further advantages of this modular design approach are:

- Simplified Simulation and Testing: Smaller modules are easier to test individually before being combined into the final design.
  
- Logical Organization: The clear division into blocks makes the overall circuit structure easier to understand and present.
  
- Better Performance Control: The designer can better control signal delays, loading effects, and switching behavior by analyzing each stage separately.

Thus, using a 2-to-1 inverting multiplexer structure provides both practical and theoretical advantages, ensuring a more successful and optimized implementation of the 4-to-1 multiplexer.

</details>

## Design of the 4-to-1 MUX

In digital systems, controlling the flow of data efficiently is crucial for proper operation and performance. One of the essential devices used to achieve this control is the multiplexer (MUX). A multiplexer selects one of several input signals and forwards it to a single output line, based on specific control inputs known as selection lines. In this section, we focus on the design and operation of a 4-to-1 multiplexer (4-to-1 MUX), which handles four input signals using two selection lines. We will discuss the concept of the 4-to-1 MUX, derive its logic expression, and present its corresponding truth table to provide a comprehensive understanding of its functionality and role in digital circuit design.

<details>
<summary>Concept of a 4-to-1 Multiplexer</summary>
<br>

A multiplexer (MUX) is a digital device that selects one input signal from several available input lines and forwards it to a single output line. It is essentially a data selector, which is useful for routing data in digital circuits. The 4-to-1 MUX specifically has four input lines, two selection lines, and one output line. The main purpose of this device is to choose one of the four inputs based on the values of the selection lines and then pass the chosen input to the output. 

The operation of the 4-to-1 multiplexer is simple but very powerful. It uses two selection lines, `S1 and S0`, to determine which of the four input lines `(D0, D1, D2, D3)` should be connected to the output Y. The selection lines act like a binary control signal that picks the appropriate input. By adjusting the values of S1 and S0, the MUX can be programmed to select any one of the four inputs. For example, if `S1 = 0 and S0 = 1`, the output will be connected to `D1`.

The versatility of the 4-to-1 MUX is vital in many applications, especially when it comes to controlling data flow or routing multiple signals through a single channel. It is often used in communication systems, data multiplexing, and digital circuits to manage the complexity of handling multiple signals without requiring multiple physical paths.

</details>

<details>
  <summary>Logic Expression Derivation for 4-to-1 MUX</summary>
  <br>

To describe the behavior of the 4-to-1 MUX in a more formal way, we derive the logic expression for the output in terms of the selection lines and the input lines. This expression will dictate the behavior of the MUX based on the different combinations of S1 and S0. Since the MUX has four inputs, the logic expression is a combination of these inputs and the selection signals.

The logic expression for the 4-to-1 multiplexer is derived from the following truth table:

$$
Y = (\overline{S1} \cdot \overline{S0} \cdot D0) + (\overline{S1} \cdot S0 \cdot D1) + (S1 \cdot \overline{S0} \cdot D2) + (S1 \cdot S0 \cdot D3)
$$

This equation shows how each of the inputs (D0, D1, D2, D3) is selected based on the values of S1 and S0:

- When S1 = 0 and S0 = 0, the output Y will be equal to D0.
- When S1 = 0 and S0 = 1, the output Y will be equal to D1.
- When S1 = 1 and S0 = 0, the output Y will be equal to D2.
- When S1 = 1 and S0 = 1, the output Y will be equal to D3.

This logic expression highlights the fact that the two selection lines control which input is passed through to the output. It is essentially a series of AND and OR operations that determine the output based on the selection of inputs.

</details>

<details>
  <summary>Truth Table of the 4-to-1 MUX</summary>
  <br>

The truth table of a multiplexer is a tabular representation that shows how the selection lines control the output. It is a crucial part of understanding how a digital circuit like a multiplexer behaves under different conditions. For a 4-to-1 multiplexer, the truth table lists all possible combinations of the two selection lines (S1 and S0) and the corresponding
output for each combination.

The truth table for the 4-to-1 MUX is as follows:

<div align="center">

| S1 | S0 | Output (Y) |
|----|----|------------|
| 0  | 0  | D0         |
| 0  | 1  | D1         |
| 1  | 0  | D2         |
| 1  | 1  | D3         |

</div>

This truth table clearly shows the relationship between the selection lines and the output. Each combination of S1 and S0 corresponds to one of the four inputs, and the output reflects the value of the selected input. When both S1 and S0 are 0, the output is equal to D0, when S1 = 0 and S0 = 1, the output is D1, and so on for the other combinations.

By examining this table, we can easily visualize how the selection lines determine which input is passed to the output. This is the foundation for the logic design of the multiplexer, and the truth table will be used in the implementation phase to ensure that the MUX behaves correctly.

</details>

## VHDL Implementation




