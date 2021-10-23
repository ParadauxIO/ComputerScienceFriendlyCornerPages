# Basic Types and Formatted I/O

## C Variable Names

- Use:
	- descrpitive variables
	- variables with lowerCamelCase
	- variables without an underscore as their first letter
	- variables that are not keywords 	

	```
	area, square, inputted_number, inputtedNum // good variables
	_under, _squarewithareaof2, NUM            // don't
	int, hello!friend, 2EZ4Me                  // impossible
	```

## C Basic Types

In a 32-bit machine

```
| Type              	 |  Keyword         | Bytes | Range
| ---------------------- | ---------------- | ----- | --------------------------------------------- |
| character		 |   char	    |   1   |   -128->127				    |
| integer		 |   int	    |   4   |   -2,147,483,648->2,147,438,647		    |
| short integer		 |   short     	    |   2   |   -32768->32367				    |
| long integer		 |   long	    |   4   |   -2,147,483,648->2,147,438,647		    |	
| long long integer      |   long long	    |   8   |   -9223372036854775808->9223372036854775807   |	
| unsigned character	 |   unsigned char  |   1   |   0->255					    |
| unsigned integer       |   unsigned int   |   2   |   0->4,294,967,295			    |	
| unsigned short integer |   unsigned short |   2   |   0->65535				    |
| unsigned long integer	 |   unsigned long  |   4   |   0->4,294,967,295			    |
| single-precision	 |   float	    |   4   |   1.2E-38->3.4E38				    |
| double-precision	 |   double	    |   8   |   2.2E-308->1.8E308			    |
```

## Conversion Specifiers
```
| Specifier | Meaning				      |
| --------- | --------------------------------------- |
| %c        | Single character			      |
| %d        | Signed decimal integer		      |
| %x        | Hexadecimal number		      |
| %f        | Decimal floating point number	      |
| %e        | Floating point in "scientific notation" |
| %s        | Character string			      |
| %u        | Unsigned decimal integer		      |
| %%        | print % sign			      |
| %ld, %lld | long, and long long		      |
```

There must be one conversion specifier for each argument being printed or inputted e.g. ``printf("%d %f %c", someInt, someDouble, someChar)``
If you are reading into a **long** or a **double**, you must precede the conversion specifier with an **l** 

```c
int main() {
	int x;
	double y;
	float z;
	long a;
	scanf("%d %f %lf %ld", &x, &y, &z, &a);
	return 0;
}
```

Unfortunately, %ld must be used with printf, but %lf must not

## Escape Characters
```
| Sequence | Meaning					|
| -------- | ------------------------------------------ |
| \a       | Bell (alert)				|
| \b       | Backspace					|
| \n       | Newline					|
| \t       | Horizontal tab				|
| \\       | Backslash					|	
| \'       | Single quote				|
| \"       | Double quotation				|	
| \xhh     | ASCII char specified by hex digits		|
| \ooo     | ASCII char specified by octal digits	|
```

## Type Conversion (Casting)

```c
int a = 10;
double b = 3.141592653, c;
c = (double) a; // a = 10.0
c = (int) b; // c = 3
c = (int) (-b); // c = -3
```

## Type Conversion Implicit

Usually seen with char, here's an example

```c
char someChar = 'A';
int num;
num = someChar; // The ascii code for 'A' will be assignmed into num, in our case num = 41 in hex or 65 in decimal
```

It is also seen when performing arithmetic operations like division 

```c
double x = 10.52, y = 3.53;
int answer;
answer = x / y; // 10.52 / 3.53 = 2
```

## Sizeof

In C, we use the function ``sizeof()`` to return the number of bytes a particular data type has. It is useful if we want to have our code running on multiple computers.
The reason it would run on multiple computers as it would calculate the bytes needed for an int on a 32-bit machine and a 64-bit machine without needing the code to be altered.
This code would result in ``printf("Size of char = %2d byte(s)\n", sizeof(char));`` ``Size of char = 1 byte(s)``

```
| sizeof()       | Result in Bytes |
| -------------- | --------------- |
| char		 | 1 byte(s)       |
| short          | 2 bytes(s)      |
| int            | 4 byte(s)       |
| long           | 4 byte(s)       |
| long long      | 8 byte(s)       |
| unsigned char  | 1 byte(s)       |
| unsigned int   | 4 byte(s)       | 
| unsigned short | 2 byte(s)       |
| unsigned long  | 4 byte(s)       |
| float		 | 4 byte(s)       |
| double	 | 8 byte(s)       |
| long double    | 16 byte(s)      |
```

sizeof() function is important when allocating memory to arrays using ``malloc()`` it stands for memory allocation

``char *oneDArrayWith5Chars = malloc(sizeof(char) * 5);``

We now have an array with 5 characters. 

## typedef

This allows us to use existing types to new or complex syntax

```c
typdef long long length;
``` 

We declared an unsinged int type variable length, we can now use it like so ``length i;`` which is the same as ``long long length i;``

## Constants

In C we have two ways of writing constants

```c
#define SOME_CONSTANT 398.234234

// or 
const double someConst = 398.234234
```

Anything with a # before it is from the preprocessor, or before the code is compiled. What this means is that whenever you use ``SOME_CONSTANT`` what is actually happening is
it gets replaced with the number you gave it. And the CONSTANT is deleted before compilation.
Using const instead of define is a better idea as it allows us to specify the type, i.e. double. It is useful as it can prevent any possible errors from occuring with our programme.
