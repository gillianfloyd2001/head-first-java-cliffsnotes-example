# Classes and Objects

## Table of Contents
- Inheritance
- Overriding methods
- Difference between things objects do and knows
- Difference between class and object
- Making an object
- Two uses of main()


## Inheritance
Inheritance is typically classes inhertiing or passing certain methods down to a subclass from the superclass.

- When inherting from a superclass:
    You need to look at your classes and see if they have anything in common:

    ```java
    class Richard {
        twoDaughter();
    }
    class Aimee {
        twoDaughter();
    }
    ```

    Once you find the similarities, you can break them up into a superclass:

    ```java
    class Parents { // this is the superclass for the classes above it. 
        twoDaughter()
    }
    ```

    Once you create the superclass:

    ```java
    class Aimee extends Parents {
        System.out.println("hello");
    }
    
    class Richard extends Parents {
        System.out.println("World")
    }
    ```
    extends 
    This is just one relationship, that you can link and pull apart to create a subclass and a superclass. The class Richard and the class Aimee inherited from the superclass Parent. 

## Overriding methods
The meaning of Overriding is a subclass redefines one of its inherited methods when it needs to chage or extend that behavior of that method.

```java
    class Parent{
        twoDaughter();
    }

    class Aimee extends Parent {
        twoDaughter() {
            // this is where you tell the method what to override it with. 
        }
    }
```
When overriding, you create new methods within the classes that extends the superclass. This will tell the subclass that has the new method or the override on it, what is needs to do. 

## Differences between things objects do and know
- Things objects can do: 
    These things are called methods:
        It's common to have methods that can read and write these values of the Instance Variable. 
- Things objects know about itself:

    This is called INSTANCE VARIABLES:

        When thinking of the word instance, it is another way of saying object. The Instance Variable represents an object's state( or it's data). These can have unique values for each of the object's.
Object has an Instance Variable and methods, but these are design to work with the class. 

## Difference between class and object
- CLASS: 
    is not an object, but it's used to construct them.
        Think of a class as a blueprint to the object, the class mainly tell the java virtual machine how to contruct the object. 

- OBJECT:
    An object is a self-contained component which consists of methods and properties to make a particular type of data useful. Object determines the behavior of the class.
        When you ask an object to do something, you are actually asking the object to say no ,invoke, or the object says yes, which it will excute one of its methods based off what you asked it to do.  

## Making an Object
When making an Object you need two classes:

    One class for the type of object you want to use:
        - the main class your using like Dog, or Television; Something singular.

    Second class needs to a class that test the new class. 
  **Tester class**:
     - is where you put the main() method and within your main() method you create and access objects of your new class type. 

    The Tester class has one job: 
        - to try out the method and variable of your new object class type. 

### Writing the main class: 

    ```java 
    class Dog {
        // instance variables
        int x;
        String breed;
        String name;

        void bark() {   // a method
            System.out.println("RUFF! RUFF!");
        }
    }
    ```
### Writing a tester (TestDrive) class: second step

    ``` java 
    class DogTestDrive {
        public static void main(String[] args) {// main method
            // Dog test code goes here;
        }
    }
    ```
    In your tester, make an objects and access the object's variables and methods: third step

    ``` java
    class DogTestDrive {
        public static void main(String[] args) {
            Dog d = new Dog();    //making this a dog object//
            d.size = 40; // to set the size of the Dog
            // use the dot operator (.) 
            d.bark(); // ad to call its bark() method
        }
    }
    ```
## Two Uses of Main()
The test program to run within the main() method, but the true application, needs objects to talk to other objects and call methods, as opposed to a static main() method creating and testing objects. 

- to test your real class
- to launch/start your Java application

A real Java application is nothing but objects that are always communicating with other objects; communicating means objects calling methods on one another. 
