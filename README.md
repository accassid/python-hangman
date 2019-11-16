# Python Hangman

1. Import the Draw Function
In Trinket, press the '+' icon to the right of your `main.py` tab to create a new file. Name it `draw.py`. Then copy the following code into that file:
```python
import random

'''
A function that takes in a number of incorrect guesses and prints out a text hangman.
-Andy Cassidy
'''
def draw_hangman(count):
  if count == 0:
    print('   _____\n   |   |\n   |\n   |\n   |\n   |\n   |\n----------')
  elif count == 1:
    print('   _____\n   |   |\n   |   O\n   |\n   |\n   |\n   |\n----------')
  elif count == 2:
    print('   _____\n   |   |\n   |   O\n   |   |\n   |   |\n   |\n   |\n----------')
  elif count == 3:
    print('   _____\n   |   |\n   |   O\n   |   |/\n   |   |\n   |\n   |\n----------')
  elif count == 4:
    print('   _____\n   |   |\n   |   O\n   |  \|/\n   |   |\n   |\n   |\n----------')
  elif count == 5:
    print('   _____\n   |   |\n   |   O\n   |  \|/\n   |   |\n   |  /\n   |\n----------')
  else:
    print('   _____\n   |   |\n   |   O\n   |  \|/\n   |   |\n   |  / \\\n   |\n----------')


'''
A function that generates a random word from a word list file.
-Andy
'''
def get_tech_word():
  words = []
  with open('words.txt') as f:
    words = f.read().splitlines()
  return random.choice(words)
  
```
Create another file called `words.txt` and paste the following in:
```
speakers
laptop
memory
browser
download
password
hacking
videogame
internet
router
scratch
tablet
virus
website
monitor
keyboard
graphics
upload
```
Go back to your `main.py` tab and in that file, at the top, add the following line of code.
```
from draw import draw_hangman, get_tech_word
```

2. This gives us access to the `draw_hangman` and `get_tech_word` functions in `main.py`. Try using it by calling the draw function with any number of guesses between 0 and 6 and see what happens. eg: `draw_hangman(4)` Try getting a random tech word and printing it out `print(get_tech_word())`

3. Make a list that keeps track of what letters have been guessed incorrectly and another list that keeps track of what letters have been guessed correctly.
```python
incorrect = []
correct = []
```

4. Make a variable named `answer` and assign a tech word to it using the `get_tech_word` function.

5. Make a while loop that continues as long as the length of incorrect is less than six (meaning the user has guessed incorrectly no more than six times).
```python
while len(incorrect) <= 6:
```

6. In that while loop, ask for a guess from the user using the `input` function and store in a variable.
```python
guess = input('Guess a letter')
```
Now if you run your code it should repeatadely ask the user for a letter.

7. We should now check if the user's guess is in the word or not. Use an if statement and the function you made before to check if a letter is in a word.
```python
if letter_in_word(answer, guess):
```
If the letter is in the word, append the guess to the correct list with `correct.append(guess)`. Else (the guess is incorrect), append the guess to the incorrect list.

8. Before you ask the user for a guess in your while loop, also print our our hangman with the `draw_hangman` function passing in the current number of incorrect guesses which you can get with the length of the incorrect list `len(incorrect)`.

9. Now you can see that the hangman is getting printed out over an over and it looks kind of messy. Lets clear our console after every loop. You can do this by at the top of your file importing the os library:
```import os```
And then at the end of your while loop (still inside of it) adding the following line of code:
```
os.system('clear')
```

10. Now we need to write a function that will print out the current answer (blank spaces if letters have not been guessed). Make a function called `print_answer` and have it take in an answer and a list of correct guesses as arguments. Create a empty string variable called `output` that we'll eventually print out. Loop over the answer word with `for letter in answer:`. Use an if/else statement to check if the letter is in the correct list with `if letter in correct:`. If it is add the current letter to the output with `output += letter` if it's not in the list, put a blank space with `output += '_'`. After your for loop print out your output with `print('\nAnswer: '+output+'\n')`. The `\n` characters will add some spacing. Now call the `print_answer` function you just made in your while loop, right after the draw_hangman function.




