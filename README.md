# 4-bit BCD Adder 

## Overview
A hardware implementation of a Binary-Coded Decimal (BCD) adder that takes two 4-bit BCD digits and a carry-in, producing a two-digit BCD sum displayed on 7-segment displays.

## Features
- Adds two BCD digits (0-9) with carry-in
- Displays inputs and sum on 7-segment displays
- Error detection for invalid BCD inputs (>9)
- Handles sums up to 19 (9+9+1)

## Hardware Setup
### Inputs
- `SW7-4`: Input A (first BCD digit)
- `SW3-0`: Input B (second BCD digit)  
- `SW8`: Carry-in (cin)

### Outputs
- `HEX5`: Displays input A
- `HEX3`: Displays input B
- `HEX1-HEX0`: Shows BCD sum (S1S0)
- `LEDR`: Binary sum indicators
- `LEDR9`: Error light (on when A or B > 9)

## Design Logic
The adder uses:
1. A 4-bit adder core for binary addition
2. BCD correction logic:
   ```pseudo
   T0 = A + B + c0
   if (T0 > 9) then
       Z0 = 10
       c1 = 1
   else
       Z0 = 0
       c1 = 0
   end if
   S0 = T0 - Z0
   S1 = c1

## Usage
Set inputs using switches:
- `SW7-4`: Input A (first digit)
- `SW3-0`: Input B (second digit)
- `SW8`: Carry-in (cin)

View outputs:
- Input values: `HEX5` (A) and `HEX3` (B)
- BCD sum result: `HEX1` (tens digit) and `HEX0` (units digit)
- Error indicator: `LEDR9` (lights when input > 9)

## Implementation
- Hybrid design combining:
  - Structural 4-bit adder core
  - Behavioral VHDL for BCD correction
- FPGA-optimized implementation
- Clean, maintainable code using VHDL operators

## Performance Metrics
- **Logic Cells Used**: 34

## Acknowledgments
This project was developed as part of the **FPGA Design for Embedded Systems** specialization capstone project offered by the **University of Colorado Boulder** on Coursera. Special thanks to:

- Course instructors for their guidance on FPGA design methodologies
- Terasic for providing the DE10-Lite development board documentation
- Intel FPGA University Program for their educational resources

The original project requirements and constraints were provided as part of the course curriculum, with implementation details and optimizations developed independently.
