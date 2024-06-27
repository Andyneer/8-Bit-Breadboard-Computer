The programming language for this computer is a custom assembly language made up of 11 instructions. An instruction consists of 1 byte of data. The instruction code is the most significant 4 bits. If the instruction uses a parameter such as an address, it is stored in the least significant 4 bits.
If the instruction does not use any parameters, the least significant 4 bits are irrelevant.

| **Instruction** | **Code** | **Description**                                                                                                         |
| :-------------- | :------- | :---------------------------------------------------------------------------------------------------------------------- |
| NOP             | `0000`   |  Do nothing.                                                                                                            |
| LDA(addr)       | `0001`   |  Load the contents of the given address into the A register.                                                            |
| ADD(addr)       | `0010`   |  Add the contents of the given address to the contents of the A register.                                               |
| SUB(addr)       | `0011`   |  Subtract the contents of the given address from the contents of the A register.                                        |
| STA(addr)       | `0100`   |  Store the contents of the A register in the given address.                                                             |
| LDI(val)        | `0101`   |  Load the given value directly into the A register.                                                                     |
| JMP(addr)       | `0110`   |  Jumps to the given address.                                                                                            |
| JC(addr)        | `0111`   |  Jumps to the given address if the carry flag is set.                                                                   |
| JZ(addr)        | `1000`   |  Jumps to the given address if the zero flag is set.                                                                    |
| OUT             | `1110`   |  Output the contents of the A register to the 7-segment display.                                                        |
| HLT             | `1111`   |  Halts the computer.                                                                                                    |

Each instruction executes a set of microinstructions to perform the given operation. A microinstruction consists of a 16-bit control word.

|**Bit**| 15<sup>th</sup> | 14<sup>th</sup> | 13<sup>th</sup> | 12<sup>th</sup> | 11<sup>th</sup> | 10<sup>th</sup> | 9<sup>th</sup> | 8<sup>th</sup> | 7<sup>th</sup> | 6<sup>th</sup> | 5<sup>th</sup> | 4<sup>th</sup> | 3<sup>rd</sup> | 2<sup>nd</sup> | 1<sup>st</sup> | 0<sup>th</sup> |
|---|--- | ---| ---| ---| ---| ---|---|---|---|---|---|---|---|---|---|---|
|**Description**|Halt|Memory Address Register Input|RAM Input|RAM Output|Instruction Register Input| Instruction Register Output|A Register Input|A Register Output|ALU Output|Subtract|B Register Input|Output Register Input|Counter Enable|Counter Output|Jump|Flag Input|
|Short Hand|HLT|MI|RI|RO|II|IO|AI|AO|∑O|SU|BI|OI|CE|CO|J|FI|

Every instruction begins with a 2-microinstruction fetch cycle before performing its other operations.

## Fetch
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  ----|0    | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
|  ----|1    | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |

## NOP
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`0000`|2    | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

## LDA
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`0001`|2    | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|`0001`|3    | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

## ADD
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`0010`|2    | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|`0010`|3    | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
|`0010`|4    | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |

## SUB
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`0011`|2    | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|`0011`|3    | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
|`0011`|4    | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |

## STA
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`0100`|2    | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|`0100`|3    | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

## LDI
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`0101`|2    | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

## JMP
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`0110`|2    | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |

## JC
JC does nothing unless the carry flag is set to 1.
| Code |Step | C 🚩|HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`0111`|2    |0    | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|`0111`|2    |1    | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |

## JZ
JZ does nothing unless the zero flag is set to 1.
| Code |Step | Z 🚩 |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|-------|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`1000`|2    |0      | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|`1000`|2    |1      | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |

## OUT
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`1110`|2    | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |

## HLT
| Code |Step |HLT|MI |RI |RO |II |IO |AI |AO |∑O |SU |BI |OI |CE |CO |J  |FI |
|------|-----|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|`1111`|2    | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
