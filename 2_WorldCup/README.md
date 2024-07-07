# Analyzing World Cup Data

Project snapshots:

(To be uploaded)

Data sources:

- [World Cup Dataset - 5 of 27 CSVs](https://github.com/jessxahmet/live-training-exploring-world-cup-data-in-power-bi/tree/main/Datasets)
- [Original Full Dataset Source by Fjelstul](https://github.com/jfjelstul/worldcup)

Key Questions:

- Which country scored the most goals?
- Which country had the most finals appearances?
- Which ear did teams score the most goals?
- Is there an advantage for the host country?

Inspired from the code along from DataCamp, with additional twists performed: [https://www.datacamp.com/code-along/live-training-exploring-world-cup-data-power-bi](https://www.datacamp.com/code-along/live-training-exploring-world-cup-data-power-bi)

Steps executed:

1. Data preparation:
    - Load the five CSV files -> goals, matches, team_appearances, teams, tournaments
2. Data modelling:
    - matches 1 ->- * goals
    - tournaments 1 ->- * goals
    - teams 1 ->- * goals
    - tournaments 1 ->- * matches
    - teams 1 ->- * team_appearances
    - matches 1 ->- * team_appearances
    - tournaments 1 ->- * team_appearances
3. Additional measures:
    - `Total Tournaments = DISTINCTCOUNT(tournaments[tournament_id])`
    - `Total Host Wins = SUM(tournaments[host_won])`
    - `% Host Wins = DIVIDE([Total Host Wins], [Total Tournaments], 0)` - percentage, 1 decimal place
    - `Finals Reached = CALCULATE(DISTINCTCOUNT(team_apperances[key_id]), team_apperances[stage_name] = "Final")` - filters the count of teams appearing in the final stage
4. Additional columns:
    - `final_result = matches[home_team_score] & '-' & matches[away_team_score]` - Final score in the matches table to combine the home team score and away team score
5. Visualizations:
    - Prepare the following custom visuals:
        - Sankey 3.4.2.0
        - Timeline Storyteller ver2.0.5
        - Box and Whisker Chart by DataScenarios
        - Enlighten World Flags
    - Cards for total tournaments and host win rate
    - Clustered column chart for finals appearances by team code. Add tooltip for team name.
    - Box and whisker chart for count of goals per match grouped by year. Sort chart by year ascending.
    - Bar chart for number of goals by team.
    - Map for number of matches per city. Change the map style to light. Add category labels to show the city names.
        - Create a tooltip that will be used in the map bubbles. Add a new page and in the canvas settings, set type to tooltip. Add card for city name then add a table showing match names and the calculated column for final score.
        - Apply the tooltip in the map visual.
6. Dashboard Enhancements
    - Page navigator
        - Apply and style the navigator: Make the grid style vertical and enlarge the font sizes.


Insights:
    - The total tournaments measure is used as part of the analysis for validating where there is an advantage of the host team. 
    - Total host wins is only 28.6%, suggesting some advantage.
    - Germany had the most number of finals appearances (8), followed by Brazil and Italy (6).
    - Note that in 1958, it was the only time where there were 4 teams that entered the final round which was played like the "Group stage" mechanic. Here, Brazil won by the most wins in that group round, therefore Brazil was recorded with 7 finals appearances in Wikipedia, contrary to 6 in this dashboard.
    - Note that due to the data design, goal records are stored row by row in a table, therefore using the goals table for analysis will not reflect matches with 0 goals.
    - There is a slight decreasing trend of the number of goals scored per match across years in the tournament.

    - The per tournament page displays the host country, the top teams according to total goals scored, and a map showing the distribution of matches with a tooltip listing the matches and scores.
    - There are evidences of homecourt advantage in some years. For instances, in the 1950 world cup, Brazil was the host country and is also the team that scored the most goals (25), with Uruguay following next (15).
