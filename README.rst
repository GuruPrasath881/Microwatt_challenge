Microwatt Full UART with TX FIFO

License: MIT

This project is a submission for the Microwatt Momentum Open Hardware Hackathon organized by the OpenPOWER Foundation and ChipFoundry
📖 Project Overview

This project implements a full-featured UART (Universal Asynchronous Receiver/Transmitter) peripheral for the Microwatt POWER-based CPU. It is designed as a memory-mapped peripheral that connects to the system's Wishbone bus.

The primary goal is to create a robust and efficient communication interface that allows the Microwatt SoC to easily send and receive data from external devices, such as a host computer's terminal. The inclusion of a transmit FIFO buffer significantly improves performance by allowing the CPU to offload multiple characters at once, freeing it to perform other tasks.
Features

    Full Duplex Communication: Simultaneous data transmission and reception.
    Wishbone Interface: For easy integration into the Microwatt SoC.
    16-Byte Transmit FIFO: A buffer to store outgoing characters, allowing the CPU to write data in bursts and improve system throughput.
    Single-Byte Receive Buffer: Buffers a single incoming character.
    Configurable Baud Rate: The communication speed can be set by the CPU.
    Standard UART Frame: 8 data bits, no parity, 1 stop bit (8-N-1).

🛠️ Hardware Design

The UART is designed to be memory-mapped, meaning the CPU interacts with it by reading from and writing to a set of control and data registers.
Register Map
Address Offset 	Register Name 	R/W 	Description
0x00 	RX_DATA_REGISTER 	R 	Reading this register returns the character from the receive buffer.
0x04 	TX_DATA_REGISTER 	W 	Writing to this register pushes a character into the transmit FIFO.
0x08 	STATUS_REGISTER 	R 	Contains status flags. Bit 0: rx_data_ready (1=new data available), Bit 1: tx_fifo_full (1=cannot accept new data).
0x0C 	BAUD_DIV_REGISTER 	W 	Writing to this register sets the clock divisor used to generate the baud rate. Divisor = SystemClock / (BaudRate * 16).
📂 Repository Structure

.
├── hdl/              # Contains all Verilog source files for the UART
├── test/             # Verilog testbenches for RTL simulation
├── sw/               # C code for the Microwatt CPU to test the UART
├── openlane/         # Configuration files for the OpenLane hardening flow
├── AI_Prompts/       # Logs of any AI-assisted code generation [TODO: Add your logs here]
├── docs/             # Screenshots and other documentation
├── LICENSE           # The project's open-source license
└── README.md         # This file

🚀 How to Run

Will be added in the future.

This project is licensed under the MIT License. See the LICENSE file for details.
