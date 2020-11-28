## Using Methods in Java

In simple terms; a method in java is a block of code which only executes when it is called upon to do so. You can pass an input to this block of code, referred to as its parameters. 

Methods are used to perform particular actions over and over again, so you're not duplicating code. Methods are known as functions in other languages. 

You have come across one method already, the "main" method. 

## The Main Method
The main() method is called the entry point of the programme. When you run your programme what you're doing is calling the main method. If you provide command-line arguments they will be passed (space-seperated) as the String[] referred to as args. 

```java
public static void main() {
	System.out.println("Hello, World!");
}
```

I'm sure you've come across the above code before, it's the "Hello, World!" application in Java. What we're going to do is break down each aspect of the method declaration here. 

## Access Modifiers [public]
Public here is the access modifier. An access modifier controls who can see and use the method. There are three access modifiers in Java.
- public
Accessible by any class which imports it. 
- private
Only accessible by the class itself (used for internal methods)
- protected
Only accessible by classes in the same package. We'll come to packages at a later date, but you can think of them like a folder of classes, so it'll only allow classes in the same folder to call the method.

Access modifiers are an important part of the OOP Concept referred to as Encapsulation which is the process of wrapping data and methods acting on the data as a single unit, which cannot be touched by the outside world. 

# Static [if not present, leave blank]

You can take this for granted for the moment, however I will try to go over it in brief on another page. 

In essence, the static keyword is used for memory-management. It is used to share the same value, or the same method given any instance of a class. 

It is quite hard to understand without first being introduced to the idea of object oriented programming. 

## Return types [void]

In the main method, we declare the return type to be void. Void here refers to nothing; a void. It doesn't return any value. This is useful in the case of the main method, as there is nothing that could receive output from the main method, as it represents the programme itself.  Most functions you will be writing for now, outside of the main method, will not be void. 

The return type is denoted by the object type of what you look to return. You return data to the programme by using the return keyword. 

```java
public static void main(String[] args) {
	System.out.println(helloWorld());
}

public String helloWorld() {
	return "Hello, World";
}
```

The function call can act as a pseudo-variable, as if whatever the return value is, is a variable. In this case we are printing out to the console whatever the method helloWorld returns.

# Method name [main()]
In order to declare the method itself we have to give it a name. This name is what we're going to type when we want to call upon the function execute. We name methods in lowerCamelCase whereby the first word has its first letter lowercase and every subsequent word be in ProperCase. Method names should be named after a verb and methods returning a boolean (a true or false value) should be named prefixed as `is`
for example
```java
private boolean isAvailable() {
	return true;
}
```

# Method body [ {} ]
A method has to have a body, some substence to itself. This is where the main body comes in. 

In the case of our first example, we have `System.out.println()` inside the body of our method. 

## A simple project example

Take the following program which calculates the interest payable by the formula F = P(1 + i)^t

```java
import java.util.Scanner;

public class CompoundInterest {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Please enter the principal amount: ");
        int principalAmount = scanner.nextInt();

        System.out.print("Please enter the interest rate as a decimal (i.e 0.04): ");
        double interestRate = scanner.nextDouble();

        System.out.print("Please enter the term, in years: ");
        int termLength = scanner.nextInt();

        double compoundInterest = calculateCompoundInterest(principalAmount, interestRate,
                termLength);

        System.out.println(getFormattedOutputString(compoundInterest));
    }

    public static double calculateCompoundInterest(int principal, double interest, int term) {
        return principal * Math.pow((1 + interest), term);
    }

    public static String getFormattedOutputString(double compoundInterest) {
        return String.format("You will have %.2f by the end of the term.", compoundInterest);
    }
}
```

If you were to run this program and supplied 10,000; 0.04 and 30 as the inputs you would receive the following output

```
Please enter the principal amount: 10000
Please enter the interest rate as a decimal (i.e 0.04): 0.04
Please enter the term, in years: 30
You will have 32433.98 by the end of the term.
```