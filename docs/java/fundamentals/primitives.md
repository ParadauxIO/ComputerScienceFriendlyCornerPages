# Primitives

<hr>
Java comes with 8 basic, fundamental types. 
These are referred to primitives. They are stored directly in the stack. Primitives are the only types which do not inherit from Object. They pertain to raw values and as such do not have helper methods like toString() -- for that you will have to use their boxed (object) equivalents -- Primitives use far less memory than their boxed counterparts and cannot be `null` (We're not considering `\u0000` `null` for the sake of this article.) 

Before we jump into some of the concepts surrounding primitives; take a look at this table which provides a short definition for each primitive type, their maximum and minimum values, how much memory they consume and their boxed equivalent. 

| Term    | Definition                                                   | Size (Bits) | Minimum            | Maximum                              | Boxed Object Equivalent |
| ------- | ------------------------------------------------------------ | ----------- | ------------------ | ------------------------------------ | ----------------------- |
| byte    | Similar to int but only takes up 8 bits of memory.           | 8           | -2<sup>7</sup>     | 2<sup>7</sup>-1                      | Byte                    |
| short   | Used to represent floating-point numbers, with a greater range than the float type | 16          | -2<sup>15</sup>    | 2<sup>15</sup>-1                     | Short                   |
| int     | A simple 32-bit two's complement integer,                    | 32          | -2<sup>31</sup>    | 2<sup>31</sup>-1                     | Integer                 |
| long    | int with a greater range.                                    | 64          | -2<sup>63</sup>    | 2<sup>63</sup>-1                     | Long                    |
| float   | Used to store simple fractional numbers with single-precision meaning after 6 digits it begins to loose accuracy. See BigDecimal for dealing with large precise decimal figures. | 32          | -2<sup>-149</sup>  | (2-2<sup>-23</sup>).2<sup>127        | Float                   |
| double  | Used to store less simple fractional numbers with double-precision. | 64          | -2<sup>-1074</sup> | (2-2<sup>-52</sup>).2<sup>1023</sup> | Double                  |
| char    | 16-bit integer representing Unicode/ascii characters from `\u0000` to `\uffff` | 16          | 0                  | 2<sup>16</sup>-1                     | Char                    |
| boolean | It can contain only two values: *true* or *false*. It stores its value in a single bit but is padded out to a byte for convenience. | 1 (8)       | N/A                | N/A                                  | Boolean                 |

## Boxing

When we discuss the term boxing (or auto-boxing) we're referring to the Java Object Wrappers for each of the primitive types (Byte, Short, Integer, Long, Float, Double, Char and Boolean.) These are used in many situations, specifically with generics. You cannot have a `List<int>` for example; it must be a `List<Integer>` the reason for why will be covered in the eventual Generics article. 

The boxed objects consume more memory than their primitive counterparts as they also include various member data and methods as such, it's often advised to convert to the boxed objects only when necessary and to convert back to the primitive as soon as possible. 

Boxing is very simple. You can convert from an int to an Integer for example by simply letting it equal, no need for casting.

```java
int userAge = 18;
Integer userAge = userAge;
Integer userAgeFromLiteral = 18; // Using an Integer Literal.
```

From the above example, you can see we can create an instance of `Integer` from an `int` or from an `int` literal. The above applies for each of the above objects. 

## Overflowing / Underflowing

What happens should we accidentally try to store 2<sup>32</sup> in an int? I implore you to open your IDE of choice and try it now! (The answer might surprise you!)

```java
int someLargeNumber = Integer.MAX_VALUE + 1; // Induce an overflow.
System.out.println(someLargeNumber);
```

You will find that the value roles around to become the minimum value, and if you go beyond the minimum value it will wrap around to the maximum value (this is referred to **underflowing**) This behaviour only applies to the integer-like primitives, such as byte, short, long, etc.

```java
int someSmallNumber = Integer.MIN_VALUE - 1; // Induce an underflow.
System.out.println(someSmallNumber);
```

Floating point numbers (float, double) have slightly differently; If you overflow them they will return `Infinity`

```java
double riansBankBalance = Double.MAX_VALUE + Double.MAX_VALUE; // Induce an overflow.
System.out.println(riansBankBalance); // Infinity
```

And another "unexpected" outcome arises when you underflow a floating point number, in that they will render down to simply 0.0 (however it will continue counting after this point.)

```java
double riansBankBalance = Double.MIN_VALUE - 1;
System.out.println(riansBankBalance);
```

This does, however, give a more realistic depiction of my bank balance at any given time.

```java
double riansBankBalance = Double.MIN_VALUE - 0.1;
System.out.println(riansBankBalance);
```

## Min/Max_Value

You probably noticed my usage of Integer.MIN_VALUE and Integer.MAX_VALUE, these are constants available within the wrapper classes themselves which make it easy to reference the maximum value possible. 

