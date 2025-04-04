import matplotlib.pyplot as plt

def cricket_comparison_graph_average():
    """
    Creates a combined bar and line graph comparing the average scores of two cricket games.
    """

    overs = list(range(1, 21))  # Overs 1 to 20
    game1_scores = []
    game2_scores = []
    game1_averages = []
    game2_averages = []

    print("Enter scores for Game 1:")
    for over in overs:
        while True:
            try:
                score = int(input(f"Game 1, Over {over}: "))
                game1_scores.append(score)
                game1_averages.append(sum(game1_scores) / len(game1_scores)) #calculate the average
                break
            except ValueError:
                print("Invalid input. Please enter an integer.")

    print("\nEnter scores for Game 2:")
    for over in overs:
        while True:
            try:
                score = int(input(f"Game 2, Over {over}: "))
                game2_scores.append(score)
                game2_averages.append(sum(game2_scores) / len(game2_scores)) #calculate the average
                break
            except ValueError:
                print("Invalid input. Please enter an integer.")

    plt.figure(figsize=(14, 7))

    # Bar graphs (total scores)
    bar_width = 0.35  # Adjust width for better visibility
    plt.bar(overs, game1_scores, color='skyblue', label='Game 1 (Scores)', width=bar_width, alpha=0.7)
    plt.bar([x + bar_width for x in overs], game2_scores, color='lightcoral', label='Game 2 (Scores)', width=bar_width, alpha=0.7)

    # Line graphs (average scores)
    plt.plot(overs, game1_averages, color='blue', marker='o', linestyle='-', label='Game 1 (Average)')
    plt.plot(overs, game2_averages, color='red', marker='o', linestyle='-', label='Game 2 (Average)')

    plt.xlabel("Overs")
    plt.ylabel("Runs Scored / Average Runs")
    plt.title("Cricket Score & Average Comparison: Game 1 vs. Game 2")
    plt.xticks(overs)
    plt.grid(True, linestyle='--', alpha=0.6)
    plt.legend()
    plt.tight_layout()
    plt.show()

# Run the function
cricket_comparison_graph_average()
