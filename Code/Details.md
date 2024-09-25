# Structure of Board Game Recommender code

## Imports & Functions

## Ranked BGG Board Games
This section explores the ranked game data which can be directly downloaded from Board Game Geek for the purposes of identifying which games to obtain further data for.

It explores the values and distributions of:
- The years in which the games are published
- The ratings given to the games
- The overall ranks of the games

It also looks at the different versions, editions, expansions and accessories present in the data.

## BGG API Board Game Data
This section is focused on filtering the games from the ranked BGG data, using game id's to then define which data to collect from the BGG servers through their API. 
Then explore, clean, and feature engineer this data to prepare it for processing by the count vectoriser.

The filtering is necessary to reduce the amount of downloaded game data, the objectives of the filtering were to include games with:
- an average rating of 7 or above
- at least 100 ratings
- no game expansions

## Board Game Recommendation
This section utilizes the processed data to create a similarity score matrix between all games. This matrix is then used as source to search and then rank the most similar games for a single game input.

A 'bag of words' is created based on the game category, mechanism, game designer, and publisher.
This bag of words is used to create a matrix of token counts (count vectoriser).
These token counts can then be used in a cosine similairty calculation to generate a matrix of similairity scores between all games.
Finally an input of a game can then be taken to generate a ranked list of the most similar games , based on the similarity matrix.
