# Static

The static keyword is probably one of the most difficult to understand. It requires a basic understanding of Java as an object-oriented programming language. I'm only going to give a superficial overview of the static keyword, as it's above the current level. 

Given a class, Book.java
```java
public class Book {

    // Fields
    String author;
    int pageCount;
    String blurb;

    // Constructor
    public Book(String author, int pageCount, String blurb) {
        this.author = author;
        this.pageCount = pageCount;
        this.blurb = blurb;
    }

    // Getters
    public String getAuthor() {
        return author;
    }

    public int getPageCount() {
        return pageCount;
    }

    public String getBlurb() {
        return blurb;
    }
}
```

A book here is an object. It is a thing which can be represented or quantified by certain information. A Class in Java refers to a blueprint for objects, i.e this shows a template from which we can create books. 

The process of creating an object from a class is called instantiation (the process of creating an instance) 

The `static` keyword marks the difference between instance variables and static (unchanging) variables. 

I can create a book by calling the constructor like so:
```java
Book harryPotter = new Book("JK Rowling", 456, "A book about a boy who finds out he's actually a wizard!");
```

This will create an instance of Book with the data we provide it via the constructor. You don't need to understand this process just yet, just take it for granted! 

The problem is, as far as the `Book` class is concerned, there is no values in author, pageCount and blurb. There are particular to any given instance of that class, as shown above. But we can create a variable which is the same no matter what instance it is. Such variables are called `static` fields and they are declared by placing the word `static` after the access modifier. 

```
static int BookCount = 456;
```

The amount of books is a piece of information that won't change for a particular book, so we can use a static variable so we can access the same variable across instances of that class. 



## Incomplete Notice.

This file is still under construction.