# Contents of Tabletop Game Recommendation code files

## 1. BGG Raw Ranked Games EDA
This explores the raw ranked game data (boardgames_ranked.csv) which can be directly downloaded from Board Game Geek:
https://boardgamegeek.com/data_dumps/bg_ranks

This main aim of this code is to identify which games to obtain further data for from the BGG server.

It explores the values and distributions of:
- The years in which the games are published
- The ratings given to the games
- The overall ranks of the games

It also looks at the different versions, editions, expansions and accessories present in the data.

## 2. BGG Data Data Extraction
This is focused on filtering the possible games to include in the recommendation engine, and extracting more game data from the BGG servers through their API. 

The filtering is necessary to reduce the amount of downloaded game data, the objectives of the filtering were to include games with:
- an average rating of 7 or above
- at least 100 ratings
- no game expansions

(note: some games were miss labelled as not being an expansion, and requires further preprocessing beyond the handful of examples removed after)

## 3. BGG Games Data EDA
This creates a some metrics and visuals of the additional game data download from the BGG server to identify the further cleaning and processing of the data required

## 4. BGG Data Cleaning
This code is about removing or updating the values in the complete dataset (Games_filtered.csv). 
Values were updated based on online research of the games properties, or by taking the average or an over estimate based on other games.

## 5. BGG Data Feature Engineering
This prepares the dataset to generate a recommendation by creating and formatting a bag of words per game, which contains the key terms from each game's category, mechanism, game designer, and publisher.

## 6.6 Tabletop Game Recommendation
This section utilizes the processed data to create a similarity score matrix between all games. This matrix is then used as source to search and then rank the most similar games for a single game input.

Method:
- The bag of words is used to create a matrix of token counts (count vectoriser).
- These token counts can then be used in a cosine similairty calculation to generate a matrix of similairity scores between all games.
- Finally an input of a game can then be taken to generate a ranked list of the most similar games , based on the similarity matrix.
