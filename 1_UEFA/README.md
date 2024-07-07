# Analyzing UEFA Championship

Data sources:

- [Records and Statistics - Wikipedia](https://en.wikipedia.org/wiki/UEFA_European_Championship_records_and_statistics)
- [Football - Soccer - UEFA EURO, 1960-2024 - Kaggle](https://www.kaggle.com/datasets/piterfm/football-soccer-uefa-euro-1960-2024)

Tasks Summary:

- Load data from different sources
- Clean and prepare data for analysis
- Transform and manipulate data to add missing variabes
- Gain insights into the statistics of the European championships

Inspired from the code along from DataCamp: [https://www.linkedin.com/events/7214981149763252224/](https://www.linkedin.com/events/7214981149763252224/)

Snapshot of the Wikipedia data source upon execution of this project:
![image](https://github.com/20100215/Analyzing_Football_Matches/assets/84717650/3c55bf4a-a018-4206-a511-ff1bfce216ac)


Steps executed:

1. Import data from Web
    - Copy the given Wikipedia URL
    - Select the tables: Ranking of teams by number of appearances, debut of national teams, overall team records, hosts, results of host nations
2. Cleaning the tables (Power Query Editor)
    - Ranking of teams
        - Remove the [ ] after country names
        - Split best result by delimiter (
        - Remove ) in the last column
        - Change Most Recent and Debut column to text instead of number
    - Debut of national teams
        - Use first row as headers
        - Rename debuting_teams columns (originally a splitted column)
        - Remove top row
    - Overall team records
        - Use first row as headers
        - Remove the [ ] after country names
    - Hosts
        - Fill down in first column
        - Remove the [ ] after country names and years
    - Results in host nations
        - Fill down in first column
        - Filter out years 2024, 2028, and 2032
3. Data modelling
    - Relationships:
        - Add a 1:1 relationship between Overall team records[team] and Hosts[nation]
        - Add a 1:* relationship between Overall team records[team] and Result of host nations[Host nation]
4. Table view
    - Overall team records
        - Add a win rate column as percentage
        - Add games per tournament and wins per tournament with 2 decimal places
        - Add goals scored per game and goals conceded per game
5. Data visualization
    - Goals scored, conceded per game, and win rate by team - line and clustered column chart with secondary y-axis enabled
    - Number of tournament participations with data labels. Apply top 10 filtering based on sum of Part.
    - Cards for sum of wins, sum of tournament participations and games played
    - Cards for first debut, most recent appearance, and team best result
    - Slicer for debut years and best results without blank. Edit interactions to none instead of filter for the other slicers.

Insights:
    - Teams with smaller win rate show an increasing trend of goals conceded, suggesting that they might lack defensive capabilities, regardless of the number of goals they have scored on their own.
    - Germany is the most participative team with 14 tournaments, while 7 teams only had 1 participation.
    - Dashboard is able to summarize cumulative statistics for a team, filtered by team, debut, and best results.
        