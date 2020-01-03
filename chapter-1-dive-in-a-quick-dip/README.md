# Breaking The Surface

## Table Content
- Code Structure in Java
- Anatomy of a Class
- Writing a Class with a Main
- What can you say in the main method? 
- Looping and looping and...
- Simple Boolean Test
- Conditional Branching 

## Code Structure in Java
- What is a Source File and What goes in it?
A source file has a source code in it which has a .java extension on it. This holds one class definition which is just a piece of your program. So in other words your Class goes into your Source File. 
- What goes in a Class? 
Inside your class, it has one or many methods. For the method, this holds instructions for how the class should work. 
- What goes in a method?
Within the method, there are statements that go into the method. These statements are like instructions for how the method should performed. 
## Anatomy of a class
When running a java program, it looks for class in your command line that is the same name as the source file. After looking for this command line, they look for a specially-written line of code.
 ``` java
public staic void main(String[] args) {
     // my code would go here. 
}
```
After looking for code that looks like that, the program then runs the code that is in between the curly braces of your main method. Every Java applications has at least one class or at least one MAIN method. I only need one main per application. 
## Writing A Class With A Main 
In Java, EVERYTHING goes into a class. 
- First:
    You will type up your source code file with the java extension 
- Secondly: 
    then you must compile it into a new class file (with .class extensions) 

- What is JVM?
    Java Virtual Machine

When running a program this mean telling the JVM to load the name of the source code file name, then this excutes the main() method. This keeps the code running until the main() is finished. 

- What is main()? 
    main() is a method where your program starts. 

NO MATTER HOW BIG YOUR CODE OR HOW MANY CLASSES IT USES, YOU ALWAYS HAVE TO USE AT LEAST ONE MAIN(), and this must be the first class you use.
## What can you say in the main method? 
You can tell your program to do these things once in the main or any other method:
- Statements:
        declarations, assignments, and method calls
            ``` java 
            int x = 3;
            String name = "Dirk";
            x = x * 17;
            System.out.print("x is " + x);
            // this is a comment
            ```
- Loops:
        for loop and while loop
            ``` java 
            while (x > 12 ) {
                x = x -1; 
            }

            for (int x = 0; x < 10; x = x + 1) {
                System.out.print("x is now" + x);
            }
            ```
- Branching:
        If/else test:
            ``` java 
            if (x === 10 ){
                System.out.print("x must be 10");
            } else {
                System.out.print("x isn't 10");
            }
            if ((x < 3 ) & (name.equals("Dirk"))) {
                System.out.println("Gently");
            }
            System.out.print("this line runs no matter what");
            ```
## Looping and Looping and...
three types of standard looping constructs:
- while
- do-while
- for 

When talking about the while loop, as long as some condition is true, the program states that you need to do it inside the loop BLOCK.

- What is a Loop Block:
This is bounded by a pair of curly braces, so if you repeat anything it needs to be inside the block.

The key to looping is the conditional test in other words a test that returns a value of true or false using booleans.
## Simple Boolean Test
- COMPARISON OPERATOR: 
    (<) less than, (>) greater than, or (==) equality; ( this does have to 2 equal signs )
  
one equal sign means assignment while two equal signs means the comparison of two things. 
## Conditional Branching
- if test is basically the same as the boolean test in a while loop
``` java 
class IfTest {
    public static void main (String[] args) {
        int x = 3;
        if (x === 3 ) {
            System.out.println("x must be 3");
        }
        System.out.println("This runs no matter what");
    }
} 
```
depending on the value of x, either one statement or two will print out. 

if I add an else statement...
```java
class IfTest {
    public static void main (String[] args) {
        int x = 2;
        if (x === 3 ) {
            System.out.println("x must be 3");
        }else{
            System.out.println("x is NOT 3");
        }
        System.out.println("This runs no matter what");
    }
} 
```