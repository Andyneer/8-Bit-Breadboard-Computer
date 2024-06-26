The programming language for this computer is a custom assembly language made up of 11 instructions. An instruction consists of 1 byte of data. The instruction code is the most significant 4 bits. If the instruction uses a parameter such as an address, it is stored in the least significant 4 bits.
If the instruction does not use any parameters, the least significant 4 bits are irrelevant.

| Instruction | Code | Description                                                                                                             |
| ----------- | ---- | ----------------------------------------------------------------------------------------------------------------------- |
| NOP         | 0000 |  Do nothing.                                                                                                            |
| LDA(addr)   | 0001 |  Load the contents of the given address into the A register.                                                            |
| ADD(addr)   | 0010 |  Add the contents of the given address to the contents of the A register and store the result in the A register.        |
| SUB(addr)   | 0011 |  Subtract the contents of the given address from the contents of the A register and store the result in the A register. |
| STA(addr)   | 0100 |  Store the contents of the A register in the given address.                                                             |
| LDI(val)    | 0101 |  Load the given value directly into the A register.                                                                     |
| JMP(addr)   | 0110 |  Jumps to the given address.                                                                                            |
| JC(addr)    | 0111 |  Jumps to the given address if the carry flag is set.                                                                   |
| JZ(addr)    | 1000 |  Jumps to the given address if the zero flag is set.                                                                    |
| OUT         | 1110 |  Output the contents of the A register to the 7-segment display.                                                        |
| HLT         | 1111 |  Halts the computer.                                                                                                    |

Each instruction executes a set of microinstructions to perform the given operation. A microinstruction consists of a 16-bit control word.

| 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|--- | ---| ---| ---| ---| ---|---|---|---|---|---|---|---|---|---|---|
|Halt|Mem. Addr. Reg. In|RAM In|RAM Out|Instr. Reg. In| Instr. Reg. Out|A Reg. In|A Reg. Out|ALU Out|Subtract|B Reg. In|Output Reg. In|Counter Enable|Counter Out|Jump|Flags In|
