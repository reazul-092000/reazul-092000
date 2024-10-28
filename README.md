import random

# Initializing win counters for the user and computer
user_wins = 0
computer_wins = 0

# Options for the game
options = ["rock", "paper", "scissors"]

# Game loop
while True:
    # Prompt user for input
    user_input = input("Type Rock/Paper/Scissors or Q to quit: ").lower()
    if user_input == "q":
        break  # Exit if user wants to quit
    
    # Ensure input is valid
    if user_input not in options:
        print("Invalid input. Please choose Rock, Paper, or Scissors.")
        continue

    # Randomly pick a move for the computer
    random_number = random.randint(0, 2)
    computer_pick = options[random_number]
    print("Computer picked", computer_pick + ".")

    # Check for a tie
    if user_input == computer_pick:
        print("It's a TIE! You both picked", user_input + ". Try again!")
        continue  # Skip to the next round if it's a tie

    # Check who wins
    if user_input == "rock" and computer_pick == "scissors":
        print("You CRUSHED the computer's scissors with your rock! Victory!")
        user_wins += 1

    elif user_input == "paper" and computer_pick == "rock":
        print("You WRAPPED up the computer's rock with your paper! Victory!")
        user_wins += 1

    elif user_input == "scissors" and computer_pick == "paper":
        print("You SLICED through the computer's paper with your scissors! Victory!")
        user_wins += 1

    else:
        print("The computer outmaneuvered you! You lost this round.")
        computer_wins += 1

    # Adding intensity for winning streaks
    if user_wins > 0 and user_wins % 3 == 0:
        print("🔥 You're on a roll! That's three wins in a row! 🔥")

# Epic end game summary
print("\n--- GAME OVER ---")
print(f"Total Wins: You won {user_wins} times. The computer won {computer_wins} times.")
if user_wins > computer_wins:
    print("🏆 Congratulations! You are the ultimate rock-paper-scissors champion! 🏆")
elif user_wins < computer_wins:
    print("Better luck next time. The computer claimed victory this time.")
else:
    print("It's a tie! You and the computer are evenly matched.")
print("Goodbye, and thanks for playing!")
