# Flow Control

Flow control is the process of controlling how your programme executes. This is done by testing conditions and moving the programme counter respectively. There are 3 primary forms of flow control:

-   If statements 
-   While loops (including do-while)
-   For loops

There are other forms of these loops that you will find in higher-level languages however due to it being difficult to translate into Assembly Language. 

## If statements

If statements are made up of a condition and a body. The body of the statement only executes if the condition is true. 

```pseudocode
x = 5 + 6;
if (x >= 11) {
	print ("X is greater than or equal to 11!");
}
```

The example above shows a typical for loop in a high-level language such as C, Javascript or Java. It contains a condition, which should render down into a Boolean expression (in this case whether or not our variable x is greater than or equal to 11) 

We can have more complicated conditions however, using logical operators. 

```pseudocode
if (x >= 3 || x >= 10) {}
if (x == false && y == true) {}
if ((X && Y) || Z) {}
```

These are accomplished by combining our simple conditions with logical operators, we're only going to be dealing with OR and AND in this particular example.

| \|\|   | Logical OR. Tests if the statement on the left OR the statement on the right is true, if so it is true. |
| ------ | ------------------------------------------------------------ |
| **&&** | **Logical AND. Tests if the statement on the left AND the statement on the right is true, if so it is true.** |

If statements are a logical conclusion to the instructions we have at our disposal in arm assembly. We can construct a simple if statement, similar to the first example above as follows: 

```assembly
Main:
	CMP     Rx, Ry			@ if (x <= y)
	BGT     XGreaterThanY    @ Branch on the opposite condition (>)
	ADD     Rx, Rx, #1
	[...]
XGreaterThanY:
	[...]

End_Main:
```

As you can see above we always branch on the opposite **condition** what this means is that we jump to a later point in our code IF and only IF the condition was the opposite to that we expected, in our case if X was greater than Y (we were testing if it was less than or equal to) `[...]` is just a stand-in for other code your programme may be executing outside the bounds of the examples provided.

## If-else

```assembly
Main:
	CMP     Rx, Ry			  @ If (x < y)
	BHS     XHigherOrEqualToY  @ Branch on the opposite condition (>=)
	MOV     Rz, Rx             @ z = x
	B       EndIf              @ End the if statement
	[...]
XHigherOrEqualToY:
	MOV Rx, Ry                 @ z = y
	[...]
EndIf:
	[...]

End_Main:
	
```

The above assembly-language code is based on this pseudo-code

```pseudocode
if (x < y) {
	z = x;
} else {
	z = y;
}
```

## If - elseif - else 

```assembly
Main:
    CMP R1, #10       @ v < 10
    BHS IfPt2

    MOV R0, #1
    b End_Main
IfPt2:
    CMP R1, #100      @ v < 100
    BHS IfPt3

    MOV R0, #10
    b End_Main
IfPt3:              
    CMP R1, #1000     @ v < 1000
    BHS Else

    MOV R0, #100
    b End_Main
  Else:               @ If none of the above are true
    MOV R0, #0
   
End_Main:
```

Which is a translation of the below pseudocode 

```pseudocode
if (v < 10) {
  a = 1;
} else if (v < 100) {
  a = 10;
} else if (v < 1000) {
  a = 100;
} else {
  a = 0;
}  
```

## If AND

```assembly
Main:
	  CMP R0, #'A'
  	  BLO End_Main
  	  
      CMP R0, #'Z'
      BHI End_Main
      
      ADD R0, R0, #0x20
End_Main:
```

```pseudocode
if (ch >= 'A' && ch <= 'Z') {
  ch = ch + 0x20;
}
```

## If OR

```assembly
Main:
  CMP R1, #'a'
  BEQ StatementWasTrue
  CMP R1, #'e'
  BEQ StatementWasTrue
  CMP R1, #'i'
  BEQ StatementWasTrue
  CMP R1, #'o'
  BEQ StatementWasTrue
  CMP R1, #'u'
  BEQ StatementWasTrue
  
  @ Statement was false if it reached this point without branching.

  MOV R0, #0
  b End_Main 			@ Go to the end so we don't execute our true body

StatementWasTrue:
  MOV R0, 1
 
End_Main:
```

```pseudocode
if (ch=='a' || ch=='e' || ch=='i' || ch=='o' || ch=='u'){
 v = 1;
} else {
 v = 0;
}
```





STUB: To be continued with more English explanations. 