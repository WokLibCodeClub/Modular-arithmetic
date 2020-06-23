### Raspberry Pi Foundation/Code Club Python project *Secret Messages*

This is one of the Raspberry Pi Foundation/Code Club projects which shows how you can use Python to send secret messages by encrypting and decrypting them using a method called the Caesar Cipher (this is because this method of secret code was used by the ancient Roman emperor Julius Caesar).

https://projects.raspberrypi.org/en/projects/secret-messages

First, I number all the letters of the alphabet like this:
```
 A   B   C   D   E   F   G   H   I   J   K   L   M   N   O   P   Q   R   S   T   U   V   W   X   Y   Z
 0   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25
```

then for every letter I want to put in my secret message I simply move three letters to the right in the alphabet and take that letter. So if I wanted to encrypt the letter F I would move three places right and take the letter I. If moving three places takes me past Z then I loop round back to A, so if I want to encrypt the letter Y the answer would be the letter B.

You may already be beginning to suspect we can use modulo division in the Python code.

One way to write Python code to do the encryption is to put the letters of the alphabet into a text variable

```
alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
```
Then, to print the item of the list with index 6 I would write the code
```
print(alphabet[6])
```
This would print the letter G. Why G? (Don't forget that the first item in the list has the index 0.)

If I want to encrypt the letter G for my secret message I would want to get the item with index 6 + 3 in the list, because by adding 3 to the index I move three places to the right. This would produce index 9 of the list, ```alphabet[9]``` which is letter J.

But what happens if I want to encrypt Y which has an index 24? Using my rule for looping past the end of the alphabet back to the beginning I would want the answer to be B. But if I use Python to add 3 to index 24 I get index 27, but my text string doesn't have an item with index 27, so the programme terminates with an error.

The way to do this is to use **modulo division**, and because my alphabet has 26 items in it I want to use mod division by 26. In other words, I want to calculate the remainder when I divide by 26.

Check out mod division by 26 in a Python shell (get to a Python shell as explained in the [previous page](README.md)):
Type
```
24%26
25%26
26%26
27%26
28%26
```
That should be enough to show you what happens.

When the remainders get to 25 they loop back to 0 and start counting up again.

Go back to encrypting the letter Y, which has index 24. I add 3 which makes 27, but now I do mod division by 26, which gives me an answer 1. This is the index of the letter B, which is the answer I want.

So, using modulo division automatically loops round from the end of the alphabet back to the beginning. Magic!

Modulo division also lets us loop from the front of the list round to the back. We need to do this if we are decrypting a secret message, since decrypting is the opposite of encrypting. The process is to take each letter in the secret message, move three places to the LEFT, and find out what the letter was in the original message.

In Python code this means *subtracting* three from the index number of the letter in the encrypted message. So if the encrypted message contained the letter P ```alphabet[15]``` I would subtract 3 from the index to get ```alphabet[12]``` and know that the decrypted letter was letter M.

But what if the encrypted letter was A ```alphabet[0]```? I would subtract 3 and get index -3, but my list doesn't have an item with index -3. Luckily modulo division continues the repeating pattern into the negative numbers, so if I subtract 3 from index 0, then do mod division by 26 the answer is index 23, which points to letter X, which is the letter I want.

Go back to [index for Modulo Division](README.md)
