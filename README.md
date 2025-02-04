# Hanging-man-game

import random

def choose_word():
    words = ["python", "hangman", "developer", "programming", "challenge"]
    return random.choice(words)

def display(word, guessed_letters):
    return " ".join([letter if letter in guessed_letters else "_" for letter in word])

def hangman():
    word = choose_word()
    guessed_letters = set()
    attempts = 6

    print("Welcome to Hangman!")
    while attempts > 0:
        print("\nWord:", display(word, guessed_letters))
        guess = input("Guess a letter: ").lower()

        if guess in guessed_letters:
            print("You already guessed that letter.")
        elif guess in word:
            guessed_letters.add(guess)
            print("Correct guess!")
        else:
            guessed_letters.add(guess)
            attempts -= 1
            print(f"Wrong guess! Attempts left: {attempts}")

        if all(letter in guessed_letters for letter in word):
            print("\nCongratulations! You guessed the word:", word)
            break
    else:
        print("\nGame Over! The word was:", word)

if __name__ == "__main__":
    hangman()
