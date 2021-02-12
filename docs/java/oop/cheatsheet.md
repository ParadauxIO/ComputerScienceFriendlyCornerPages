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

// TODO: Inheritence implementation of classes. 

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







 