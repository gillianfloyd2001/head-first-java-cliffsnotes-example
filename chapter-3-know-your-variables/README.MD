# Know your Variables

## Table of Contents
- Declaring a Variable
- Primitive Types
- Java Keywords
- Reference Variables
- Objects declaration and assignment
- Array 

## Declaring a Variable 
When dealing with Java, Java cares about type. Java will not let you put a reference that does not make sense to go into a certain variable name, an example of this is that java will not let you put a floating point number into an interger variable, unless you let the compiler know that you know you that you will lose the precise. 

Your compiler can spot most of the problems before it runs.

- What does declaring a Variable look like:
    first off you need to know what type your variable is:
        is it a interger, is it a string, or a single character.
    Variable can be one of two things: Primitive or Object reference.
        Primitive holds fundamental values, this includes intergers, booleans, and floating point numbers.
        Object reference holds the references to objects. 
    Must Follow the declaration rules:
        - Variables must have a type 
        - Variables must have a name so I can use it in code.
    Example of this:

    ```java
      int  count;
    //type //name
    ```

## Primitive Types
When thinking of **primitives**, think of cups that they have at your local coffehouse or a Starbucks. Now Starbucks have three different sizes, which are "tall", "grande", and "venti" - the word size would be the type in this analogy and the actually sizes are the names like in the example right before this section.

- In Java, primitives come in different sizes, and those sizes have names;
    > When declaring a variable in Java you must declare it with is specific type. 
    > There are four interger primitives: 
        >- long
        >- int
        >- short
        >- byte

- Each primitive variable has a fixed number, which means its not a decimal. 
    >The other two numeric primitives in Java: 
        >- float
        >- double
    
These are used for decimal numbers.

## Java Keywords
- Rules to name a class, method or variable: these rules are slightly more flexible
    >- Must start with a letter, underscore, or dollar sign($); do not start a name with a number.

    >- After the first chapter, you can use numbers as well. Just don't start it with a number.

    >- It can be anything you like, subjects to those tow rules, just as long as it isn't one of Java's reserved words.

**Reserved Words** are keywords that the compiler recognizes.
- examples of Keywords: these are some words after the first chapter.
    - public, static, and void

- Primitive types are reserved:
    >- boolean
    >- char
    >- byte
    >- short
    >- int
    >- long
    >- float
    >- double
But there are many more that will be touched on in the book a little later. 

## Reference Variable
- An object reference is just another variable value.

An example of Reference Variable:

``` java
Dog myDog = new Dog();
```
This is creating a new Dog instance based off the old instance. 


## Objects Declaration and Assignment
- There are three step of object declaration, creation, and assignment:
    1. Declare a reference variable
        ```java
        Dog myDog
        //the class | "myDog" is the variable name
        ```
        This tell the Java Virtual Machine (JVM) to allocate space for a reference variable, and names that variable "myDog". The reference variables is of type Dog.

    2. Create an object
        ```java
        new Dog()
        // this is creating a new instance of Dog()
        ```
        This tells the JVM to allocate space for a new Dog object on the heap. 
    
    3. Link the object and the reference 
        ```java
        = // this is just saying that the left side is equal to the right side, which is saying myDog is equal to the new instance of Dog() 
        ```
        Assigns the new Dog to the reference variable myDog. 

## Array
- Arrays are objects too.
    - used for oreded and effcient list of things. Arrays can give you fast random access by letting you use an index position to get to any element in the array. 
    
    - Every element in an array is just a variable. In other words, anything you can assign to a variable can be placed or assign to an array.

    - In an array of type int (int[]) can hold intergers. In a Dog array (Dog[]), this can hold reference variable, not the object itself. 

    **Array are always objects, whether ther're declared to hold promitives or object reference**
    
    - When creating an array you have some steps you can rememeber:
        1. Declare  an int array variable. An array variable is a remote control to an array object.
            ``` java 
            int[] nums;
            ```
        2. create a new int array with a length of 7, and assign it to th eperviously declared int[] variable nums.
            ```java 
            nums = new int[7] // the 7 is how long the array
            ```
        3. Give each element in the array an int value. You have only intergers in this array.
            ``` java 
            nums[0] = 6;
            nums[1] = 19;
            nums[2] = 44;
            nums[3] = 42;
            nums[4] = 10;
            nums[5] = 20;
            nums[6] = 1;
            ```
            This is an array of intergers. When you want to go into the array and get a number out you would need to use an index, but we will learn about that in another chapter.

