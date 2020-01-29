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

- Example of superclass:
    ```java
    class Teacher {
        String designation = "Teacher";
        String collegeName = "BegginnerBook";

        void does() {
            System.out.println("Teaching");
        }
    }
    ```

The class `Teacher` is the superclass this will not inherit from anything. But the next example will be a subclass which will inherit from the superclass.

```java
public class PhysicsTeacher extends Teacher { // the subclass is PhysicsTeacher
    String mainSubject = "Physics";
    public static void main(String[] args) {
        PhysicsTeacher obj = new PhysicsTeacher();
        System.out.println(obj.collegeName);
        System.out.println(obj.designation);
        System.out.println(obj.mainSubject);
        obj.does();
    }
}
```
You can only use `extends` on the superclass when creating a subclass.

Bases off this example, I can say that a PhysicsTeacher **is-a** Teacher. This means that a subclass has a **is-a relationship** with the superclass.

## Overriding methods
- Declaring a method in your subclass which is already present in your superclass is know as method overriding. Overriding is done so that a subclass can give it's own implementation to a method which is already provided by the parent class.
    - In this case the method in superclass is called overridden method.
    - The method in the subclass is called overriding method.


```java
class Human {
    //Overridden method
    public void eat() {
        System.out.println("Human is eating");
    }
}

class Boy extends Human {
    //Overriding methods
    public void eat(){
        System.out.println("Boy is eating");
    }
    public static void main(String[] args) {
        Boy obj = new Boy();
        //This will call the subclass version of eat()
        obj.eat();
    }
}
```
- Output:
    - Boy is eating.

##### Why do we use Overriding methods?
- The main reason we override is that the class can give it's own specific implementation to a inherited method without even changing the superclass code. 

    - This is helpful when a class several subclasses, so if a subclass needs to use the superclass method, 
    
    - it can use it and the other classes that want to have different implementation can use overriding feature to make changes without touching the superclass code.
    

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
- In your tester, make an objects and access the object's variables and methods: third step

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
