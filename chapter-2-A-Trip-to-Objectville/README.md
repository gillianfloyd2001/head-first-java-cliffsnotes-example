# Classes and Objects

## Table of Contents
- Difference between things objects do and knows
- Difference between class and object
- Making an object
- Two uses of main()

## Differences between things objects do and know
- Things objects can do: 
    These things are called methods:
        It's common to have methods that can read and write these values of the Instance Variable. 
- Things objects know about itself:
    This is called INSTANCE VARIABLES:
        when thinking of the word instance, it is another way of saying object. The Instance Variable represents an object's state( or it's data). These can have unique values for each of the object's.
Object has an Instance Variable and methods, but these are design to work with the class. 
## Difference between class and object
- CLASS: 
    is not an object, but it's used to construct them.
        Think of a class as a blueprint to the object, the class mainly tell the java virtual machine how to contruct the object. 
- OBJECT:
    Each object that was constructed from that class has it's own values for the Instance Variable of that class.
## Making an Object
When making an Object you need two classes:
    One class for the type of object you want to use:
        - the main class your using like Dog, or Television; Something singular.
    Second class needs to a class that test the new class. 
        This is called a Tester class:
            - which is where you put the main method and within your main method you create and access objects of your new class type. 
            The Tester class only has one job: 
                - this job is to try out the method and variable of your new object class type. 

write the class: this it the first step

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
writing a tester (TestDrive) class: second step

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
## Two Uses of Main
The test program to run within the main method, but the true application, needs objects to talk to other objects and call methods, as opposed to a static main() method creating and testing objects. 

- to test your real class
- to launch/start your Java application

A real Java application is nothing but objects that are always communicating with other objects; communicating means objects calling methods on one another. 
