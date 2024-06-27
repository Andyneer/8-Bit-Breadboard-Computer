
|**Memory Address**|**Instruction**|**Memory Contents**|**Description**|
|:----------------:|---------------|:-----------------:|---------------|
|0|LDA 14|`0001` `1110`| Load the contents of address 14 into the A register|
|1|SUB 12|`0011` `1100`|Subtract the contents of address 12 from the contents of the A register|
|2|JC 6|`0111` `0110`|Jump to address 6 if the carry flag is set|
|3|LDA 13|`0001` `1101`|Load the contents of address 13 into the A register|
|4|OUT|`1110` `----`|Output the contents of the A register to the 7-segment display|
|5|HLT|`1111` `----`|Halt the computer|
|6|STA 14|`0100` `1110`|Store the contents of the A register in address 14|
|7|LDA13|`0001` `1101`|Load the contents of address 13 into the A register|
|8|ADD 15|`0010` `1111`|Add the contents of address 15 to the contents of the A register|
|9|STA 13|`0100` `1101`|Store the contents of the A register in address 13|
|10|JMP 0|`0110` `0000`|Jump to address 0|
|11|----|`----` `----`|Address not used|
|12|1|`0000` `0001`|The value 1|
|13|product|`0000` `0000`|Where the resulting product will be stored|
|14|x| |One of the values to multiply|
|15|y| |The other value to multiply|
