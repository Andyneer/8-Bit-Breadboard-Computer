# Fibonacci Sequence
|**Memory Address**|**Instruction**|**Memory Contents**|**Description**|
|:----------------:|---------------|:-----------------:|---------------|
|0|LDI 1|`0101` `0001`| Load 1 into the A register|
|1|STA 14|`0100` `1110`|Store the contents of the A register in address 14|
|2|LDI 0|`0101` `0000`| Load 0 into the A register|
|3|STA 15|`0100` `1111`|Store the contents of the A register in address 15|
|4|OUT|`1110` `----`|Output the contents of the A register to the 7-segment display|
|5|LDA 14|`0001` `1110`|Load the contents of address 14 into the A register|
|6|ADD 15|`0010` `1111`|Add the contents of address 15 to the contents of the A register|
|7|STA 14|`0100` `1110`|Store the contents of the A register in address 14|
|8|OUT|`1110` `----`|Output the contents of the A register to the 7-segment display|
|9|LDA 15|`0001` `1111`|Load the contents of address 15 into the A register|
|10|ADD 14|`0010` `1110`|Add the contents of address 14 to the contents of the A register|
|11|JC 13|`0111` `1101`|Jump to address 13 if the carry flag is set|
|12|JMP 3|`0110` `0011`|Jump to address 3|
|13|HLT|`1111` `----`|Halt the computer|
|14|x|`----` `----`|One of the values being added|
|15|y|`----` `----`|The other value being added|

# Fibonacci Sequence (Looping)
|**Memory Address**|**Instruction**|**Memory Contents**|**Description**|
|:----------------:|---------------|:-----------------:|---------------|
|0|LDI 1|`0101` `0001`| Load 1 into the A register|
|1|STA 14|`0100` `1110`|Store the contents of the A register in address 14|
|2|LDI 0|`0101` `0000`| Load 0 into the A register|
|3|STA 15|`0100` `1111`|Store the contents of the A register in address 15|
|4|OUT|`1110` `----`|Output the contents of the A register to the 7-segment display|
|5|LDA 14|`0001` `1110`|Load the contents of address 14 into the A register|
|6|ADD 15|`0010` `1111`|Add the contents of address 15 to the contents of the A register|
|7|STA 14|`0100` `1110`|Store the contents of the A register in address 14|
|8|OUT|`1110` `----`|Output the contents of the A register to the 7-segment display|
|9|LDA 15|`0001` `1111`|Load the contents of address 15 into the A register|
|10|ADD 14|`0010` `1110`|Add the contents of address 14 to the contents of the A register|
|11|JC 13|`0111` `0000`|Jump to address 0 if the carry flag is set|
|12|JMP 3|`0110` `0011`|Jump to address 3|
|13| |`----` `----`|Address not used|
|14|x|`----` `----`|One of the values being added|
|15|y|`----` `----`|The other value being added|
