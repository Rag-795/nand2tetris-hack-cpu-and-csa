# Nand2Tetris Hack CPU and CSA (Carry Select Adder)

## Project Overview

This repository contains a complete implementation of the Hack Computer architecture as specified in the "Nand to Tetris" course, with an additional specialized implementation of a Carry-Select Adder (CSA) for optimized addition operations.

The implementation is written in Hardware Description Language (HDL) and is divided into two main parts:

## Part A: Hack CPU Implementation

### Components

- **ALU (Arithmetic Logic Unit)**: Performs various arithmetic and logical operations
- **CPU**: The central processing unit that executes instructions
- **Memory**: Manages the computer's memory system
- **PC (Program Counter)**: Controls the flow of instruction execution
- **Register**: Stores data and addresses
- **Bit**: The fundamental storage element
- **Various Logic Gates**: Building blocks for the architecture (And16, Or16, Not16, Mux16, etc.)

### Implementation Details

The CPU chip is a complex circuit that integrates:
- An ALU for performing computations
- A register for storing the D value
- An A register for storing addresses or values
- A Program Counter (PC) for instruction sequencing
- Logic for decoding and executing instructions

The CPU handles two types of instructions:
- A-instructions (address instructions): Set the A register to a 15-bit value
- C-instructions (compute instructions): Perform operations using the ALU and update registers

### Chip Design
![image](https://github.com/user-attachments/assets/781f1502-4e38-4b01-b7d2-336cee5083d5)

### Testing

The CPU implementation can be tested using the CPU.tst file, which verifies the correct execution of various instructions according to the Hack computer architecture specification.

### Files Structure - Part A

```
CPU/
├── Add16.hdl         # 16-bit adder
├── ALU.hdl           # Arithmetic Logic Unit
├── And16.hdl         # 16-bit AND gate
├── Bit.hdl           # 1-bit register
├── Computer.hdl      # Top-level computer chip
├── CPU.cmp           # Expected output for CPU test
├── CPU.hdl           # Central Processing Unit
├── CPU.tst           # Test script for CPU
├── Inc16.hdl         # 16-bit incrementer
├── Memory.hdl        # RAM and memory-mapped I/O
├── Mux.hdl           # Multiplexer
├── Mux16.hdl         # 16-bit multiplexer
├── Not16.hdl         # 16-bit NOT gate
├── Or16.hdl          # 16-bit OR gate
├── Or16Way.hdl       # 16-way OR gate
├── PC.hdl            # Program Counter
└── Register.hdl      # 16-bit register
```

## Part B: Carry-Select Adder (CSA) Implementation

### Components

The CSA is an optimized adder implementation that improves performance by calculating results for both possible carry input values (0 and 1) in parallel, then selecting the correct result once the actual carry input is known.

### Implementation Details

The Carry-Select Adder optimizes addition by:
1. Computing two possible sums in parallel (assuming carry-in is 0 or 1)
2. Using multiplexers to select the correct result based on the actual carry input
3. Producing both a 16-bit sum and a carry output bit

### Chip Design
![image](https://github.com/user-attachments/assets/10136d23-d3d7-423e-8286-1dd81dce5b32)
![image](https://github.com/user-attachments/assets/d857351a-b214-42a5-8a58-1bcd6ed4dfb5)



### Files Structure - Part B

```
CSA/
├── Add16.hdl         # 16-bit adder with carry for CSA
├── CSA.hdl           # Carry-Select Adder implementation
├── FullAdder.hdl     # Full adder for CSA
├── Mux.hdl           # Multiplexer for CSA
└── Mux16.hdl         # 16-bit multiplexer for CSA
```

## Usage

### Setting Up the Environment

1. **Install the Nand2Tetris Software Suite**:
   - Download the Nand2Tetris Software Suite from the [official website](https://www.nand2tetris.org/software)
   - Extract the downloaded ZIP file to a location on your computer
   - The suite includes the Hardware Simulator, which is needed to test HDL implementations

2. **Clone This Repository**:
   ```bash
   git clone https://github.com/Rag-795/nand2tetris-hack-cpu-and-csa.git
   ```

### Testing the Hack CPU (Part A)

1. **Open the Hardware Simulator**:
   - Navigate to the Nand2Tetris software directory
   - Run `HardwareSimulator.bat` (Windows) or `HardwareSimulator.sh` (macOS/Linux)

2. **Load the CPU Implementation**:
   - In the Hardware Simulator, click "File" > "Load Chip" 
   - Navigate to the CPU directory in this repository
   - Select `CPU.hdl` to load the CPU implementation

3. **Run the CPU Tests**:
   - Click "File" > "Load Script"
   - Select `CPU.tst` from the CPU directory
   - Click "Run" or "Run Script" to execute the test
   - The simulator will compare the actual outputs with the expected outputs defined in `CPU.cmp`
   - Check the comparison results window to verify all tests have passed

4. **Testing Individual Components**:
   - You can similarly load and test other components (ALU.hdl, Register.hdl, PC.hdl, etc.)
   - Each component has its corresponding test script (*.tst) and comparison file (*.cmp)
   - For example, to test the ALU, load `ALU.hdl` and run `ALU.tst`

5. **Testing the Complete Computer**:
   - Load `Computer.hdl` to test the integration of all components
   - Use the provided test scripts to verify the computer's functionality

### Testing the CSA Implementation (Part B)

1. **Load the CSA Implementation**:
   - In the Hardware Simulator, click "File" > "Load Chip"
   - Navigate to the CSA directory
   - Select `CSA.hdl` to load the Carry-Select Adder implementation

2. **Manual Testing of CSA**:
   - After loading the chip, the simulator will display the input and output pins
   - Set input values by clicking on the pins or entering values in the input section
   - Click "Eval" to evaluate the circuit with the given inputs
   - Observe the outputs to verify correct addition with carry

3. **Comparing with Standard Adder**:
   - You can compare the functionality of the CSA with the standard Add16 implementation
   - Load both implementations and test with identical inputs to verify they produce the same results

### Modifying and Extending

1. **Editing HDL Files**:
   - Use any text editor to modify the HDL files
   - Save changes and reload the chip in the Hardware Simulator to test modifications

2. **Creating New Components**:
   - Create new HDL files following the Nand2Tetris HDL syntax
   - New components can use existing components as building blocks

3. **Integrating CSA with CPU**:
   - To use the CSA in place of the standard adder, modify the CPU implementation to reference the CSA components
   - Update relevant component paths in the HDL files

## Credits

This project is based on the Nand2Tetris platform by Noam Nisan and Shimon Schocken. The CSA implementation is a specialized extension to the standard architecture.

* Hari Heman V K ([GitHub](https://github.com/HXMAN76))
* Raghav N ([GitHub](https://github.com/Rag-795))
* Dev Bala Saragesh ([GitHub](https://github.com/dbsaragesh-bs))
* Ghanasree ([GitHub](https://github.com/your-username))

## License

This project is provided as an educational resource. Use in accordance with the Nand2Tetris project licensing.
