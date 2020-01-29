# How Objects Behave 

## Table of Content 
---
- Introduction
- Methods use Object State
- Method Arguments and Return Types
- Pass-by-Value
- Getters and Setters
- Encapsulation
- Using References in an Array

## Introduction:
---
- __State affects behavior, behavior affects state__.
- We know that objects have __State__ and __Behavior__, represented by __Instance Variables__ and __Methods__.
- Until now, we haven't looked at how state and behavior are *related*.
    - We already know that each instance of a class (each object of a particular type) can have its own unique values for its instance variables. 
- An objects has behavior that acts on its state. In other words, __methods use instance variable values__.

## Methods use object state:
---
### Remember: A class describes what an object knows and what an object does
- A class is the blueprint for an object.
    - When writing a class, you're describing how the JVM should make an object of that type. 
    - You know that every object of that type can have different instance variable values. 
        #### Can every object of that type have different method behavior?
        - The answer to that question is "sort of".
        - Every instance of a particular class has the same methods, but the methods can behave differently based on the value of the instance variables.

        - In a example of a `class Song` ~ this has to instance variables, `title` and `artist`.
            - The play() method plays a song, but the instance you can play() on will play the song represented by the value of the *title* instance variable for that instance. 
            - So, if you call the play() method on one instance you'll hear the song "Politik", while another instance plays "Darkstar".

        - The method code is the same. 
```java
class Dog {
    int size;
    String name;

    void bark() {
        if (size > 60) {
            System.out.println("Wooof! Wooof!");
        } else if (size > 14) {
            System.out.println("Ruff! Ruff!");
        } else {
            System.out.println("Yip! Yip!");
        }
    }
}

class DogTestDrive {
    // test the class and method
    public static void main (String[] args) {
        Dog one = new Dog();
        one.size = 70;
        Dog two = new Dog();
        two.size = 8;
        Dog three = new Dog();
        three.size = 35;

        one.bark();
        two.bark();
        three.bark();
    }
}
```
- The output:
>- Wooof! Wooof!
>- Yip! Yip!
>- Ruff! Ruff!

## Method Arguments and Return Types:
---
### Methods Arguments:
- You can pass values into your methods.
    - For example, you might want to tell a Dog object how many times to dark by calling ~
        ```java
        Dog d = new Dog();
        d.bark(3) // the "3" is the argument not a parameter;
        ```
- The value you passed into bark() method are called __arugments__ or __parameters__. 
   -  *A method uses parameters. A caller passes arguments.*
        - __Arguments__ are the things you pass into the methods. 

        - __Parameter__ is nothing more than a local variable .
            - A variable with a type and a name, that can be used inside the body or the method.
    
    - **Important**:
        -  __If a method takes a parameter, you MUST pass it something.__ This something must be of the appropiate type also.
```java
void bark(int numOfBarks) { // "numOfBarks" is the parameter
    while (numOfBarks > 0) {
        System.out.println("ruff");
        numOfBarks = numOfBarks - 1;
    }
}
```
### Return Types:
- Methods can return values.
    - Every method is declared with a return type, but until now we've made all of our methods with a `void` return type.
        - This means they do not give anything back.
        ```java
        void go() {
            // this returns nothing back.
        }
        ```
    - We can declare a method to give a specific type of value back to the caller:
        ```java
        int giveSecret() {
            return 42; 
        }
        ```
        - When you declare a method to return a value, you __must__ return a value of the declared type!
            - Or a value that is __compatible__ with the declared type.
- You can send more than one thing to a method:
    - Methods can have multiple parameters. When declaring arguments, you separate them with commas. When passing the arguments, you must seprate them with commas. 
    - **Important**:
        If a method has parameters, you must pass arguments of the right type and right order. 
    
- Example of calling two parameter method and sending it two arguments:

```java
void go() {
    TestStuff t = new TestStuff();
    t.takeTwo(12, 34); // the aruments you land in the same order you passed them.
}

void takeTwo(int x, int y) { // 12 lands in the int x parameter 34 land in the int y parameter
    int z = x + y;
    System.out.println("Total is " + z);
}
```

- Example of passed variables into a a method: 
```java
void go() {
    int foo = 7;
    int bar = 3;

    t.takeTwo(foo, bar);
}

void takeTwo(int x, int y) {
    int z = x + y;
    System.out.println("Total is " + z);
}
```

## Pass-by-Value:
---
### Java is pass-by-value, this means pass-by-COPY
1. Declare an int variable and assign it the value `7`. The bit pattern for `7` goes into the variable name `x`.
 ```java
    int x = 7;
```
2. Declare a method with an int parameter named z.
```java
void go(int z){ }
``` 
3. call the go() method, passing the variable x as the argument. the bits in x are copied, and the copy lands in z.
```java
foo.go(x);

void go(int z){

}
```
4. Change the value of z inside the method. The value of x doesn't change! The argument passed to the z parameter was only a copy of x.
```java
void go(int z){
    z = 0;
}
```
The method can't change the bits that were in the calling variables x.
## Getters and Setters:
---
- Getters and Setters are also known as *Accessors* and *Mutators*.
- Getters and Setters let you, *get and set things*. 
    - A Getter's sole purpose in life is to send back, as a return value, the value of whatever it is that particular Getter is supposed to get Getting. 
    - A Setter lives and breathes for the chance to take an argument value and use it to *set* the value of an instance variable.
```java
class ElectricGuitar {
    String brand;
    int numOfPickups;
    boolean rockStarUsesIt;

    String getBrand() {
        return brand;
    }

    void setBrand(String aBrand) {
        brand = aBrand;
    }

    int getNumOfPickups() {
        return numOfPickups;
    }

    void setNumOfPickups(int num) {
        numOfPickups = num;
    }

    boolean getRockStarUsesIt() {
        return rockStarUsesIt;
    }

    void setRockStarUsesIt(boolean yesOrNo) {
        rockStarUsesIt = yesOrNo;
    }
}
``` 

## Encapsulation: 
---
- __Encapsulation__ is a mechanism of wrapping the data ( variables ) and code acting on the data (methods) together as a single unit. 
    - In encapsulation, the variables of a class will be hidden from other classes, and can be access only through the methods of their current class.

        - This is also know as data hiding.

    - When wanting to acheive encapsulation...
        >- Declare the variable of a class as private.

        >- Provide public Getters and Setters methods to modify and view the variables value.
- You may have already experienced that vaguely unsettling feeling that comes with leaving your instance variables exposed.
    - __Exposed__ means reachable with the dot operator.

    ```java
    theCat.height = 27;
    ```
- Think about this idea of using our remote contol to make a direct change to the Cat object's size instance variables. In the hands of the wrong person, a reference variable (remote control) is quite a dangerous weapon.
```java
theCat.height = 0; // this is no good.
```
- This would be a Bad Thing. We need to build Setters methods for all the instance variables, and find a way to force other code to call the setters rather than access the data directly.
```java
public void setHeight(int ht) { 
    if (ht > 9 ) { // We put in checks to guarantee a minimum cat height.
        height = ht;
    }
}
```
### Hide the Data:
- It is simple to go from an implementation that's just begging for bad data to one that protects your data and protects your right to modify your implementation later. __But how do you hide the data?__ 
    - With __public__ and __private__ access modifiers. You're familiar with __public__- we use it with every main method. 
    - An encapsulation *starter* rule of thumb: 
        1. Mark instance variables __private__.
        2. mark getters and setters __public__. 
```java
class GoodDog {
    private int size; // make the instance variable private

    public int getSize() { 
        return size;
    }
    // make getters and setters public

    public void setSize(int s) {
        size = s;
    }
}
```

## Using References in an Array:
---
### How do objects in an array behave?
- Just like any other object. The Only difference is how you *get* to them. In other words, how you get the remote control. Let's try calling methods on Dog objects in an array. 
    1. Declare and create a Dog array to hold 7 Dog reference.
        ``` java 
        Dog [] = pets;
        pets = new Dog[7];
        ```
    2. create two new dong objects and assign them to the first two array elements.
        ```java
        pets[0] = new Dog();
        pets[1] = new Dog();
        ```
    3. Call methods on the two Dog objects.
        ```java
        pets[0].setSize(30);
        int x = pets[0].getSize();
        pets[1].setSize(8);
        ```