# T20 World Cup Match Data Processing
This code processes data from T20 World Cup cricket matches, specifically batting and bowling summaries. The data is provided in JSON format and is stored in local files. The code uses the pandas library for data manipulation and json module for loading JSON data.

## Getting Started

1. Clone the repository to your local machine.
2. Navigate to the root directory of the project.
3. Create a folder named "json file" in your Desktop.
4. Add the T20 World Cup match data files to the "json file" folder. These files are:
- t20_wc_match_results.json
- t20_wc_batting_summary.json
- t20_wc_bowling_summary.json

5. Install the necessary libraries by running the following command:
pip install pandas

6. Run the script in your preferred IDE or from the command line using the following command:
python T20_World_Cup_Data_Processing.py

## Code Description

The code is divided into multiple sections, each section responsible for processing a specific data file.

### Match Results Data
The first section of the code processes the match results data. It reads the data from the "t20_wc_match_results.json" file, extracts the match summary information, and creates a pandas dataframe. The resulting dataframe contains the match id, team names, venue, and match outcome.

### Batting Summary Data
The second section of the code processes the batting summary data. It reads the data from the "t20_wc_batting_summary.json" file, extracts the batting summary information for each match, and creates a pandas dataframe. The resulting dataframe contains the match id, batsman name, runs scored, balls faced, and other relevant statistics. The code also maps the match id from the match summary dataframe to the batting summary dataframe using a dictionary.

### Bowling Summary Data
The third section of the code processes the bowling summary data. It reads the data from the "t20_wc_bowling_summary.json" file, extracts the bowling summary information for each match, and creates a pandas dataframe. The resulting dataframe contains the match id, bowler name, number of overs bowled, runs conceded, wickets taken, and other relevant statistics. The code also maps the match id from the match summary dataframe to the bowling summary dataframe using a dictionary.

### Data Cleaning
The last section of the code performs some data cleaning operations on the batting and bowling summary dataframes. It removes unwanted columns, renames columns, and converts data types. It also removes any special characters from the batsman and bowler names.

### Saving Data
The cleaned dataframes are then saved as CSV files in the same "json file" folder where the input files are stored.
