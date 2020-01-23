# Extra-Strenght Methods


## Table Of Contents
---
- Introduction
- Building the Sink a Dot Com game
- Starting with the Simple Dot Com game (a simpler version)
- Writing prepcode ( Pseudocode for the game)
- Test code for Simple Dot Com
- Coding the Simple Dot Com 
- Final code for Simple Dot Com
- Generating random Number with Math.random()
- Ready-bake code for getting user input from the command-line
- Looping with *for* loops
- Casting Primitives from a large size to a smaller size

## Introduction:
---
- In this chapter, we need more power like __operators__ and __loops__. It might be useful to __generate random numbers__ and __turn a String into an int__. The easiest way to learn all this is by building something real, to see what it's like to write (and test) a program from scratch.

## Building the Sink a Dot Com game:
---
- This is going to be a Battleship-style game:

- It's you against the computer, but unlike the real Battleship game, in this one you don't place any ships of your own. Instead, your job is to sink the computer's ships in the fewest number of guesses. 
    - In this game, you will be killing Dot Coms.
    - __Goal__: Sink all of the computer's Dot Coms in the fewest number of guesses. You're given a rating or level, based on how erll you perform.
    - __Setup__: When the game program is launched, the computer places three Dot Coms on a __virtual 7x7 grid__. When that's complete, the game asks for your first guess.
    - __How you play__: We haven't learned to build a GUI yet, so this version works at the command-line. The computer will prompt you to enter a guess(a cell), that you'll type at the command - line as "A3", "C5", ect. In response, to your guess, you'll see a result at the command - line, either "Hit", "Miss", or "You Sunk Pets.com" (or whatever the lucky Dot Com of the day is). When you've sent all three Dot Coms to that big 404 in the sky the game ends by printing out your rating. 
### First, a high-level design:
- We know we'll need classes and methods. We need more information about what the game should do. First, we need to figure out the general flow of the game. 
    1. User starts the game:
        - Game creates three Dot Coms
        - Game places the three Dot Coms onto a virtual grid.
    2. Game plays begin repeat the following until there are no more Dot Coms:
        - Prompt user for a guess("A2","C0",ect.).
        - Check the user guess against all Dot Coms to look for a hit, miss, or kill. Take appropriate action: if    a hit, delete cell (A2, D4, ect.). If a kill, delete Dot Com.
    3. Game finishes.
        - Give the user a rating based on the number of guesses.
    
    - Now we have an idea of the kinds of things the program needs to do. The next step is figuring out what kind of __objects__ we'll need to do the work. Remember, think like Brad rather than Larry; focus first on the __things__ in the program rather than the *_procedures_*.

## Starting with the Simple Dot Com game (a Simpler Version):
---
- It looks like we're gonna need at least two classes, a Game class and a DotCom class. But before we build the full monty __Sink a Dot Com__ game, we'll start with a stripped-down, simplified version, __Simple Dot Com Game__. We'll build the simple version in *this* chapter, followed by the deluxe version that we build in the *next* chapter.

- Everything is simpler in this game. Instead of 2-D grid, we hide the Dot Com in just a single *row*. And instead of *three* Dot Com, we use *one*
    1. __Game Starts__, and creates ONE DotCom and gives it a location on three cells  in the single row of seven cells.

    Instead of "A2", "C4", and so on, the locations are just integers ( for example 1,2,3 are the cell locations in this picture. )

        -----------------------------------------
        |         |         |         |          |   
        -----------------------------------------
              1         2         3          4

    2. __Game Play Begins__: Prompt user for a guess, then check to see if it hit any of the DotCom's three cells. If a hit, increment the numOfHits variable. 

    3. __Game Finishes__: When all three cells have been hit(the numOfHits variable value is 3), and tells the user how many guesses it took to sink the DotCom.

        - __A complete game interaction__:

            - enter a number: 2
                >- hit
            - enter a number: 3
                >- hit
            - enter a number: 4
                >- miss
            - enter a number : 1
                >- kill

            - You Took 4 Guesses.

- The goal is the same, though, so the game still needs to make a DotCom instance assign it a location sowmehere in the row, get user input, and when all of the DotCom's cells have been hit, the game is over. This simplified version of the game gives us a big head start on building the full game. If we can get this small one working, we can scale it up to the more complex on later.       
```java
class SimpleDotCom {
    int[] locationCells;
    int numOfHits;

    String checkYourself(String guess);
    void setLocationCell(int[] loc);
}
```

- In this simple version, the game class has no instance variables and all the game code is in the main() method. In other words, when the program is launched and mian() begins to run, it will make the one and only FotCom instance, pick a location for it (three consecutive cells on the single virtual seven-cell row), ask user  for a guess, check the guess, and repeat until a three cells have been hit.

- Keep in that the virtual row is...*Virtual*. In other words, it doesn't exist anywhere in the program.

### Developing a Class:
---
- As a programmer, you probably have a methodology/process/approach to writing code. 
    - Our sequence is designed to help yoiu see (and learn) what we're thinking as we work through coding a class. It isn't necessarily the way we (or you) write code in the Real World. In the Real World, of course, you'll follow the approach your rersonal preferences, project, or employer dictate. 
    - When we create a Java class as a "learning experience", we usually do it like this:
        - [] Figure out what the class is supposed to do.
        - [] List the __instance variables and methods__.
        - [] Write __precode__ for the methods.(You'll see this in just a moment). 
        - [] Write __test code__ fo the methods.
        - [] __Implement__ the class.
        - [] __Test__ the methods.
        - [] __Debug__ and __reimplement__ as needed.
        - [] Express gratitude that we don't have to test our so-called learning expreience app on actual live           users.
- The Three things we'll write for each class:
    - Prep Code --> Test Code --> Real Code
        - This bar is splayed on the next set of pages to tell you which part you're working on. For example, if your see this picture at the top of a page, it means you're working on prpcode for the Simple DotCo class.
    - __prep code__: A form of pseudocode, to help you focus on th elogic with out stressing about syntax.
    - __Test code__: A class or methods that will test real and validate that it's doing the right things.
    - __real code__: The actual implementation of the class. this is where we write real java code.
## Writing Prepcode (Pseudocode for the game):
---
- When using prepcode, it's sort of half-way between real Java code and a plain English description of the class. Most prepcode includes three parts:
    >- instance variable declarations
    >- methods declarations
    >- method logic
- But out of these three the most important part of prepcode is method logic. 
    - The reason why is, because it defines *what* has to happen, which we later translate into *how*, we actually write the method code.
- Example of Prepcode:
    - Instance Variable Declaration:
        >- __Declare__ an __*int array*__ to hold the location cells, Call it __*locationCells*__. 
        >- __Declare__ an __*int*__ to hold the number of hits. Call it __*numOfHits*__ and __SET__ it to 0.
        ---
    - Methods Declarations:
        >- __Declare__ a __*checkYourself()*__ method that takes a __*string*__ for the user's guess ("1", "3", ect.), checks it and returns a result representing a "hit", "miss", or "kill".
        >- __Declare__ a __*setLocationCells()*__ setter method that takes an __*int array*__ (which has the three cell locations as __*ints*__(2,3,4,etc.)).
        ---
    - Method Logic:
        >- __Method__: *String checkYourself(String userGuess)
            >- __Get__ the user guess as a String parameter
            >- __Convert__ the user guess to an __*int*__
            >- __Repeat__ with each of the location cells in the __*int*__ array.
                >- __// COMPARE__ the user guess to the location cell
                >- __If__ the user guess matches
                    >- __INCREMENT__ the number of hits
                    >- __// FIND OUT__ if it was the last location cell:
                    >- __If__ number of hits is 3, __RETURN__ "kill" as the result
                    >- __ELSE__ it was not a kill, so __RETURN__ "hit"
                    >- *END IF*
                >- __ELSE__ the user guess did not match, so __RETURN__ "miss"
                >- *END IF*
            >- *END REPEAT*
        >- *END METHOD*
        >- __METHOD__: __*void setLocationCells(int[] cellLocations)*__
            >- __GET__ the cell locations as an __*int array*__ parameter
            >- __ASSIGN__ the cell locations parameter to the cell locations instance variable 
        >- *END METHOD*
### Writing the method implementations:
---
- Before we start coding the methods, though, let's back up and write some code to *test* the methods.
    - The concept of writing the test code first one of the practices of Extreme Programming (XP), and it can make it easier (and faster) for you to write your code. 
#### Extreme Programming (XP):
---
- Extreme Programming(XP) is a newcomer to the software development methodology world. Considered by many to be "the way programmers really want to work," XP emerged in the late 90's and has been adopted by companies ranging from the two-person garage shop to the Ford Motor Company.
- XP is based on a set of proven practices that are all designed to work together, although many folks do pick and choose, and adopt only a portion of XP's rules. these practices include things like:
    - Make small, but frequent, releases
    - Develop in iteration cycles.
    - Dont release anything until it passes all the test.
    - Keep it simple, ect.
## Test code for Simple Dot Com:
---
- We need to write test code that can make a SimpleDotCom object and run its methods. For the SimpleDotCom class,  we really care about only the `checkYourself()` method, although we will have to implement the `setLocationCell()` method in order to get the `checkYourself()` method to run correctly.

- __Based on the this prepcode__:

    >- __Method__ String checkYourself(String userGuess)
        >- __Get__ the user guess as a String parameter
        >- __Convert__ the user guess to an __*int*__.
        >- __Repeat__ with each of the location cells in the __*int*__ array.
            >- __// Compare__ the user guess to the location cell
            >- __IF__ the user guess mathches 
                >- __INCREMENT__ the number of hits
                    >- __// FIND OUT__ if it was the last location cell:
                    >- __If__ number of hits is 3, __RETURN__ "kill" as the result
                    >- __ELSE__ it was not a kill, so __RETURN__ "hit"
                    >- *END IF*
                >- __ELSE__ the user guess did not match, so __RETURN__ "miss"
                >- *END IF*
            >- *END REPEAT*
        >- *END METHOD*

- __Here's what we should test:__

    1. Instantiate a SimpleDotCom object.
    2. Assign it a location (an array of 3 ints, like {2,3,4}).
    3. Create a String to represent a user guess ("2", "0", etc.)
    4. Incoke the `checkYourself()` method passing it the fake user guess.
    5. Print out the result to see if it's correct ("passed" or "failed").

## Coding the Simple Dot Com:
---
```java 
public class SimpleDotComTestDrive {
    public static void main (String[] args) {
        SimpleDotCom dot = new SimpleDotCom();// instantiate a SimpleDotCom object

        int[] locations = {2, 3, 4};// make an int array for the location of the dot com (3 consecutive ints out of a possible 7)

        dot.setLocationCells(locations); // invoke the setter method on the dot com.
        
        
        String userGuess = "2";  // make a fake user game

        String result = dot.checkYourself(userGuess); // invoke the checkYourself() method on the dot com object, and pass it to fake guess.

        String testResult = "failed"; 
        if (result.equals("hit")) {
            testResult = "passed";// if the fake guess(2) gives back a "hit", it's working
        }
        System.out.println(testResult); // print out the test result (passed or failed)
    }
}
```
### The checkYourself() method:
---
- There isn't a perfect mapping from prepcode to javacode; you'll see a few adjustments. The prepcode gave us a much better idea of *what* the code needs to do, and now we have to find the java code that can do the *how*. 

- In the back of your mindm be thing about parts of this code you might want (or need) to improve. The numbers (1.) are for things (syntax and language features) you haven't seen yet. They're explained on the opposite page.
```java
public String checkYourself(String stringGuess) {
    int guess = Integer.parseInt(stringGuess); // convert the String to an int
    
    String result = "miss";// make a variable to hold the result we'll return. Put "miss" in as the default.

    for (int cell : locationCells) {// repeat with each cell in the locationCells array (each cell location of the objects )

        if (guess == cell) {// compare the user guess to this element (cell) in the array
            result = "hit"; 
            numOfHits++;
            break;// get out of the loop, no need to test the other cells
        }// end if 
    }//end for 

    if (numOfHits == locationscells.length) {
        result = "kill";
    } // end if 
    System.out.println(result); // display the result for the user

    return result; // return the result back to the calling method
}// end method
```

### Just the New Stuff:
---
- the things we haven't seen before are on this page. The rest of the details are at the end of the chapter. This is just enough to let you keep going.
    1. Converting a __String to an Int__:
    ```java
    // (Integer) - a class that ships with java
        Integer.parseInt("3") // takes a String
             // (parseInt)- A method in the Integer class that knows how to "parse" a String into the int it represents.
    ```

    2. The __for__ loop: 
    ```java
        //(for) - for each element in the `locationCells` array: take the next element in the array and assign it to the int.
                    //(:) - the colon means "in", so the whole thing means "for each int value IN locationCells..."
        for(int cell : locationCells) {}
            // (int cell)- Declare a variable that will hodl one element from the array.
                        // (locationCells) - the array to iterate over in the loop.
    ``` 

    3. the __post-increment operator__:
    ```java 
        // numOfHits++ is the same(in this case) as saying numOfHits = numOfHits + 1, except slightly more efficient.

        numsOfHits++ // (++) - means add 1 to whatever's there (in other words, increment by 1).
    ```

    4. __break__ statement:
    ```java
        // Gets you out of a loop. Immediately. Right here. no iteration, no boolean test.  
        break;
    ```
## Final code for Simple Dot Com:
---
```java 
public class SimpleDotComTestDrive {
    public static void main(String[] args) {
        SimpleDotCom dot = new SimpleDotCom();
        int[] locations = {2, 3, 4};
        dot.setLocationCells(locations);
        String UserGuess = "2";
        String result = dot.checkYourself(userGuess);
    }
}
```
---
```java
public class SimpleDotCom {
    int[] locationCells;
    int numOfHits = 0;

    public void setLocationCells(int[] locs) {
        locationCells = locs;
    }
    public String checkYourself(String stringGuess) {
        int guess = Integer.parseInt(stringGuess);
        String result = "miss";
        for (int cell : locationCells ) {
            if (guess = cell) {
                result = "hit";
                numOfHits++;
                break;
            }
        }// out of the loop

        if (numOfHits == locationCells.length) {
            result = "kills";
        }
        System.out.println(result);
        return result;
    }//close method
}// close class
```

### Bullet Points:
---
- Your Java program shoudl start with a high-level design. 
- Typically you'll write three things when you create a new class: 
    - __prepcode__
    - __testcode__
    - __real(java)code__
- Prepcode should describe what to do, not how to do it. Implementation comes later.
- Use the prepcode to help design the test code.
- Write test code before you implement the methods. 
- Choose *for* loops over whike koops when you know how many times you want to repeat the loop.
- Use the pre/post increment operator to add 1 to a variable (x++;)
- Use __Integer.parseInt()__ to get the int value of a String.
- __Integer.parseInt()__ works only if he string represents a digit("0", "1", "2", etc.)
- Use *break* to leave a loop early(i.e even if the boolean test condition is still true.)

### The Game's main() method:
---
- Just as you did with the SimpleDotCom class, be thinking about parts of this code you might want (or need) to improve. The numbered things (1.)  are for stuff we want to point out. They're explained on the opposite page. Oh, if you're wondering why we skipped the rest code phase for this class, we don't need a test class for the game. It has only one method.
    - so what would do in your test code? 
    - Make a separate class that would call main() on this class?
- We didn't do either of them.
```java
public static void main(String[] args) {
    int numOfHits = 0; // make a variable to track how many guesses the user makes

    GameHelper helper = new GameHelper();// this is a special class we wrote that has the method for getting user input for now.

    SimpleDotCom theDotCom = new SimpleDotCom();// make the dot com object
    int[] randomNum = (int) (Math.random() * 5);// make a random number for the first cell

    int[] locations = {randomNum, randomNum+1, randomNum+2};// make a random number for the first cell, use it to make the cell locations array

    theDotCom.setLocationCells(locations);// give the dot com its location (the array).
    boolean isAlive = true;

    // make a boolean variable to track whether the game is still alive, to use in the while loop test repeat while game is still alive. 
    while ( isAlive == true ) {
        String guess = helper.getUserInput("enter a number");// get user input String

        String result = theDotCom.checkYourself(guess);// ask the dot com to check the guess; save the returned results in a String

        numOfGuesses++;// increment guess count 
        if (result.equals("kills")) {
            isAlive = false;// set is asalive to false.
            System.out .println("You took" + numOfGuesses + " guesses");
        }// close if 
    }// close while
}// close main
```
## Generating random Number with Math.random():
--- 
- Two things that need a bit more explaining. This is just a quick look to keep you going; more details on the GameHelper class are at the end of this chapter.
    1. make a random number: 
        ```java
        int randomNum = (int) (Math.random() * 5);
        //(int) - this is a cast and it forces the thing immediately after it to cecome the type of the cast (i.e. the type in the parents)

        // (* 5) - the Math.random() method returns a numver form zero to just less than one.  

        //(Math) - a class that come with java

        //(.random()) - a method of the Math class

        //(randomNum) - we declare an int variable to hold the random number we get back 

        ```
    2. Getting user input using the GameHelper class
    ```java 
   String guess = helper.getUserInput("entet a number");

   // (String guess) - we declare a String variable to hold the user input String we get back.
   // (helper ) - An instance we made earlier, of a class that we built to help with the game.
   // (getUserInput()- A method of the GameHelper class that asks the user for command-line input, reads it in after the user hits RETURN, and gives back the result as a string)
   // ("enter a number");- this method takes a string argument that it uses to prompt the user at the command line.
    ```
## Ready-bake code for getting user input from the command-line:
---
- __We made the *dot com* class__.
- __We made the *game* class__. 
- __All that's left id the helper class__-- the one with the getUserInput() method. The code to get command-line input is more than we want to explain right now. It opens up way to many topics best left for later.

```java
import java.io.*;
public class GameHelper {
    public String getUserInput(String propmt) {
        String inputLine = null;
        System.out.print(prompt + " " );
        try {
            BufferedReader is = new BufferedReader (new InputStreamReader(System.in));
            inputLine = is.readline();
            if (inputLine.length() == 0) return null;
        } catch (IOException e) {
            System.out.println("IOException: " + e);
        } 
        return inputLine;
    }
}
```

## Looping with *for* loops:
---
- We've covered all the game code for *this* chapter. We did not want to interrupt your work with some of the details and background info so we put it back here.
    - __Regular (non-enhanced) for loops__:
    ```java
    for(int i = 0; i < 100; i++);

    // (int i = 0) - initialization
    // (i< 100); - boolean test 
    //(i++ ) - iteration expression
    ```
    - __What does this mean in plain English__: Repeat 100 times
    - __How the compiler sees it__:
        - create a variable *i* and set it to 0.
        - repeat while *i* is less than 100.
        - at the end of each loop iteration, add 1 to *i*. 
    - __Part One__: *Initialization
        - use this part to declare and initialize a variable to use within the loop body. 
    - __Part Two__: *boolean test*
        - This is where the conditionsal test goes. Whatever's in there it must resolve to be a boolean value (true or false).
    - __Part Three__: *Iteration Expression*
        - In this part, put one or more things you want to happen with each trip through the loop. Keep in mind that this stuff happends at the end of each loop.
### Difference between for and while:
---
- A *while* loop has only the boolean test; it doesn't have a built-in initialization or iteration expresssion. A *while* loop is good when you don't know how many times to loop and just want to keep going while some condition is true. 
- But if you *know* how many time to loop, a *for* loop is cleaner.
```java
int i = 0;

while (i < 8 ) {
    System.out.println(i);
    i++;
}
System.out.println("done");
```
- output: 
0
1
2
3
4
5
6
7
done

## Casting Primitives from a large size to a smaller size:
- In chapter 3 we talked about the size of the various primitives, and how you cant shove a big thing directly into a small thing. 
```java
long y = 42;
int x = y; // won't work
```
- A long is bigger than an int and the compiler cant be sure where tha tlong has been. It might have been out drinking with other longs, and takin gon really big values. to force the compiler to jam the value of a bigger primitive variable into a smaller one, you can use the cast operator.
```java
long y = 42;
int x = (int) y;
```
- Putting in the cast tells the compiler to take the value of y, chop it down to int size, and set x equal to whatever is left. If the value of y was bigger than the maximum value of x, then what's left will be a weird number.
```java
long y = 40002;
// 40002 exceeds the 16-bit limit of a short 
short x = (short) y // x now equals -25534!
``` 
- Still, the point is that the compiler let's you do it. And let's say you have a floating point number, and you just want to get the whole number (int) part of it. 
```java
float f = 3.14f;
int x = (int) f; // x will equal 3
```

