# Week 13

This week's tutorial is primarily testing you on your ability to use `Getters` and `Setters` which are special methods that `Get` and `Set` values within objects respectively. 

An example of a Getter

```java
public int getNumber() {
    return number;
}
```

An example of a Setter 

```java
public void setNumber(int number) {
	this.number = number;
}
```

## Tutorial Question.

## 1. 

Create a Java class called BankCustomer with the following fields:

-   accountNumber (int/long)
-    customerName (String)
-    customerAddress (String)
-   customerDateOfBirth (LocalDate/String/int)

Create a `Getter` and `Setter` for each of these fields. 

Then, in another class using the `main` method, intialise the values for each field using a `Setter` or, alternatively, a `constructor` 

## 2. 

Create a Java class called Swap with the following fields:

-   numberOne (int/long)
-   numberTwo (int/long)

And the following methods

-   `Getters` / `Setters` for both fields
-   `swap` which swaps the values of numberOne and numberTwo without introducing a third variable (local or otherwise.) 

Intialise the values of `Swap` , swap the values -- then print them out to the console. 

# Solution

## Main.java

```java
import java.time.LocalDate;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter two space-separated numbers: ");
        Swap twoNumbers = new Swap(scanner.nextInt(), scanner.nextInt());
        System.out.printf("Number one: %d, Number two: %d%n", twoNumbers.getNumberOne(), twoNumbers.getNumberTwo());
        twoNumbers.swap();
        System.out.printf("Number one: %d, Number two: %d%n", twoNumbers.getNumberOne(), twoNumbers.getNumberTwo());

        BankCustomer bankCustomer = new BankCustomer(573636363L, "Rían Errity", "Main Street, Celbridge", LocalDate.parse("2002-05-13"));
    }
}

```

Example console input/output:

```
$ java Main
Enter two space-separated numbers: 45 78
Number one: 45, Number two: 78
Number one: 78, Number two: 45
```

BankCustomer.java (Including Constructor)

```java
import java.time.LocalDate;

public class BankCustomer {

    private long accountNumber;
    private String customerName;
    private String customerAddress;
    private LocalDate customerDateOfBirth;

    public BankCustomer(long accountNumber, String customerName, String customerAddress, LocalDate customerDateOfBirth) {
        this.accountNumber = accountNumber;
        this.customerName = customerName;
        this.customerAddress = customerAddress;
        this.customerDateOfBirth = customerDateOfBirth;
    }

    public long getAccountNumber() {
        return accountNumber;
    }

    public String getCustomerName() {
        return customerName;
    }

    public String getCustomerAddress() {
        return customerAddress;
    }

    public LocalDate getCustomerDateOfBirth() {
        return customerDateOfBirth;
    }

    public void setAccountNumber(long accountNumber) {
        this.accountNumber = accountNumber;
    }

    public void setCustomerName(String customerName) {
        this.customerName = customerName;
    }

    public void setCustomerAddress(String customerAddress) {
        this.customerAddress = customerAddress;
    }

    public void setCustomerDateOfBirth(LocalDate customerDateOfBirth) {
        this.customerDateOfBirth = customerDateOfBirth;
    }

}

```

## Swap.java (Including Constructor)

```java
public class Swap {

    private int numberOne;
    private int numberTwo;

    public Swap(int numberOne, int numberTwo) {
        this.numberOne = numberOne;
        this.numberTwo = numberTwo;
    }

    public void swap() {
        numberOne += numberTwo;
        numberTwo = numberOne - numberTwo;
        numberOne -= numberTwo;
    }

    public int getNumberOne() {
        return numberOne;
    }

    public int getNumberTwo() {
        return numberTwo;
    }

    public void setNumberOne(int numberOne) {
        this.numberOne = numberOne;
    }

    public void setNumberTwo(int numberTwo) {
        this.numberTwo = numberTwo;
    }
}
```

If you have any questions or find this confusing, please do let me know.



