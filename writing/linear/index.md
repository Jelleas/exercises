# Linear Search

> Bij deze opdracht is het helemaal prima om samen te werken met één of twee medestudenten. Zorg dat je gezamenlijk op één scherm kunt kijken en echt samen het probleem probeert op te lossen. Heeft iemand een goed idee, dan moet die zorgen dat de anderen het ook begrijpen. De bedoeling is dat alle samenwerkers evenveel hebben bijgedragen aan de opdracht. Iedereen levert uiteindelijk een eigen versie in.

Write a program that can find a needle in a haystack using linear search. Well, we won't be using literal needles and haystacks (that would be too unwieldy), but rather integer numbers and arrays respectively.


## Getting started

    $ mkdir ~/problems/linear
    $ cd ~/problems/linear
    $ wget https://github.com/minprog/exercises/raw/main/writing/linear/find-linear.c


## Specification

Write a program that can find a needle in a haystack using linear search. Remember linear search? It is the slow way of going through the phone book. You start with the first name in the book and you go through the book name after name until you find the person you were looking for.

In our case, we won't be looking for names in a phone book, but a number (integer) in a list (array). For the purpose of this exercise we'll call our array the *haystack* and our number the *needle*. The output of the program should look something like this (where the numbers at the end of each line denote the user input):


    $ ./find-linear 42
    
    haystack[0] = 3
    
    haystack[1] = 14
    
    haystack[2] = 15
    
    haystack[3] = 42
    
    haystack[4] = 11235
    
    haystack[5] = 1
    
    haystack[6] = ^D
    ---------------------------------------------------------
    I will try to find needle "42" in the following haystack:
    [3, 14, 15, 42, 11235, 1]
    Found needle in haystack!


The program `./find-linear` expects one command line argument: the needle. Once it starts, it asks the user to enter a number. It keeps on asking for numbers until the user enters `^D` (ctrl-d). These numbers will form the haystack. The program will have to print the haystack, and find the needle in it.

### Assignment

For this assignment you don't have to worry about the user input. This has already been implemented for you. You will have two tasks to complete:

1. Implement the function `print_array`. This function will take an integer array as input and will have to print its contents.
2. Implement the function `search`. With this function you will implement linear search. The function takes an integer array and an integer value as input and will return `true` if and only if the value is found in the array.


## Walkthrough

### Compile

You can compile `find-linear.c` by executing the command:


    make find-linear

This will create the binary (executable) `find-linear` which you can execute:


    ./find-linear 42

Now you can enter numbers into the haystack. For, example:


    haystack[0] = 10
    haystack[1] = 42
    haystack[2] = ^d

You will get an output similar to this:


    ---------------------------------------------------------
    I will try to find needle "42" in the following haystack:

    Didn't find needle in haystack.

It doesn't work yet! It does not find the needle, and it does not show the array. You still have to write the functions that do this.

### find-linear.c

Let's look at the file `find-linear.c`. When you open it you will see that there is already a lot of code written. You can leave most of this code alone. The only thing you will have to implement are the functions:


    bool search(int value, int values[], int size)
    void print_array(int values[], int size)

But before getting to that, let's briefly step through the existing code in order to provide some context.

### Declarations

Near the top of the file, right after the `include`s you see the declaration of the functions you will have to implement. Here we just tell the compiler that these functions will be implemented later in the file.


    bool search(int value, int values[], int size);
    void print_array(int values[], int size);

### main

After that we have the `main` function. You don't have to change this function. Line 22 to 30 of the main function deal with the command line argument. This provides us with the needle. Line 33-47 is the code to create the haystack based on the user input.

Take a look at line 53 and 56 in the main function. Here you see the calls to the functions `print_array` and `search`, respectively.

### print_array

Start by implementing the function `print_array`. The current implementation starts on line 68, and looks as follows:


    void print_array(int values[], int size)
    {
        // TODO: print all the values in the array.

        // the next two lines should eventually be removed
        (void)values;
        (void)size;

        return;
    }

As you can see, it doesn't do much yet. Don't get distracted by the lines:


        (void)values;
        (void)size;

They don't actually do anything. These lines should be removed when you start implementing the function. The reason why these lines are there is a little beyond the scope of this assignment. But, if you are curious, feel free to ask the teacher/TA about it.

To implement this function try to keep the formatting readable. A common way to print an array is with square brackets around it and interspaced with comma's, like so:


    [3, 14, 15, 42, 11235, 1]

An empty list should look like this:


    []

Make sure that the empty list is also printed correctly!

### search

On line 79 you find the empty `search` function:


    bool search(int value, int values[], int size)
    {
        // TODO: find value in values. return true if found, otherwise return false.

        // the next three lines should eventually be removed
        (void)value;
        (void)values;
        (void)size;

        return false;
    }

The function returns a `bool` value, which should be `true` if the needle is found in the haystack, and `false`, otherwise. The current version of the function always returns `false`.

When you implement `search`, think about the edge cases:

- What happens if the needle is the first element of the haystack?
- What happens if the needle is the last element of the haystack?
- What happens if the haystack is empty?

Make sure those cases are handled correctly!


## How to submit

As soon as you're done, submit your implementation below! 

1. Toward CS50 IDE's top-left corner, within its "file browser" (not within a terminal window), control-click or right-click your `find-linear.c` file (that's within your `~/problems/linear` directory) and then select **Download**. You should find that your browser has downloaded `find-linear.c`.

2. Make sure you are signed in to **this** website!

3. Type the names of students that you've worked with on this problem: <input name="form[samen]" type="text" required>

4. In the form below, choose the file that you just downloaded.

5. Press "Submit for grading". Presto!
