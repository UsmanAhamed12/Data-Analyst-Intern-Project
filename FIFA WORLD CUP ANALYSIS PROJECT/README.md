# FIFA World Cup Analysis Project

## Overview

The FIFA World Cup is one of the most celebrated sporting events globally, held every four years and showcasing the pinnacle of football talent from nations around the world. Behind the excitement and passion of the games lies the often-overlooked work of data analysts who provide fans with crucial insights into every match, team, and player. This project seeks to shine a light on these unsung analysts and their contributions, uncovering the data-driven story of the World Cup.

## Project Objectives

Using historical World Cup data, including match results and tournament statistics, this analysis explores key metrics and factors that may influence a World Cup victory. The project combines data from:

1. **WorldCups Dataset** - A historical record of all tournaments, capturing details such as the year, host country, winning team, total goals, teams, and matches played.
2. **WorldCupMatches Dataset** - Information on individual match outcomes, including teams, scores, and match conditions.
3. **WorldCupPlayers Dataset** - Player and lineup details for each match, covering player positions, events, and coaches.

By analyzing these datasets, the project aims to identify patterns, trends, and important factors contributing to success in the World Cup. The findings will offer insights for football fans and highlight the role of data analysts in delivering meaningful answers to fans' questions, adding depth to the narrative of each World Cup.

---


# The Analysis

## 1. Average goals per match

To answer the question, “What is the average number of goals scored per match in the FIFA dataset?” I created a new column called total_goals_per_match based on the existing Home Team Goals and Away Team Goals columns. This column combines the goals scored by both teams in each match, making it easier to analyze the overall goal-scoring trend.

Using the mean of this total_goals_per_match column, I calculated the average number of goals scored per match across all matches in the dataset. This approach highlights the scoring patterns within matches and provides insights into the general level of competitiveness and excitement in World Cup games. By focusing on average goals per match, this analysis can help fans and analysts understand trends in goal-scoring across different tournaments.

This analysis offers a foundational metric for exploring factors that contribute to high-scoring games and can guide future assessments of offensive and defensive strategies employed by teams in the World Cup.


## Visualize Data

``` python


Total_gols_per_match = Data['Away Team Goals'] + Data['Home Team Goals']

Avg_gl_pr_mch = Total_gols_per_match.mean()

result = int(Avg_gl_pr_mch)

print(f'Average Goals Per Match is {result}')


```


## Results

Average Goals Per Match is 2

## Insights

1. Balanced Competition: With an average of 2 goals per match, World Cup games tend to be competitive, reflecting strong defensive and tactical gameplay.

2. Decisive Goals: Each goal holds high value, often being decisive in match outcomes, adding to the suspense and strategic depth of each game.

3. Evolution of Play Styles: This metric allows for comparisons over time, highlighting shifts in offensive and defensive strategies across different tournaments.

4. Strategic Implications: Teams aiming for success may target strategies that allow them to consistently exceed this average, improving their chances in critical matches.



## 2. Home And Away Win Rates

To answer the question, “What are the win rates for home teams, away teams, and draws in FIFA World Cup matches?” I analyzed match outcomes by comparing goals scored by the home and away teams. I categorized each match as a home win, away win, or draw to simplify the analysis.

Using these categories, I calculated the proportion of each outcome across all matches, providing insights into the likelihood of a home or away victory versus a draw. This approach highlights how match location impacts win rates and gives an overview of the balance between home advantage and competition intensity.

This analysis offers a data-driven perspective on match outcomes, helping fans and analysts understand trends in home and away team performance, as well as the frequency of draws. This insight can support further exploration of factors that contribute to home-field advantage or parity in World Cup games.


## Visualize Data

``` python


df = Data[['Home Team Goals','Away Team Goals']]


# Calculate the number of home wins, away wins, and draws
home_wins = (df['Home Team Goals'] > df['Away Team Goals']).sum()
away_wins = (df['Away Team Goals'] > df['Home Team Goals']).sum()
draws = (df['Home Team Goals'] == df['Away Team Goals']).sum()
total_matches = len(df)

# Data for pie chart
labels = ['Home Wins', 'Away Wins', 'Draws']
sizes = [home_wins, away_wins, draws]
colors = ['#4CAF50', '#FF9800', '#03A9F4']  # Custom colors
explode = (0.1, 0.1, 0)  # Explode the Home and Away Wins

# Plotting the pie chart
plt.figure(figsize=(6, 6))
plt.pie(sizes, explode=explode, labels=labels, colors=colors, 
        autopct='%1.1f%%', shadow=True, startangle=140)
plt.title('Home vs Away Win Rates', fontsize = 15)
plt.show()


```


## Results

![alt text](image.png)


## Insights

1. Home Advantage: The majority of matches, 57.3%, resulted in home wins, indicating a strong home-field advantage in the FIFA World Cup.

2. Balanced Competition: Away wins account for 20.5% of matches, showing that while home advantage exists, away teams still perform competitively.

3. Draw Frequency: Draws occurred in 22.2% of matches, reflecting a relatively balanced level of competition and parity among teams.





