# Modulo division, or division with remainders


When young children are first introduced to division at school they are taught to give the answer as a number and a remainder. So the answer to 7 divided by 4 would be "1 remainder 3".

As you learn about fractions and decimals this way of doing division seems very childish, but surprisingly, computer coding can make great use of division with remainders. In fact the remainders are so important that Python has a special method of calculating them. In addition to the normal arithmetic operators for add (+), subtract (-), multiply (\*) and divide(/) Python also has one for "*modulo division*" which uses a % sign.

So in Python ```24/7``` will give the result with decimals if you divide 24 by 7, but ```24%7``` will give the remainder if you divide 24 by 7. Can you work out what it would be?

You can quickly find the answer using the Python shell - this is a window where every line begins with ```>>>```. 

* If you are using the Python IDLE editor the first window which opens will be a Python shell, and you can type calculations like this straight into it. 
* If you are using *Visual Studio Code* you can open a Python shell by opening a terminal window - go to View>Integrated Terminal or View>Terminal - then typing ```Python``` in the terminal.
* You can also quickly get a Python shell on the internet by going to [trinket.io/console](https://trinket.io/console).

Try typing ```24%7``` into the Python shell.

To investigate these remainders try doing modulo division by 3 for the numbers from 1 to 8. Type
```
1%3
2%3 etc
.
.
.
8%3
```

You should see that the remainders follow a repeating pattern. Because we did mod division by 3 this pattern is 3 numbers long.

The repeating pattern of remainders also extends into negative numbers. You can check this with the Python shell by doing mod division of negative numbers:
```
-5%3
-4%3
-3%3
-2%3
-1%3
0%3
1%3
```

You will see that the repeating pattern 0 1 2 continues back beyond 0 into the negative numbers.

Here are three ways we can use modulo division in Python coding:

[Code Club Python project *Secret Messages*](Example1.md)

[Code Club Python project *Rock Paper Scissors*](Example2.md)

[Using a list where you need the list to repeat](Example3.md)

