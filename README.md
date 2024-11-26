# vosir-
висилица
import random

words = ["python", "javascript", "programming", "computer"]
word = random.choice(words)
guessed_letters = set()
incorrect_guesses = 0
max_incorrect_guesses = 6

while incorrect_guesses < max_incorrect_guesses:
    display_word = ""
    for letter in word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print(display_word)
    print(f"Incorrect guesses remaining: {max_incorrect_guesses - incorrect_guesses}")

    guess = input("Guess a letter: ").lower()

    if guess in guessed_letters:
        print("You already guessed that letter!")
        continue

    guessed_letters.add(guess)

    if guess in word:
        if all(letter in guessed_letters for letter in word):
            print("Congratulations! You win!")
            break
    else:
        incorrect_guesses += 1
        print("Incorrect guess.")

else:
    print(f"You lose! The word was {word}")
