# Dictionary

## Week 1

| Term | Definition |
| ------ | ------------ |
|JDK| Java Development Kit - A bundle of software including a java compiler and java runtime envoirnment |
|Compiler| A Compiler is a program which turns source code into machine code (or in the case of java; bytecode.) |
|IDE| Integrated Development Environment - A text editor which is usually bundled with various development utilities such as a compiler and debugger. |
|Eclipse| An antiquated IDE circa 2001 |
|IntelliJ IDEA| A modern IDE for Java development |
|Class| A blueprint for creating objects. |
|Main method| The Entry point to a Java Program |
|Variable| A placeholder which stores some (changeable) value. |
|Constant| A placeholder which never changes its value. |
|Computation| The process of computing |
|Compiling| The process of turning source code into machine code |
|Interpreting| The process of translating one statement at a time into machine code. Usually occurs at runtime. Languages such as Python do this. |
## Week 2

### Primitive Types

| Term | Definition | Size (Bits) | Minimum | Maximum | Boxed Object Equivalent |
|------|------------|------|------|------|------|
| byte | Similar to int but only takes up 8 bits of memory. | 8 | -2<sup>7</sup> | 2<sup>7</sup>-1 | Byte |
| short | Used to represent floating-point numbers, with a greater range than the float type | 16 | -2<sup>15</sup> | 2<sup>15</sup>-1 | Short |
| int | A simple 32-bit two's complement integer, | 32 | -2<sup>31</sup> | 2<sup>31</sup>-1 | Integer |
| long | int with a greater range. | 64 | -2<sup>63</sup> | 2<sup>63</sup>-1 | Long |
| float | Used to store simple fractional numbers with single-precision meaning after 6 digits it begins to loose accuracy. See BigDecimal for dealing with large precise decimal figures. | 32 | -2<sup>-149</sup> | (2-2<sup>-23</sup>).2<sup>127        | Float                   |
| double | Used to store less simple fractional numbers with double-precision. | 64 | -2<sup>-1074</sup> | (2-2<sup>-52</sup>).2<sup>1023</sup> | Double |
| char | 16-bit integer representing Unicode/ascii characters from \u0000 to \uffff | 16 | 0 | 2<sup>16</sup>-1 | Char |
| boolean | It can contain only two values: *true* or *false*. It stores its value in a single bit but is padded out to a byte for convenience. | 1 (8) | N/A | N/A | Boolean |

### Objects

| Term | Definition |
|------|------------|
|String| A series of characters (text) surrounded by double quotes "like this."|
|Scanner| A library which is used to parse (or scan) its input such as the System.in stream|

### Terms
| Term | Definition |
|------|------------|
|Floating point number | A number which in decimal has a decimal point, marking a fraction value|