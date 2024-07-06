The programming language for this computer is a custom assembly language made up of 11 instructions. An instruction consists of 1 byte of data. The instruction code is the most significant 4 bits. If the instruction takes a parameter, it is stored in the least significant 4 bits.
If the instruction does not use any parameters, the least significant 4 bits are irrelevant. When it comes to actually programming the computer, the binary instruction codes and parameters must be manually input into each memory address using the control box.

| **Instruction** | **Code** | **Description**                                                                                                         |
| :-------------- | :------- | :---------------------------------------------------------------------------------------------------------------------- |
| NOP             | `0000`   |  Do nothing.                                                                                                            |
| LDA(address)    | `0001`   |  Load the contents of the given address into the A register.                                                            |
| ADD(address)    | `0010`   |  Add the contents of the given address to the contents of the A register.                                               |
| SUB(address)    | `0011`   |  Subtract the contents of the given address from the contents of the A register.                                        |
| STA(address)    | `0100`   |  Store the contents of the A register in the given address.                                                             |
| LDI(value)      | `0101`   |  Load the given value directly into the A register.                                                                     |
| JMP(address)    | `0110`   |  Jump to the given address.                                                                                             |
| JC(address)     | `0111`   |  Jump to the given address if the carry flag is set.                                                                    |
| JZ(address)     | `1000`   |  Jump to the given address if the zero flag is set.                                                                     |
| OUT             | `1110`   |  Output the contents of the A register to the 7-segment display.                                                        |
| HLT             | `1111`   |  Halt the computer.                                                                                                     |

Each instruction executes a set of microinstructions to perform the given operation. The instruction code and the current step are sent to the microcode EEPROMs which output a corresponding 16-bit control word for that step of the instruction. Each bit of the control word is connected to the relevant module of the computer.
Below is a table which describes what each bit of the control word does.

|**Bit**| 15<sup>th</sup> | 14<sup>th</sup> | 13<sup>th</sup> | 12<sup>th</sup> | 11<sup>th</sup> | 10<sup>th</sup> | 9<sup>th</sup> | 8<sup>th</sup> | 7<sup>th</sup> | 6<sup>th</sup> | 5<sup>th</sup> | 4<sup>th</sup> | 3<sup>rd</sup> | 2<sup>nd</sup> | 1<sup>st</sup> | 0<sup>th</sup> |
|---|--- | ---| ---| ---| ---| ---|---|---|---|---|---|---|---|---|---|---|
|**Description**|Halt|Memory Address Register Input|RAM Input|RAM Output|Instruction Register Input| Instruction Register Output|A Register Input|A Register Output|ALU Output|ALU Subtract|B Register Input|Output Register Input|Program Counter Enable|Program Counter Output|Jump|Flag Register Input|
|**Short Hand**|HLT|MI|RI|RO|II|IO|AI|AO|∑O|SU|BI|OI|CE|CO|J|FI|

### Fetch
A 2-microinstruction fetch cycle runs before every instruction.
This cycle fetches the instruction from the memory and puts it into the instruction register to be executed.
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0    | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
|1    | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |

Below are the microinstructions that run for each instruction after the fetch cycle.

### NOP - `0000`
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### LDA - `0001`
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|3    | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### ADD - `0010`
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|3    | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
|4    | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |

### SUB - `0011`
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|3    | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
|4    | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |

### STA - `0100`
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|3    | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### LDI - `0101`
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### JMP - `0110`
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |

### JC - `0111`
JC does nothing unless the carry flag is set to 1.
|Step | C 🚩|HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    |0    | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|2    |1    | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |

### JZ - `1000`
JZ does nothing unless the zero flag is set to 1.
|Step | Z 🚩 |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|-------|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    |0      | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|2    |1      | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |

### OUT - `1110`
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |

### HLT - `1111`
|Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2    | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
