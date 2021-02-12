# OOP Cheat Sheet

>   This is an incomplete article, and will continue to be extended over time, it also makes great use of code examples, while you may not understand every aspect of the provided code provided, it is there for you to be able to copy and paste into your own IDE (or online IDEs such as codespaces or Repl.it in order to have a play around with it. )

>   **N.B**: This is not a beginners guide, it is a loosely written tutorial which is aimed to be more of a reference guide, than a step-by-step process for learning object oriented programming.

>   Author: [Rían](https://github.com/ParadauxIO) 11/02/2020

## What is object-oriented programming

Objected oriented programming is a programming paradigm which relies on the existence of `classes` and `objects` 

## The "Anatomy" of an object

-   Class
-   Fields
-   Static Initialisor Blocks
-   Constructors
-   Methods
    -   Accessors (Getters/Setters)
    -   Mutators 

Objects contain data in the form of `fields` or object-scoped variables and methods with modify or `mutate` that data. For non-primitive types fields default to `null` and if an `access modifier` it defaults to `package-private`

## Classes

Classes can be thought of like the "blueprint" of an object, they represent every possible object -- in an abstract form, there is no data contained inside. It's like a blank form, waiting for someone to fill in the blanks, by `initialising` values. 

Classes can be represented as a `UML Class Diagram` outlined below which is a shorthand notation for referring to the implemented `attributes`, `methods` and relationships with other objects. Take the below (rather simplistic) example below:

| Class: Lightbulb                          |
| ----------------------------------------- |
| - poweredOn : boolean                     |
| +powerOn() : void<br />+powerOff() : void |

This sets out the existence of this `Lightbulb` class which has the following fields: `poweredOn` and implements the following methods: `poweredOn(), poweredOff()` Such a Lightbulb could be implemented as below:

```java
// Class Declaration
public class Lightbulb {
    // Fields
    private boolean poweredOn;
    
    // Constructor
    public Lightbulb() {
        this.poweredOn = false;
    }
    
    // Methods
    public void powerOn() {
        this.poweredOn = true;
    }
    
    public void powerOff() {
        this.poweredOn = false;
    }
    
}
```

### Benefits of using a class structure

The concept of classes allows us to create complex, modular and understandable applications in Java, making them the building blocks of all of object-oriented programming, in any OOP programming language.

## Objects

Objects are simply the incarnations of classes, with some form of `data`.  This data can be provided in one of three ways, `static initialisor blocks` (coved later) `constructors` and `setters`. 

But first we have to create an `instance` or copy of the class, which we can then imprint with our data. To do this we use the `new` keyword. 

```java
// The Main Method -- The Entry Point to your application
public static void main(String[] args) {
    Lightbulb bulb = new Lightbulb();
}
```

We defined our constructor above to take no parameters so we simply use empty parentheses `()` but now we have a Lightbulb with its `poweredOn` field (or state) set to `false` what if we want to power it on ? Well that's as simple as `invoking` the `powerOn()` method defined in our UML Diagram, on our particular `instance` of our class (which we named `bulb`) 

```java
// The Main Method -- The Entry Point to your application
public static void main(String[] args) {
    Lightbulb bulb = new Lightbulb();
    
    // Turn on our bulb
    bulb.powerOn();
}
```

Now we have a bulb, and we have it powered on, what else can we do with it? You may ask. In our case our lightbulb is much too simplistic to provide any more depth, maybe we could implement a method to get the poweredOn state of our bulb? Which we could do by implementing the below method into our Lightbulb class: 

```java
public boolean isPoweredOn() {
    return this.poweredOn;
}
```

This is referred to as a `getter` is *gets* information from our class for us, as object-oriented programmers we must never interact with fields directly, to do so would break `ensapsulation` a key object-oriented principal aiming to prevent unauthorised, and unprotected access to our internal workings of our objects. 

Usually getters begin with the word get, take the example our example of the Coffee Machine Class below, for example.

```java
public class CoffeeMachine {
    
    // Number of beans present in the machine
    private double beanAmount;
    
    // The amount of water (in millileters) in the machine
    private double waterAmount;
    
    // The powered on state taken from Lightbulb
    private boolean poweredOn;
    
    public CoffeeMachine() {
        this.beanAmount = 0;
        this.waterAmount = 0d;
        this.poweredOn = false;
    }
    
    public double getBeanAmount() {
        return this.beanAmount;
    }
    
    public double getWaterAmount() {
        return this.waterAmount;
    }
    
    public boolean isPoweredOn() {
        return this.poweredOn;
    }
   
}
```

This class will be extended and extended to become more complex over the course of this cheatsheet, but for now all we care about is the `getter ` methods. We use these to access the state of the class, without directly interacting with the fields themselves, thus ensuring `encapsulation`, which I have alluded to earlier.  

Notice how the methods which return doubles are prefixed with `get` where as the method which returns a boolean is prefixed with `is ` this is due to the convention in how variables are named, with booleans expected to be named after a boolean state, and thus the `is` prefix should be a method which returns "Yes" or "No", or in our case `true` and `false`

[More coming soon]

### Declaration, Instantiation and  Initialisation 

#### Declaration

Declaring the scope of the object, the value for objects defaults to `null`

```java
CoffeeMachine coffeeMachine; // Declare the existence of our object, sets the scope and sets the value to null.
```

### Instantiation

Creating an `instance` of the class, with the state as set in the default constructor (which is empty if not specified.) 

```java
coffeeMachine = new CoffeeMachine(); // Call the default (empty) constructor.
```

### Initialisation

Giving values to the fields inside of your class, via `setters` or via a more complex, `parameterised` constructor

```java
coffeeMachine.setFuelAmount(450);
coffeeMachine.setBeanAmount(175);

// or if an appopriate constructor is defined
coffeeMachine = new CoffeeMachine(450, 175); // Instantiation and Initialisation in one step. 
```



## Encapsulation

Encapsulaiton is the process of hiding the inner workings of a class to external observers, through the use of `access modifiers` and `methods` such as the `getters` and `setters` outlined earlier in the guide. 

### Access Modifiers

-   `private`

    Members can not be accessed directly from outside the class, keeping it hidden from other classes, as well as its subclasses. This is the most useful, as it prevents outside forces from manipulating our objects directly. 

-   `public` 

    This allows members to be directly accessed by anything within the same scope as the object. 

-   `protected`

    Protected lies in between `private` and `public` and its primary usecase is within the context of `inheritence` where we have classes extending from eachother, and creating classes out of other classes, `polymorphism`. Protected members can be accessed within the same package, however outside the package they can still be accessed through an inherited class. 

-   `default` (package-private -- no access modifier specifed.)

    If you don't give a field or method an access modifier, it is considered to be `default` access, which is similar in practice to `protected` without the ability to access via a subclass.

### Fields

I have thrown around the term `field` pretty liberally before really explaining what they are, but they are the `members` of the class, or the variables which differenciate different `instances` of the class. For example, within a class labelled `Dog` we might have the following `fields` to differenciate different types of dog: 

-   -age : int
-   -breed : String
-   -name : String
-   -owner : String
-   -birthday : Date

These are unique to each `instance` of the class, and are what we are trying to protect through `encapsulation`.

### Static Fields

Fields which are denoted as `static` are not specified to any one instance of a class, they are common to all. `static` is usally reserved for constants, which are denoted as `static final` variables, in that they are static (do not change across instances) and final (the value will never change from its initial value) 

Static fields can be assigned values using a special block of code referred to as a `static initialiser` It is called implicitly (automatically) by referencing a static member within the class, or at the creation of the first instance of that class. 

```java
public class SomeClass {
    
    private static int z;
    
    // Static initialiser block
    static {
        z = 15;
    }
}
```

The above static initialiser block simply sets the value of `z` to be fifteen, but we can run any abitrary code within the static initialisor block. The only issue with this, is that it only has a scope which allows it to access other static fields, and can not be provided any inputs from the constructor or anything of that sort, by virtue of being `static`. They are great for creating relationships between various static fields which rely on eachother, but don't need to be each be manually updated by a human. 





