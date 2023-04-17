import pandas as pd

# Read the data into a pandas dataframe
data = pd.read_csv("data.csv")

# Create new columns to count the number of statements and reasons for each individual
data["num_statements"] = data.iloc[:, 4:].count(axis=1)
data["num_reasons"] = data["total_reasons"]

# Create a leaderboard for the number of statements
statement_leaderboard = data.sort_values(by=["num_statements"], ascending=False)[["name", "num_statements"]]

# Create a leaderboard for the number of reasons
reason_leaderboard = data.sort_values(by=["num_reasons"], ascending=False)[["name", "num_reasons"]]

# Print the leaderboards
print("Statement leaderboard:")
print(statement_leaderboard)

print("\nReason leaderboard:")
print(reason_leaderboard)
