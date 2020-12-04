# Using Watch Expressions

When using Visual Studio Code (VSC) to write assembly language you will probably want to view what's happening in memory whilst you are running your code. You can do this (via Cortex Debug) in one of two ways; "view memory" as a Ctrl+Shift+P Instruction or using a watch expression. The only problem with the "view memory" option is that it only shows ascii characters next to the hexadecimal literals, which isn't much use to a developer, unless they're well-versed in hexadecimal that is. 

## What is a watch expression?

Essentially it is an expression which monitors certain variables (addresses in memory in our case) for changes, and displays their value. Using watch expressions we can tell VSC to "listen" to certain sections of memory by setting the address, variable type (will become relevant in a few minutes) and the amount of addresses after the specified address we would like to monitor. 

## What does it look like?

![1](https://cdn.paradaux.io/img/3x9c0.png)

Well, it looks like this! On the left hand side you have the cortex registers dialogue as usual but you also have the watch dialogue, this will contain all of the watch expressions we could possibly want. In this example (which is set to Intro to Computing Assignment 5-1) where we are monitoring setC and setA (which refer to the addresses in which setA and setC start, these are defined in test.s)

![2](https://cdn.paradaux.io/img/sc1ot.png)

Here we can see the integer values stored in the addresses beginning at setA (I have it set to display 16 values, labelled 0-15) Negative values are represented in 32 bit two's complement form, which are the large numbers you see above.

## OK, that's cool but how do I create a watch expression?

Well, I'm glad you asked! 

![2](https://cdn.paradaux.io/img/tanjj.png)

Simply go to the right hand side of the "WATCH" header and click the plus

![3](https://cdn.paradaux.io/img/x9i6x.png)

Then type the following in to view setB

```assembly
(unsigned int[16]) setB
```

Alternatively you can suggest a specific address as follows:

```assembly
(unsigned int[16]) 536870912
(unsigned int[16]) 0x20000000 
```

As you can see you can use integer or hexadecimal here. 

You can also switch `unsigned` to `signed` to view negative numbers as negative numbers

![4](https://cdn.paradaux.io/img/9vtbm.png)

int specifies the variable type, the only ones really useful to us are `int` and `char` Char will show us the ascii-character letters rather than integers so like (an example from itoa2)

![5](https://cdn.paradaux.io/img/ex0nd.png)

On the left hand side you can see the integer values associated with the particular `char` followed by a char literal surrounded by single quotes. (`\u000` (unicode) or simply `\000` (ascii) represents null or 0x0.) This of course works for letters too! 

## General form

```assembly
(un/signed type [#]) address
```

The only types which matter for us are `int` which represents ordinary numbers and `char` which represents ascii characters. # is some number (256 is the most you should ever have to use.) 