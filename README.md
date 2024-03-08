```python
# This code defines a simple game where players take turns choosing numbers
# from a list. The goal is to achieve a sum of 15 with a combination of three
# chosen numbers. Players alternate turns until one player achieves the goal
# or no more numbers are available.

def display_board(numbers):
    print("Available numbers:", numbers)

def is_game_over(numbers, player_choices):
    if len(numbers) == 0:
        print("It's a draw! No player achieved 15.")
        return True
    for player_choice in player_choices:
        if len(player_choice) >= 3:
            # Check all possible combinations of three numbers
            for a in range(len(player_choice)):
                for b in range(a+1, len(player_choice)):
                    for c in range(b+1, len(player_choice)):
                        if player_choice[a] + player_choice[b] + player_choice[c] == 15:
                            print("Player", player_choices.index(player_choice) + 1, "wins!")
                            return True
    return False

def player_turn(player_choices, numbers, player):
    player_choice = int(input("Player {} choose a number: ".format(player)))
    if player_choice not in numbers:
        print("Invalid choice. Try again.")
        return player_turn(player_choices, numbers, player)
    player_choices[player-1].append(player_choice)
    numbers.remove(player_choice)

def play_game():
    numbers = list(range(1, 10))
    player_choices = [[], []]
    while not is_game_over(numbers, player_choices):
        display_board(numbers)
        player_turn(player_choices, numbers, 1)
        if is_game_over(numbers, player_choices):
            break
        display_board(numbers)
        player_turn(player_choices, numbers, 2)

play_game()
```

