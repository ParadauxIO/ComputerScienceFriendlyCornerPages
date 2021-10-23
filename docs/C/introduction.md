## Introduction to C

#### A Brief history
Created by Dennis Ritchie at AT&T Labs in 1972.
Original Unix implemented in assembly, but portable.
It had 27 keywords originally and was simple to write.
It is easy to write a compiler for it.

## Hello World

Writing a programme like this requires an inclusion of ``stdio.h``, a header file. A header file is a collection of functions that have been declared and/or defined.
In our case these functions are written by the developers of C and are ready for use. 
Std stands for standard and io stands for **I**nput **O**utput. What stdio.h does is give us functions that are related to input and output streams like printf()
it is a printing (output)function. and scanf() is an scanning (input) function. We also need to include a main, where we run all the functions we have implemented in. 
In C the main is an integer which requires us to return a number, 1, 0, -1.
0 means the programme succesfully exit, and what we'll be seeing in Systems programming. The others refer to a possible error that occured which prevented successful termination

```c
#include <stdio.h>

// print a simple message 
int main() {
	printf("Hello world!\n");
	return 0;
}
```

As you may know, *//* is for comments, the main in our case can take in parameters however it did not. In C we can take in the number of arguments supplied and arguments.

```c
int main(int ** argv, int argc) {
}
```

Here is an example of that. Also notice the two asterix refered to as *stars* in C. These are called pointers and they have many uses. For the moment understand argv are the 
arguments given to the programme.

## Compliation

In C, we need to compile and link files. Here are the methods of compiling we will need 

- Compile the program to object code
```c
clang -c hello.c // you can also use gcc -c hello.c
```

clang is a compiler that produces better warnings and faster compilation however gcc is widely used and works well.

- Link the object code to executable file
```c
clang hello.o -o hello // gcc hello.o -o hello
```

- You can do compile and link at the same time by running
```c
clang hello.c -o hello // gcc hello.c -o hello
```

- To run a program in unix
```c
./hello
```

## Example of C code

```c
// This programme calculates the area of a square
#include <stdio.h>

double area_of_square(double length); // this is a function, it is declared in the main file and not in a header, we must declare it before using it in C.

int main() {
	int length;

	printf("Enter the length of one side of your square: ");
	scanf("%d", &length); // In C, when receiving input we point to the address of the variable, hence the &. The %d is how we output/input integer variables.

	int area = area_of_square(length);

	printf("\nThe area of your square is = %d\n", area); // we are not receiving input hence the lack of &
	return 0;
}
double area_of_square(double length) { // this function was declared before running it, it needs to be defined now
	return length * length; 
}
```

A couple of notes, in C in order to print anything we must give it *%* followed by the letter corresponding to the type of variable. 
For the moment *%d* are for integers and *%f* for floats (doubles). One more thing to note *\n* makes the console create a new line

If you were to run this program and input 5 you would get an output like this
```
Enter the length of one side of your square: 5 
The area of your square is = 25

```
