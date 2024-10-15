# Tabletop Game Recommendation Engine

## Overview
This is a personal project, where I developed a board game recommendation engine using content-based filtering. This project was created to enhance my skills in ETL, EDA, and text processing, as well as providing a recommendation engine for exploration of new table top games to play.

This is for anyone interested in exploring potential boardgames, card games, or any other physical game played on a tabletop to play, based on an existing game you already like. 

This uses data from Board Game Geek (BGG), which was extracted from their public ranked board game dataset and server. I applied initial filters to restrict game recommendations to base games that have an average rating of 7/10 or higher and received at least 100 votes to ensure the recommendations are relevant and trustworthy.

## Repository Structure
### Code 
This folder contains all the code used in the project. 
The functional code is in .ipynb format and can be accessed using Jupiter Notebook, it also contains a contents file which details the order and function of each code file. 

### Data
This folder contains all the data used in the project.
The raw data is extracted from Board Game Geek website, in the form of a downloadable .csv file and from their public server which was accessed through an API.
There is also a file describing the metadata for each of the stored .csv files.  

## How to use
There are separate code files, each performing a stage of the project, which can be run in Jupiter Notebook.  
Each code file imports a specific .csv file (which could be created from a previous stage) and can be updated and run individually.  
The order refers to the order I performed each stage of the project and can be followed if new data from BGG is utilised.
A breakdown of the required data input and code output is below:  

| Order | Data Input (.csv)  | Code file (.ipynb)  | Data Output (.csv) |
|-----------|-----------|-----------|-----------|
| 1 | boardgames_ranks | BGG_Ranked_Games_EDA | games_ranks_updated |
| 2 | games_ranks_updated | BGG_Game_Data_Extraction | games_filtered |
| 3 | games_filtered | BGG Game Data EDA | (none) |
| 4 | games_filtered | BGG_Data_Cleaning | games_clean |
| 5 | games_clean | BGG_Data_Feature_Engineering | games_fe |
| 6 | games_fe | Tabletop_Game_Recommendation | (none) |

## Interesting Findings
- 155634 games on BGG website, and include ancient games such as Senet (about 3000 BCE)
- Original ranked dataset from BGG includes game accessories and future games up to 2028
- 1278 versions of Monopoly exist
- Extreme values – 35 games had +99 max players
- Average rating for games with >=100 ratings is 6.9 / 10
- Only 17% of games have an overall rank

## Further work
- User interface (input prompts, include pictures & possibly descriptions)
- Calculate the similarity scores for each key term category (e.g. mechanism) and use weights to enable preferences
- Output metrics on similarity  /  success of suggested game considering test scenarios (e.g. travelling on a plane)
- Investigate difference between good and bad votes
- Try to label more non-base games to enable genuine suggestion of base games (or possibly expansions in future)
- Explore feature engineering the different labels into suitable clusteres to reduce unique label size
- Compare with the other board game recommendation engines

