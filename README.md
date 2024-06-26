# 8-Bit-Breadboard-Computer
This project follows Ben Eater's series on building a programmable breadboard computer using the SAP-1 (Simple-As-Possible-1) computer architecture outlined in Paul Malvino's book: "Digital Computer Electronics".
It was built using 7400-series transistor–transistor logic chips and a few EEPROMs to store microcode and decode input for the 7-segment displays.
Modules were built and tested individually before combining them all with the bus and control logic.
The computer has only 16 Bytes of RAM so programs are quite limited but it is Turing complete.

Ben Eater's Series:
https://youtube.com/playlist?list=PLowKtXNTBypGqImE405J2565dvjafglHU&si=T-VIjqWlPINV_P_u

Finished Build Diagram:
![8-bit computer diagram](https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/8c201af0-f3b9-4e81-ae10-88bd3f7d4240)

Fibonacci Sequence Demo:
https://youtu.be/hMcOJK3IJHs

Finished Controls and Multiplication Demo:
https://youtu.be/AokFEmNVFQk

The programming language for the computer is a custom assembly language with 11 Instructions:
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

Additional information for how each instruction works is available in the [Programming-Language.md](Programming-Language.md) file

Arduino EEPROM Programmer:
![EEPROM Programmer](https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/4b1a490d-1e85-40b4-b276-feb9e0df7762)

EEPROM Programmer Arduino Code:
https://github.com/beneater/eeprom-programmer/tree/master

Simple-As-Possible-1 Computer Architecture - "Digital Computer Electronics" by Albert Paul Malvino, page 140:
![SAP-1 Architecture](https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/ca557870-c1c1-4004-a7bc-5e941358bff1)

Schematics - Credit Ben Eater https://eater.net

High-Level Overview:
<img width="890" alt="high-level" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/14fe68f3-9eb1-4c80-885a-17a2a1f34d7c">

Clock Module:
<img width="1314" alt="clock" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/6646c655-a451-41b6-971c-34c5ec028bbc">

A Register:
<img width="1193" alt="a-register" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/4c5da3d8-df1b-4bbf-a5bb-f6754ecf6c3e">

B Register:
<img width="1202" alt="b-register-1" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/0a204da4-4c27-4b25-9dd2-ab528a617e9f">

Instruction Register:
<img width="1124" alt="instruction-register" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/3c73cf02-e06d-42cc-8965-48d41d453bd7">

Arithmetic Logic Unit (ALU):
<img width="1427" alt="alu" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/b14e982f-f6f4-49f2-91ed-7cbf42902d84">

Memory Address Register (MAR):
<img width="1128" alt="memory-address-register" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/86fc4211-26fa-4312-a12e-8baa68d8c02f">

Random Access Memory (RAM):
<img width="1409" alt="ram" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/55bb503e-b215-45a2-ad43-28f69c15fe72">

Program Counter:
<img width="972" alt="program-counter" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/41bd989e-fff1-40d9-9422-a1a4b4048f73">

Output Register:
<img width="1411" alt="output" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/d40a9d81-3915-44c2-8369-eca7a86a886d">

Control Logic:
<img width="1403" alt="control-logic" src="https://github.com/Andyneer/8-Bit-Breadboard-Computer/assets/90639840/7ccfa138-bb09-4dd9-ba20-af355113857d">







