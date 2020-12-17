# Ascii / Unicode

"American Standard Code for Information Interchange" or ASCII is a set of standards which dictate how computers with interpret binary as characters, symbols and structural things such as a line break in a document. Unicode builds upon ASCII's work, and is the organisation we have to thank for things such as Emoji and the ability to communicate in languages that aren't dependent on the Latin alphabet, like Chinese or Thai. It's how your computer knows that this document is a document with words, and isn't just a meaningless stream of ones and zeroes. 

## What does this have to do with Arm Assembly?

Well, if we want our Assembly Language Programmes to be able to return text, or interpret user input our programme is going to have to understand Arm Assembly. Take numbers for example. The Number 1 and the Character 1 are two different things in ASCII. 

If I were to send you the ascii 1 or 0x1 a computer would interpret that as SOH or Start of Heading which is a meta instruction for computers, but if I sent you 49 or 0x31 the computer will interpret that as the symbol 1, not the mathematical representation of 1. 

This means if you want to take numbers from the user and convert them into their integer equivalents we're going to have to perform some basic arithmetic. If you were to take a look at an ascii table, which is a table showing all ascii characters and their binary / hex/ octal representations.  

![Ascii Table](https://cdn.paradaux.io/img/9zxcp.png)

If you look at the number 1, which is labelled under "SOH" and the symbol one which is number 49 you can see that all the symbol numbers follow each-other. This means that we can easily convert from the symbol form to the integer form by performing some simple arithmetic. We want to subtract the value at 0 (48 / 0x30) to go from the symbol to the character and add the value at 0 to go from integer to symbol form.

## In Practice

```assembly
Main:
	LDR R0,  =10      @ Load integer 10 into a register
	LDR R1,  ='5'     @ Load Character (Symbol) 5 into a register
	LDR R2,  =56      @ Load Character (Symbol) 8 into a register
ConvertToSymbol:
	ADD R0, R0, #0x30 @ Adds a space, converting from Integer to Symbol
	SUB R1, R1, 48    @ Takes a space, converting from Symbol to Integer
	SUB R1, R1, #' '  @ Takes a space, converting from Symbol to Integer
```

If you're reading this tutorial in order, you won't have come across this, but we can also convert integers into symbols and vice versa (knowing the integer/symbol is between 0-9) using bit manipulation. The Mask for this is `0b000110000` or simply 48 / `0x30` The same value we were using for addition/subtraction above. 

```assembly
Main: 
  LDR R1, =9
  ORR R1, R1, #0x30 	@ R1 is now 57 / '9'
  
  LDR R1, ='9'
  BIC R1, R1, #0x30 	@ R1 is now 9 / 0x09
```

