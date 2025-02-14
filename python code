import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import os

def matches_per_season():
    match_per_season = pd.DataFrame({'Season': ['2008', '2009', '2010', '2011', '2012', '2013', '2014', '2015', '2016', '2017', '2018', '2019', '2020'],
                                     'matches': [56, 57, 60, 73, 74, 76, 60, 59, 60, 59, 60, 60, 60]})
    colors = ['turquoise'] * len(match_per_season)
    colors[5] = 'crimson'
    plt.figure(figsize=(10, 6))
    plt.bar(match_per_season['Season'], match_per_season['matches'], color=colors)
    plt.title("Number of matches played in different seasons", fontsize=16)
    plt.xlabel("Season", fontsize=14)
    plt.ylabel("Count", fontsize=14)
    plt.xticks(rotation=45)
    plt.grid(True)
    plt.show()

def no_of_matches():
    colors = ['turquoise'] * len(played)
    colors[8] = 'crimson'
    plt.figure(figsize=(10, 6))
    plt.bar(played['Team Name'], played['Total Matches played'], color=colors)
    plt.title("Total number of matches played", fontsize=16)
    plt.xlabel("Team Name", fontsize=14)
    plt.ylabel("Count", fontsize=14)
    plt.xticks(range(len(played['Team Name'])), played['Team Name'], rotation=45, ha='right')
    plt.grid(True)
    plt.show()

def most_wins():
    colors = ['turquoise'] * 15
    colors[8] = 'crimson'
    plt.figure(figsize=(10, 6))
    plt.bar(played['Team Name'], played['Wins'], color=colors)
    plt.title("Total Win by teams", fontsize=26)
    plt.xlabel("Team Name", fontsize=14)
    plt.ylabel("Count", fontsize=14)
    plt.xticks(rotation=45, ha='right')
    plt.grid(True)
    plt.show()

def win_percentage():
    colors = ['turquoise'] * 15
    colors[-4] = 'crimson'
    plt.figure(figsize=(10, 6))
    plt.bar(played['Team Name'], played['% Win'], color=colors)
    plt.title("Win % by teams", fontsize=26)
    plt.xlabel("Team Name", fontsize=14)
    plt.ylabel("Count", fontsize=14)
    plt.xticks(rotation=45, ha='right')
    plt.grid(True)
    plt.show()

def comparison():
    available_teams = [
        'Chennai Super Kings', 'Delhi Capitals', 'Delhi Daredevils', 'Kings XI Punjab',
        'Kolkata Knight Riders', 'Mumbai Indians', 'Rajasthan Royals', 'Royal Challengers Bangalore',
        'Sunrisers Hyderabad', 'Deccan Chargers', 'Pune Warriors India', 'Gujarat Lions',
        'Rising Pune Supergiants', 'Kochi Tuskers Kerala'
    ]
    print("Available teams:")
    for i, team in enumerate(available_teams, start=1):
        print(f"{i}. {team}")
    team1_index = int(input("Select the first team (Enter the corresponding number): ")) - 1
    team2_index = int(input("Select the second team (Enter the corresponding number): ")) - 1
    team1 = available_teams[team1_index]
    team2 = available_teams[team2_index]
    team_wins = played.set_index('Team Name')['Wins']
    team1_wins = team_wins.loc[team1]
    team2_wins = team_wins.loc[team2]
    all_teams_wins = np.array([team1_wins, team2_wins])

    plt.figure(figsize=(2, 5))
    plt.bar([team1, team2], all_teams_wins, color=['turquoise', 'crimson'])
    plt.title("Comparison between " + team1 + " and " + team2, fontsize=16)
    plt.xlabel("Teams", fontsize=14)
    plt.ylabel("Wins", fontsize=14)
    plt.grid(True)
    plt.show()

def player_stats():
    try:
        filt = (deliveries_data['batter'] == 'V Kohli')
        df_kohli = deliveries_data[filt]

        print(len(df_kohli[df_kohli['batsman_runs'] == 4]))
        print(len(df_kohli[df_kohli['batsman_runs'] == 6]))
        print(df_kohli['total_runs'].sum())
        values = df_kohli['dismissal_kind'].value_counts()

        labels = values.index
        plt.figure(figsize=(8, 8))
        plt.pie(values, labels=labels, autopct='%1.1f%%', startangle=150)
        plt.title('Dismissal Type', fontsize=15)
        plt.show()
    except KeyError as e:
        print(f"KeyError: {e}. Please check if the column names are correct in the deliveries_data DataFrame.")

def most_wickets():
    dismissal_kinds = ['caught', 'bowled', 'lbw', 'caught and bowled', 'stumped', 'hit wicket']
    hwt = deliveries_data[deliveries_data["dismissal_kind"].isin(dismissal_kinds)]
    bo = hwt['bowler'].value_counts()
    colors = ['turquoise'] * 10
    colors[0] = 'crimson'
    plt.figure(figsize=(10, 6))
    plt.bar(bo[:10].index, bo[:10], color=colors, edgecolor='black')
    plt.title('Leading wicket-takers', fontsize=26)
    plt.xlabel('Bowler')
    plt.ylabel('Total Wickets')
    plt.xticks(rotation=45, ha='right')
    plt.tight_layout()
    plt.show()

def mom_awards():
    colors = ['turquoise'] * 10
    colors[0] = 'crimson'
    top_players = match_data['player_of_match'].value_counts()[:10]
    plt.figure(figsize=(10, 6))
    plt.bar(top_players.index, top_players.values, color=colors, edgecolor='black')
    plt.title('Top 10 Players of the Match Awardees', fontsize=26)
    plt.xlabel('Players')
    plt.ylabel('Count')
    plt.xticks(rotation=45, ha='right')
    plt.tight_layout()
    plt.show()

def menu():
    print("Select an option:")
    print("1. Matches per Season")
    print("2. Total Matches Played by Each Team")
    print("3. Total Wins by Each Team")
    print("4. Win Percentage by Each Team")
    print("5. Comparison Between Two Teams")
    print("6. Player Stats")
    print("7. Most Wickets")
    print("8. Most Player of the Match Awards")
    print("9. Exit")

    choice = input("Enter your choice (1-9): ")

    if choice == '1':
        matches_per_season()
    elif choice == '2':
        no_of_matches()
    elif choice == '3':
        most_wins()
    elif choice == '4':
        win_percentage()
    elif choice == '5':
        comparison()
    elif choice == '6':
        player_stats()
    elif choice == '7':
        most_wickets()
    elif choice == '8':
        mom_awards()
    elif choice == '9':
        print("Exiting the program...")
        return
    else:
        print("Invalid choice. Please enter a number from 1 to 9.")
    menu()

desktop_path = os.path.expanduser("~/Desktop")  # Get the path to the desktop

for dirname, _, filenames in os.walk(desktop_path):
    for filename in filenames:
        print(os.path.join(dirname, filename))

deliveries_data = pd.read_csv(r'/content/deliveries.csv')
match_data = pd.read_csv(r'/content/matches.csv')

print("Data ready for exploration")
print('Total Matches Played:', match_data.shape[0])
print(' \n Venues Played At:', match_data['city'].unique())
print(' \n Teams :', match_data['team1'].unique())
colors = ['turquoise'] * 13
colors[5] = 'crimson'
matches_played_byteams = pd.concat([match_data['team1'], match_data['team2']], axis=1)
teams = (matches_played_byteams['team1'].value_counts() + matches_played_byteams['team2'].value_counts()).reset_index()
teams.columns = ['Team Name', 'Total Matches played']
teams.sort_values(by=['Total Matches played'], ascending=False).reset_index().drop('index', axis=1).style.background_gradient(cmap='PuBu')

wins = pd.DataFrame(match_data['winner'].value_counts()).reset_index()
wins.columns = ['Team Name', 'Wins']
wins.style.background_gradient(cmap='PuBu')

played = teams.merge(wins, left_on='Team Name', right_on='Team Name', how='inner')
played['% Win'] = (played['Wins'] / played['Total Matches played']) * 100
played.sort_values(by=['% Win'], ascending=False).reset_index().drop('index', axis=1).style.background_gradient(cmap='PuBu', subset=['% Win'])

menu()
