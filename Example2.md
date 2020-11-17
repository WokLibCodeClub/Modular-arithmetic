### Raspberry Pi Foundation/Code Club Python project *Rock Paper Scissors* 

[Raspberry Pi Foundation/Code Club Python project *Rock Paper Scissors*](https://projects.raspberrypi.org/en/projects/rock-paper-scissors)

In the real life game of Rock Paper Scissors two players choose which of three three shapes to make with their hand. They both show the shapes together. Rock defeats Scissors, Scissors defeats Paper, and Paper defeats Rock, so there is a circular pattern here.

In the computer game you select which shape to make, and the computer chooses one of the shapes at random. The code has to work out whether you or the computer has won (of course, if both shapes are the same it is a draw).

In the Raspberry Pi Foundation/Code Club project there is a complicated ```if``` block to work out the winner, but we can make this much simpler using modulo arithmetic. Here's how.

Let's give Rock the number 0, Paper the number 1 and Scissors the number 2, so if you choose Rock your choice is 0 and if the computer randomly chooses Scissors the computer's choice is 2. We will create variables called ```your_choice``` and ```computer_choice``` and then subtract ```computer_choice``` from ```your_choice```.

Let's look at all the possibilities where you beat the computer:

```
  your                     computer's                         your_choice minus
 choice   your_choice =      choice      computer_choice =     computer_choice
--------  -------------    ----------    -----------------    ------------------
 Paper          1            Rock                0                 1-0 = 1
Scissors        2            Paper               1                 2-1 = 1
 Rock           0           Scissors             2                 0-2 = -2
```
You can see that when you win the value of the ```your_choice``` variable is bigger than the value of the ```computer_choice``` variable, except for the annoying case where you chose *rock* and the computer chose *scissors*.  One way for Python to tell which of two numbers is bigger is to subtract one from the other: if the answer is positive then the first number is bigger, and if the answer is negative then the second number is bigger. In the last column I have shown the answers if you subtract the ```computer_choice``` variable from the ```your_choice``` variable. The answer is always 1, except for the last line, where the answer is -2.

The subtraction gives 1 or -2 if you defeat the computer. But what if we use modulo division after the subtraction? We will divide by 3 because there three items in our circular pattern. In Python we code up ```(your_choice - computer_choice)%3```. (We need the brackets to make sure Python does the subtraction before the mod division because mod division follows the same rules as normal division for order of operations.) Here is the table with an extra column added:

```
  your                     computer's                         your_choice minus     modulo division
 choice   your_choice =      choice      computer_choice =     computer_choice           by 3
--------  -------------    ----------    -----------------    -----------------     ---------------
 Paper          1            Rock                0                 1-0 = 1            (1-0)%3 = 1
Scissors        2            Paper               1                 2-1 = 1            (2-1)%3 = 1
 Rock           0           Scissors             2                 0-2 = -2           (0-2)%3 = 1
```
We see that whenever you beat the computer, the subtraction followed by mod division by 3 is always 1. 

Now let's draw a table for all the possibilities where the computer beats you:

```
  your                     computer's                         your_choice minus     modulo division
 choice   your_choice =      choice      computer_choice =     computer_choice           by 3
--------  -------------    ----------    -----------------    -----------------     ---------------
 Paper          1           Scissors             2                 1-2 = -1           (1-2)%3 = 2
Scissors        2            Rock                0                 2-0 = 2            (2-0)%3 = 2
 Rock           0            Paper               1                 0-1 = -1           (0-1)%3 = 2
```
We see that whenever the computer beats you, the subtraction followed by mod division by 3 is always 2.

There is a third possibility - that both you and the computer choose the same shape - in this case the game is a draw. You can probably work out, without seeing a table, that, in this case, the subtraction followed by mod division by 3 always gives 0.

So here's how Python can work out who won Rock, Paper, Scissors with only three lines of code:

1. make a **list** of possible outcomes of  the game:
```
outcomes = ["It was a draw", "You won", "You lost"]
```
The code will print one of these three outcomes after each game.

2. Write Python code to carry out subtraction followed by mod division by 3 and put the answer in a variable called ```result```:

```
result = (your_choice - computer_choice) % 3
```

3. Use the variable ```result``` as the index for the item to print from the list of outcomes. So if result = 0 (meaning it was a draw) Python will print the item in the list with index 0 (the first item), if result = 1 (meaning you beat the computer) Python will print the second item in the list and if result = 2 (meaning the computer beat you) Python will print the third item:
```
print(outcomes[result])
```
Just three lines! All because of the Python ```%``` operator.

Actually, you can combine the last two lines, because Python can do calculations **inside** a ```print()``` statement, so we don't really need the variable ```result```:
```
print(outcomes[(your_number - computer_number)%3])
```

Go back to [index for Modulo Division](README.md)
