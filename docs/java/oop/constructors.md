# Java Constructors

>   This article is a written accompaniment to a video which is available on YouTube [here](https://youtu.be/jVGTWXbGpVI).

>   This article does not make use of **encapsulation**. Please be aware that referencing fields as I have done in the video is considered **bad practice**, and I did it for the sake of not having so much code as to not fit on the screen.

**Constructors** provide **state** to our **objects**, in that they set the values of the fields (like variables) contained within them, which we define at the **beginning** of our **class**.

In the video I make use of this base object 

```java
public class BankAccount {
    
    String name;
    LocalDateTime timeOpened;
    double balance;
    double overdraftAllowance;
    
}
```

However, this object alone isn't much use to a developer, we need to be able to set the values of those fields so that they actually contain data! There is two ways to do this, via **setters** or via **constructors**. 

In this article I'm talking solely about the latter. 

In essence, a constructor is a special kind of method which initialises all of our fields, via its parameters or through default values contained within. We define a constructor by using an access modifier, then the class name, a pair of parentheses and then a code block, like so:

## Empty Constructor

```java
public BankAccount() {
    
}
```

This is referred to as an no-argument, unparameterized, default or simply empty constructor -- whatever you like to call it, frankly. The Java Compiler automatically adds this to our code if we do not explicitly set a constructor, and you can see this if you invoke a constructor in a file which doesn't have one. The empty constructor is usually used to set default values for fields, rather than leaving them as **null**/uninitialized.

The second type of constructor is a parameterised constructor, in which we have a list of parameters like a standard method, which we then use to set the values in our object, for example:

## Parameterized Constructors

```java
    public BankAccount(String name, LocalDateTime timeOpened, double balance, double overdraftAllowance) {
        this.name = name;
        this.timeOpened = timeOpened;
        this.balance = balance;
        this.overdraftAllowance = overdraftAllowance;
    }
```

`this` refers to the object we are currently creating, so we're setting the field's values, rather than setting the constructors parameters to themselves, `this` is used to differentiate fields in this way by scope. From the [oracle java specification](https://docs.oracle.com/javase/tutorial/java/javaOO/thiskey.html)

>   Within an instance method or a constructor, `this` is a reference to the *current object* — the object whose method or constructor is being called. You can refer to any member of the current object from within an instance method or a constructor by using `this`.

We don't have to set values to exactly what we pass in as a parameter, for example -- when a Bank Account is created we could add 100€ to whatever the parameter passed is, a "gift" for opening an account at our virtual bank.

```java
    public BankAccount(String name, LocalDateTime timeOpened, double balance, double overdraftAllowance) {
        this.name = name;
        this.timeOpened = timeOpened;
        this.balance = balance + 100d;
        this.overdraftAllowance = overdraftAllowance;
    }
```

And we don't have to have a parameter for each field, we can mix and match, and place them in any order we like -- and we can straight up remove parameters which we don't need -- take timeOpened for example, we could just drop the parameter and let it equal to the current time -- as the time at the object's creation should match the time the account is created. We can do that like so:

```java
    public BankAccount(String name, double balance, double overdraftAllowance) {
        this.name = name;
        this.timeOpened = LocalDateTime.now();
        this.balance = balance + 100d;
        this.overdraftAllowance = overdraftAllowance;
    }
```

If you haven't used LocalDateTime I suggest giving it a quick look over either on the [specification](https://docs.oracle.com/javase/8/docs/api/java/time/LocalDateTime.html) or via the [Java 8 Date/Time tutorial](https://www.baeldung.com/java-8-date-time-intro) on Baeldung. 

We're not limited to one constructor per class either! We can mix and match, and have multiple constructors depending on how we want to create the object in different contexts like so:

```java
public class BankAccount {
    
    String name;
    LocalDateTime timeOpened;
    double balance;
    double overdraftAllowance;
    
    // Default Constructor
    public BankAccount() {
    	this.name = "Joe Bloggs";
        this.timeOpened = LocalDateTime.now();
        this.balance = 100d;
        this.overdraftAllowance = 0d;
	}
    
    // Parameterised Constructor setting some fields, and using defaults for others
    public BankAccount(String name, double balance, double overdraftAllowance) {
        this.name = name;
        this.timeOpened = LocalDateTime.now();
        this.balance = balance + 100d;
        this.overdraftAllowance = overdraftAllowance;
    }
    
    // Paramaeterised Constructors setting each field explicitly
    public BankAccount(String name, LocalDateTime timeOpened, double balance, double overdraftAllowance) {
        this.name = name;
        this.timeOpened = timeOpened;
        this.balance = balance+100d;
        this.overdraftAllowance = overdraftAllowance;
    }
    
}
```

As you can see, the above is very clunky and there is a lot of duplicated code, and I'm sure you're aware by now that object oriented programming is all about modularity and not repeating yourself, and that applies here as well. This is why we can call one constructor from another, so that we only truly need one fully defined constructor, then others which may define differences, taking our example from above: 

## Constructor Chaining

```java
public class BankAccount {
    
    String name;
    LocalDateTime timeOpened;
    double balance;
    double overdraftAllowance;
    
    // Default Constructor
    public BankAccount() {
        this("Joe Bloggs", 100d, 0d);
	}
    
    // Parameterised Constructor setting some fields, and using defaults for others
    public BankAccount(String name, double balance, double overdraftAllowance) {
        this(name, LocalDateTime.now(), balance, overdraftAllowance);
    }
    
    // Paramaeterised Constructors setting each field explicitly
    public BankAccount(String name, LocalDateTime timeOpened, double balance, double overdraftAllowance) {
        this.name = name;
        this.timeOpened = timeOpened;
        this.balance = balance+100d;
        this.overdraftAllowance = overdraftAllowance;
    }
    
}
```

It's a lot smaller, right? And now if we decide to change our general gift of €100 or wish to change something else about our constructor we don't have to change every single one, only the primary. You can, hopefully, see that I am calling the other constructors using the `this` keyword we talked about earlier, so this refers to *this* object's constructor, which accepts the specific parameters we provide, very similar to method overloading, if you're familiar. 

If, for whatever reason, we need to create a copy of an object which is modified in some pre-defined way we can use a special type of **parameterized constructor** which accepts an existing instance of the particular object in question and then modifies it in some way.

In the video I use the example of renewing defunct/dormant account by passing the defunct instance through a copy constructor, which re-sets the timeOpened to the current time like so: 

## Copy Constructors

```java
public BankAccount(BankAccount existingInstance) {
    this(existingInstance.name, LocalDateTime.now(), existingInstance.balance, existingInstance.overdraftAllowance);
}
```

These aren't used very often, but it's another perfectly valid example of a Constructor, which is all the rage right now in this article. 











