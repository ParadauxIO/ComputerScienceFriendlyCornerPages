# Bit Manipulation

Bit Manipulation concerns everything to do with changing bits (**bi**nary digi**ts**) from 0 to 1 or from 1 to 0 given some value. We can do this by clearing, setting, shifting and rotating binary. The latter two will be covered in a later tutorial. 

Say we have the binary for 49 which is the ascii representation for 1. 

```assembly
0b000110001  @ 49
```

And we want to turn the two ones in bit numbers 5 and 6 to be zeros, that is referred to as *bit clearing* and is done using the `BIC` Instruction. However, in order for the `BIC` Instruction to know which bits we want to modify we have to use something called a mask, which is a binary number with 1s in the places where we wish to change the bits. In our case we want to change the two back-to-back ones in our binary number so we use the mask:

```assembly
0b000110000  @ 48
```

And if you recall from the end of the ASCII-Unicode tutorial, I made reference to this when converting from '1' to 1. The following is the syntax for the BIC or **Bi**t **C**lear instruction. BIC can be be given a branch condition code, like MOV, ADD, and Branch. Rd refers to the destination register, Rn is the input register and Operand2 represents a flexible second operand, which in our case represents a mask. See [Flexible second operand](https://developer.arm.com/documentation/dui0068/b/arm-instruction-reference/arm-general-data-processing-instructions/flexible-second-operand?lang=en) for more details. 

## BIC - Bit Clear - Bitwse AND

```assembly
BIC{cond} Rd, Rn, Operand2
```

```assembly
Main:
	LDR R0, =49
	BIC R0, R0, #48

```

The following clears the bits (sets them to 0) as per our mask outlined above, leaving us with 

```assembly
0b00000001
```

or simply 1. 

## ORR - Bitwise OR

ORR Follows the same syntax as BIC and performs the opposite function, it sets bits. So if we had 1 and wanted to convert it to '1' we could set the 5th and 6th bits to be one using the same mask as before.

```assembly
Main:
	LDR R0, =49
	BIC R0, R0, #48 @ 9
	
	ORR R0, R0, #48 @ 49 again
```

## AND

And performs the same task as `BIC` however 

## EOR (XOR) - Exclusive OR

## RXX 

## Truth Tables 





