# Analyzing UEFA Championship

Project snapshots:

![image](https://github.com/20100215/Analyzing_Football_Matches/assets/84717650/f266eda9-1fce-4f52-b285-65e0ad07204d)

![image](https://github.com/20100215/Analyzing_Football_Matches/assets/84717650/2ecd64ac-e665-4ac9-bc65-9fdbeabef8e0)

![image](https://github.com/20100215/Analyzing_Football_Matches/assets/84717650/44c01605-43e1-406b-9bbd-28a550810a9c)

![image](https://github.com/20100215/Analyzing_Football_Matches/assets/84717650/6d55cded-a38f-4d44-81c0-53ce6b417140)

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

6. Additional data ingestion (Kaggle dataset)
    - Import the UEFA > Matches > Euro folder, then combine the CSVs (separated by years)
    - In Power Query editor, keep the following columns - Source.Name, id_match, home team, away team, home team code, away team code, home score. away score, home penalty, away penalty, home score total, away score total, winner, win reason, year, group name, match day name, type, round, round mode, match attendance, stadium country, stadium city, stadium name
7. Additional data manipulation
    - Add numeric column for total goals for all matches
    - Add boolean columns for checking if the host team was playing in the match and whether or not the host team has won the match.
    - Add numeric column for absolute difference of team scores in matches.
7. Additional data visualization
    - Line and stacked column chart for number of matches per year and average of match attendance as line y-axis.
    - Add a column color legend for stadium_country_code, and tooltip for count of stadium_country_code
    - Line and stacked column chart for Total Goals and Avg Goals Per Game by year

Insights:

    - Dashboard is able to:
        - summarize cumulative statistics (games played, wins, losses, draws, tournament appearances, win rate) for a team, filterable by team, debut, and best results.
        - Analyze trends for total and average goals as well as number of matches and match attendance by year, filterbale by round mode and whether the matches involved the hosting team or not.
    - Teams with smaller win rate show an increasing trend of goals conceded, suggesting that they might lack defensive capabilities, regardless of the number of goals they have scored on their own.
    - Germany is the most participative team with 14 tournaments, while 7 teams only had 1 participation.
    - More matches playing as the years progress, from just 4-5 matches in the 1960s to 51 in 2024. In 1968, there are 5 games as opposed to 4 games in the past 2 and next 2 tournaments, this is because there was no penalties back then and the final game was replayed. 1980 was the year group stages are introduced, allowing more games to exist.
    - The average match attendance do not exhibit a specific trend when analyzed by year. Rather, this more likely varied based on the host country. (France and Germany hosted matches have the most attendances).
    - Games where the host country is not playing (e.g. in 2020 - Sweden vs Ukraine played in Scotland - only less than 10,000 attendees)
    - No significant trend for average goals per game across years, though it began with several fluctuations in the 1960s then stabilized at around 2.5 goals per game starting 2000 onwards.
    - There is an increase in the number of total goals across the years, which is growing at a similar rate to the number of matches across the years.
    - There is not much variation in the average total goals when filtered by round type (2.34 for group, 2.74 for knock outs, and 2.41 for final - 2.44 all matches), however, there is an increase in the average score difference in matches across the stages (1.19 for group, 1.31 for knock outs, and 1.35 for final - 1.23 all games).
    - There is a clear increasing trend for average match attendance by round mode (37.39k for group stage, 41.44k for knock outs, 53.68k for final - 39.05k all games). The overall average attendance is higher for matches with the host team playing (either home or away - 43.06k) compared to matches where the host team is not playing (37.79k). The difference of average total goals filtered by the presence/absence of the host team is insignificant (2.48 with home team playing and 2.42 for home team not playing)

        
