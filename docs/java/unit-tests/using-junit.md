# Using JUnit5 

JUnit5 is a utility for unit testing code. Unit testing is the process of testing indivual portions of code to ensure they do as they're intended. It's an incredibly important process, and prevents faulty code from being pushed into production. 

# IntelliJ IDEA
This guide assumes you're using the latest version of IntelliJ IDEA (20202..4 at the time of writing)

Write your program with some methods you wish to test. I will be using an example project for this.

![1](https://cdn.paradaux.io/img/bupri.png)

Here's the class we're going to be testing 
```java
public class SomeClass {
    
    public static int addNumbers(int a, int b) {
        return a+b;
    }

    public static double addNumbers(double a, double b) {
        return a+b;
    }

    public static int multiplyNumbers(int a, int b) {
        return a*b;
    }

    public static double multiplyNumbers(double a, double b) {
        return a*b;
    }

}
```

Once you have created the class in IntelliJ click the center of the class name and press alt + enter, a context menu will appear as such:

![2](https://cdn.paradaux.io/img/ldf5r.png)

Click "create test" and you will get a popup as such:

![3](https://cdn.paradaux.io/img/7n72m.png)

Press OK

You will now receive a configuration dialogue, keep the values at their defaults. 

![4](https://cdn.paradaux.io/img/9o5sp.png)

You can use the tick boxes on the bottom left to automatically generate empty test methods for each method in the class we're greating the tests for, but we're not going to do that for the purposes of this tutorial. 

![4](https://cdn.paradaux.io/img/zw0bj.png)

## Writing your first test.

Now that you have your class you are going to want to make some test methods. We define a test method by placing @Test before the method declaration (function header) This is referred to as an [annotation](https://docs.oracle.com/javase/tutorial/java/annotations/). 

In this case we have two sets of methods with the same name but with different parameters, so we're going to create two different tests for each type. Usually a test method is named after the method with the suffix 'Test' appended onto the end. In this case we're also including the parameter types to distinguish the two test methods. 

```java
import static org.junit.jupiter.api.Assertions.*;

class SomeClassTest {
	
	@Test
	public void addNumbersIntTest() {}   
	
		@Test
	public void addNumbersDoubleTest() {} 
	
		@Test
	public void multiplyNumbersIntTest() {}   
	
		@Test
	public void multiplyNumbersDoubleTest() {} 
	
}
```

## Erorrs 

You will see some errors when you write some of the JUnit 5 keywords, this is fine! hover over @Test until a context menu appears,  then press alt+enter to make the more options dialogue appear, or click it with your mouse as so

![5](https://cdn.paradaux.io/img/4hiuo.png)

Select the "Add JUnit 5.4 to classpath option" 

![6](https://cdn.paradaux.io/img/2ivdh.png)

Another dialogue box may appear, just click OK. This is just asking you where you would like to download JUnit 5 from.

![7](https://cdn.paradaux.io/img/jvrnr.png) 

Doing all this will make JUnit 5 available for you inside this project. 

## Assertions

A large part of unit testing is marking assertions, which is the process of stating a fact, confidently. Essentially we're going to tell the test that this is our expected output given the input, if that ISN'T the case then fail the test, because clearly the method we're testing isn't behaving as it's supposed to. 

There are many types of assertions however the most useful to us right now are assertEquals assertTrue and assertFalse. These are methods accessible by calling 
```java
Assertions.assertEquals(Object a, Object b);
Assertions.assertTrue(boolean expression);
Assertions.assertFalse(boolean expression);
```

You use the Assertions class much in the same was as you do the Math class when you wish to cite Math functions, it's referred to as a utility class as it contains a set of static methods for you to use. 

## Populating our test methods

Now we need to make some statements within our tests to make sure they run successfully. The term "pass" for a unit test simply means no exceptions were thrown, so we don't handle exceptions in a test (unless we're testing to make sure an exception is thrown -- but that's outside the scope of this tutorial) 

So we need to make some statements we know are true, statements we need to `assert`

Because these methods are simple we can easily create example cases to test our methods. The way assertEquals works is it compares the first parameter (which will call our method) and compares it to the second parameter, very similar to .equals() we've been using to compare Strings. 

## addNumbersTest() 

We have two addNumbers tests. for the purposes of demontation I'm going to use System.out.println() to print to the console, however in industry this is considered bad practice, and should use a logger instead. 

```java
    @Test
    public void addNumbersIntTest() {
        // Positive Integers
		Assertions.assertEquals(SomeClass.addNumbers(4, 5), 9);
		Assertions.assertEquals(SomeClass.addNumbers(1, 1), 2);

		
		// Positive and Negative Integers
		Assertions.assertEquals(SomeClass.addNumbers(-4, 4), 0);
		Assertions.assertEquals(SomeClass.addNumbers(-10, 5), -5);
		
		// Negative Integers
		Assertions.assertEquals(SomeClass.addNumbers(-4, -5), -9);
		Assertions.assertEquals(SomeClass.addNumbers(-1, -1), -2);
		
    }
```

Here we're running three test cases, one with all positive numbers, one with both positive and negative numbers and a final one with just negative numbers. It's a good idea to run each test care twice, with two sets of parameters, just to make doubly sure. 

I'm going to leave the other methods to test for you, some example test cases for the double methods would be 
- Whole number parameters
- Whole and real parameters
- Real parameters
- Negative number parameters
- Negative real parameters

## Running our tests.
IntelliJ has fantastic in-house support for JUnit to run our test we just have to click the little play icon next to our individual tests to run them, or the play button next to the class definiton to run all of the tests

![8](https://cdn.paradaux.io/img/f18tk.png)

IntelliJ will take a minute to compile your tests, then run them. You'll see a run dialogue open at the bottom of your screen which should say "1 test passed" provided everything went swimmingly. 

![9](https://cdn.paradaux.io/img/jl6zd.png) 

If you printed out anything to the console during this tme it will come up there in the run dialogue, or if your program output anything to the console. 

## Now you're a JUnit 5 Wizard !

You now know the basics of using JUnit 5. Try running one of our pre-prepared Unit Tests such as [PerniciousNumbersTest](/java/unit-tests/PerniciousNumbersTest) against your assignment solutions. We're going to try and have a unit test suite for each upcoming programming assignment, but you should try to write your own too!

## Further Reading Material

https://www.baeldung.com/junit-5

https://www.baeldung.com/junit-5-migration

https://www.baeldung.com/junit5-test-templates

https://www.baeldung.com/parameterized-tests-junit-5

https://blog.jetbrains.com/idea/2020/09/writing-tests-with-junit-5/

## Full Example Class
```java
import org.junit.jupiter.api.Assertions;
import org.junit.jupiter.api.Test;

class SomeClassTest {
    
    @Test
    public void addNumbersTest() {

        // Positive Integers
        Assertions.assertEquals(SomeClass.addNumbers(4, 5), 9);
        Assertions.assertEquals(SomeClass.addNumbers(1, 1), 2);


        // Positive and Negative Integers
        Assertions.assertEquals(SomeClass.addNumbers(-4, 4), 0);
        Assertions.assertEquals(SomeClass.addNumbers(-10, 5), -5);

        // Negative Integers
        Assertions.assertEquals(SomeClass.addNumbers(-4, -5), -9);
        Assertions.assertEquals(SomeClass.addNumbers(-1, -1), -2);

    }

}
```


