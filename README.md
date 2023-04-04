## T20-World-Cup-Data-Analysis

## Code Description

This Python code reads data from multiple JSON files containing T20 World Cup cricket match results and batting summaries. It processes the data to create a Pandas DataFrame with columns for match ID, team names, player names, runs scored, balls faced, and whether the player was dismissed or not. It then cleans up the data by removing special characters and replacing them with appropriate values. Finally, it exports the cleaned DataFrame to a CSV file.

## Code

import pandas as pd
import json

# Read match results JSON file and create DataFrame
with open(r'C:\Users\nachi\Desktop\json file\t20_json_files\t20_wc_match_results.json') as f:
    data=json.load(f)

    df_match =pd.DataFrame(data[0]['matchSummary'])

# Read batting summary JSON file and create DataFrame
with open(r'C:\Users\nachi\Desktop\json file\t20_json_files\t20_wc_batting_summary.json') as f:
    data=json.load(f)

    all_records = []

    for rec in data:
        all_records.extend(rec['battingSummary'])

    df_batting=pd.DataFrame(all_records)

# Rename match ID column and create dictionary to map team names to match IDs
df_match.rename({'scorecard':'match_id'}, axis = 1, inplace = True)

match_ids_dict={}

for index, row in df_match.iterrows():
    key1 = row['team1'] +' Vs '+row['team2']
    key2 = row['team2'] +' Vs '+row['team1']
    
    match_ids_dict[key1] = row["match_id"]
    match_ids_dict[key2] = row["match_id"]

# Add columns for dismissal and match ID, and clean up player names
df_batting["out/not_out"]=df_batting.dismissal.apply(lambda x: "out" if len(x)>0 else "not_out")
df_batting['batsmanName'] = df_batting['batsmanName'].apply(lambda x: x.replace('â€',''))
df_batting['batsmanName'] = df_batting['batsmanName'].apply(lambda x: x.replace('\xa0',''))
df_batting["match_id"] = df_batting["match"].map(match_ids_dict)

# Remove dismissal column and export DataFrame to CSV
df_batting.drop(columns=["dismissal"], inplace=True)
df_batting.to_csv(r'C:\Users\nachi\Desktop\json file\t20_json_files\t20_wc_batting_summary.json', index = False)
