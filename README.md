# Design and Functional Verification of Wishbone Memory Subsystem 

This project focuses on the RTL design and functional verification of a Wishbone-based memory subsystem using SystemVerilog. A layered, transaction-based verification environment was developed to validate protocol compliance, read/write correctness, and corner cases using constrained-random testing and self-checking mechanisms.

# RTL Design

Designed an 8-bit wide, 256-depth memory module compliant with the Wishbone bus protocol

Implemented an FSM-based controller supporting:

- **IDLE**
- **MODE CHECK**
- **WRITE**
- **READ**

Supported Wishbone signals:

- `we` (write enable)
- `strb` (strobe)
- `ack` (acknowledge)
- `addr`, `wdata`, `rdata`

Ensured deterministic acknowledgment behavior and correct data handling for all valid transactions

# Verification Architecture

A modular, layered SystemVerilog testbench was developed following UVM-aligned verification principles.

Testbench Components:

Transaction Class
 - Encapsulates Wishbone operations (read, write, random)
 - Uses constrained-random generation
 - Enables transaction reuse and abstraction

Generator
- Produces randomized transactions
- Synchronizes with driver and scoreboard using events
- Controls stimulus flow and test iteration count

Driver
- Converts high-level transactions into pin-level DUT activity
- Handles reset, read, write, and random modes
- Ensures correct Wishbone signal timing

Monitor
- Passively observes DUT interface signals
- Reconstructs transactions from bus activity
- Sends observed transactions to the scoreboard

Scoreboard
- Implements a reference memory model
- Performs data integrity checks for read/write operations
- Detects protocol violations and mismatches automatically

# Project Structure

| **Module File** |                              **Description**                                                       |
|-----------------|----------------------------------------------------------------------------------------------------|
| design.sv       | RTL implementation of the Wishbone-compliant memory module and control logic.                      |
| testbench.sv    | SystemVerilog-based verification environment including generator, driver, monitor, and scoreboard. |
| design.sv.bak   | Backup version of the RTL design file preserved for reference and iterative development.           |
| testbench.sv.bak| Backup version of the testbench used during verification refinement and debugging.                 |
| Wishbone.cr.mti | Questa/ModelSim compiled simulation database generated during verification runs.                   |
| Wishbone.mpf    | ModelSim project file containing simulation configuration, file mappings, and run settings.        |
| README.md       | Project documentation describing design, verification strategy, and results.                       |

# Tools and Technologies

- Languages: Verilog, SystemVerilog
- Methodologies: Constrained-Random Verification, Transaction-Based Verification, Scoreboarding
- Protocols: Wishbone Bus
- Simulation Tools: Questa, ModelSim
- Debugging: Waveform analysis, transaction logging



