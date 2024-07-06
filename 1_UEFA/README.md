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
        - Add a 1:* relationship between Hosts[nation] and Result of host nations[Host nation]