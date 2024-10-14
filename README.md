# Tabletop Game Recommendation Engine

## Overview
This is a personal project, where I developed a board game recommendation engine using content-based filtering. This project was created to enhance my skills in ETL, EDA, and text processing, as well as providing a recommendation engine for exploration of new table top games to play.

This is for anyone interested in exploring potential boardgames, card games, or any other physical game played on a tabletop to play, based on an existing game you already like. 

This uses data from Board Game Geek, which was extracted using their public ranked board game dataset and API. I applied initial filters to restrict game recommendations to base games that have an average rating of 7/10 or higher and received at least 100 votes to ensure the recommendations are relevant and trustworthy.

## File Manifest
### Code 
This folder contains all the code used in the project. 
The functional code is in .ipynb format and can be accessed using Jupiter Notebook, it also contains a contents file which details the order and function of each code file.


### Data
This folder contains all the data used in the project.
The raw data is extracted from Board Game Geek website, in the form of a downloadable .csv file and from their public server which was accessed through an API.
There is also a file describing the metadata for each of the stored .csv files.


Each code processes a data input into a data output, meaning each stage can be updated indiviudally.
A breakdown of the required data input and code output is below:  

| Data Input (.csv)  | Code file (.ipynb)  | Data Output (.csv) |
|-----------|-----------|-----------|
| boardgames_ranks | BGG_Ranked_Games_EDA | games_ranks_updated |
| games_ranks_updated | BGG_Game_Data_Extraction | games_filtered |
| games_filtered | BGG Game Data EDA | (none) |
| games_filtered | BGG_Data_Cleaning | games_clean |
| games_clean | BGG_Data_Feature_Engineering | games_fe |
| games_fe | Tabletop_Game_Recommendation | (none) |
