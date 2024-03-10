import divoom

# Initialize the display
display = divoom.DivoomDevice("YOUR_DEVICE_MAC_ADDRESS")

# Function to update the scoreboard
def update_scoreboard(scores):
    display.clear()
    display.draw_text((0, 0), f"Player 1: {scores[0]}", divoom.WHITE)
    display.draw_text((0, 8), f"Player 2: {scores[1]}", divoom.WHITE)
    display.draw_text((0, 16), f"Player 3: {scores[2]}", divoom.WHITE)
    display.draw_text((0, 24), f"Player 4: {scores[3]}", divoom.WHITE)
    display.update()

# Function to handle score updates
def update_score(player, scores):
    scores[player] += 1
    update_scoreboard(scores)

# Main function
def main():
    scores = [0, 0, 0, 0]  # Initialize scores for 4 players
    
    while True:
        print("Enter player number (1-4) to update score or 'q' to quit:")
        player_input = input()
        
        if player_input.lower() == 'q':
            break
        else:
            try:
                player = int(player_input) - 1
                if player >= 0 and player < 4:
                    update_score(player, scores)
                else:
                    print("Invalid player number!")
            except ValueError:
                print("Invalid input! Please enter a number (1-4) or 'q' to quit.")
    
    print("Exiting scoreboard...")

if __name__ == "__main__":
    main()
