import random

def single_game():
    target = random.randint(1, 100)
    attempts = 0
    print("I picked a number between 1 and 100. Try to guess it!")

    while True:
        guess = input("Your guess (press 'q' to quit): ").strip()
        if guess.lower() == 'q':
            print("You quit the game. The correct number was:", target)
            return False
        if not guess.isdigit():
            print("Please enter a number between 1 and 100 or 'q' to quit.")
            continue

        guess = int(guess)
        attempts += 1

        if guess < 1 or guess > 100:
            print("The number must be between 1 and 100.")
        elif guess < target:
            print("Go higher!")
        elif guess > target:
            print("Go lower!")
        else:
            print(f"Congratulations! You guessed it in {attempts} tries. The number was {target}.")
            return True

def game_loop():
    while True:
        play_again = single_game()
        if play_again is False:
            break
        again = input("Do you want to play again? (y/n): ").strip().lower()
        if again != 'y':
            print("Thanks for playing! Goodbye.")
            break

if __name__ == "__main__":
    game_loop()
