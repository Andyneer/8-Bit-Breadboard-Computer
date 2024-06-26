The programming language for this computer is a custom assembly language made up of 11 instructions, each instruction executes a set of microinstructions to perform the operation.

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
