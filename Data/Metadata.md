## Metadata

## boardgames_ranks.csv
This is raw data from Board Game Geek (BGG) that shows a full list of all games on their website (https://boardgamegeek.com/data_dumps/bg_ranks) and their following data:

#### **id**
This is the identification number given by Board Game Geek to each game

#### **name**
This is the name of the game.

#### **average**
The average user rating, based on individual ratings out of 10.

#### **bayesaverage**  
Statistical technique used to calculate a more reliable average by incorporating prior knowledge or assumptions about the data. 
These assumptions include:  
- **Prior Mean** - the average rating across all games assumed before observing any data  
- **Prior Count** - weighting of prior belief about the prior mean, balances the influence of observed data against prior assumption 
    
(if high the bayes average will be close ot the prior mean, if low, it willbe more influenced by actual observed data)

#### **usersrated**
This is just the number of people who have voted.

#### **abstracts_rank** 
"Abstract game" often refers to games of perfect information with alternating turns and no randomness; usually for 2 players.
It is also often used to refer to a game without a theme (regardless of the game mechanics).  
https://boardgamegeek.com/wiki/page/Abstract_Games&redirectedfrom=Abstract_Strategy  
https://boardgamegeek.com/abstracts/browse/boardgame

#### **cgs_rank**
 Custom Game System Rank. It is a specific ranking for games that fall under custom or special rankings created by users or groups within the BGG community.  
https://boardgamegeek.com/cgs/browse/boardgame

#### **childrensgames_rank** 
Childrens games are designed specifically for children generally under the age of 10.  
https://boardgamegeek.com/childrensgames/browse/boardgame.  

#### **familygames_rank**  
Family games are accessible for a broad audience, including adults, teenagers, and children, typically ages 8 and up.  
https://boardgamegeek.com/familygames/browse/boardgame

#### **partygames_rank**  
Party games are designed ot be played in causal, social setting, often with large groups of people.  
https://boardgamegeek.com/partygames/browse/boardgame

#### **strategygames_rank**  
Strategy games emphasize strategic thinking, planning, and decision-making over luck or simple mechanics.  
https://boardgamegeek.com/strategygames/browse/boardgame

#### **thematic_rank**    
Thematic games are characterized by their strong storytelling elements, immersive themes, and emphasis on the narrative experience.  
https://boardgamegeek.com/thematic/browse/boardgame

#### **wargames_rank** 
Wargames simulate military conflicts, battles, or wars, often focusing on historical accuracy, strategy, and tactical decision-making.  
https://boardgamegeek.com/wargames/browse/boardgame

## games_ranks_updated.csv

This includes the same data as boardgames_ranks.csv, with the addition of the following data per game:

####  **name_prefix**  
This is a the prefix of the game name, which attempts to group games based on a common base game (monopoly being a key example), the prefix is defined as all charracters at the start of the game name until a ":" or "(" is reached

####  **name_prefix_count**  
This is simply the count of all unique name_prefix values

## games_filtered.csv

This is data of games from the games_ranks_updated.csv file filtered by:
- an average rating of 7 or above
- at least 100 ratings
- no game expansions extracted from the BGG server 

Additional data for each of these filtered games is then extracted from the BGG servers through their public API.

The complete list of columns in the dataset include:

#### id
This is the identification number given by Board Game Geek to each game

#### name  
This is the name of the game.

#### Average
The average user rating, based on individual ratings out of 10.

#### usersrated
This is the number of people who have rated the game.

#### number of comments  
This is the number of people who have sent a comment with their rating about the game on the website

#### complexity votes  
This the total number of people who have voted on the complexity of the game

#### average complexity  
The average user rating, based on individual ratings out of 5, 0 being the lowest complexity and 5 being the highest

#### year published  
The year the game was published

#### min player number  
The minimum number of players of the game as recorded by Board Game Geek

#### max player number  
The maximum number of players of the game as recorded by Board Game Geek

#### min play time  
The minimum play time of the game in minutes

#### max play time  
The maximum play time of the game in minutes

#### expected play time  
This is the expected play time of the game in minutes

#### minimum age limit  
This is the minimum age limit for the game

#### category  
These are groupings for a games based on similar subjects or characteristics

#### mechanism  
These are groupings for games based more specifically on the types of action performed in game by a player that modifies the game state

#### game designer 
These are the individuals or groups that responsible for the creative vision, concept, and overall design
 
#### publisher
These are the groups responsible for financing, marketing, distributing the game

#### url
This is the URL of the API server used to access the source of data from the Board Game Geek server for the specific game  

## games_clean.csv

This is a cleaned version of games_filtered.csv which updates:

#### complexity values 
Missing values updated based on average from previous similar entries of game series  

#### player number values 
Updated first based on BGG or publisher website, then game box (if shown), then based on BGG community

#### play time values
Rules on revised values for playtime
- Round values up to the nearest 5 minutese:
- If no expected playtime - take average of max and min play times
- If no max play time - take min play time
- If no values in min, max or expected playtimes, and other versions exist, take average of other editions/ versions

Exceptions:
- Chess - values based on estimates from chess.com
- Disney Lorcana - values based on wikipedia article
- Under the Lily Banners, 1914: Offensive à outrance! & 
Iron Curtain: Central Europe, 1945-1989 - values based on similar war games
- 1914: Offensive à outrance! - values based on similar war games
- Digimon Card Game, One Piece Card Game, The Genius Star - no evidence found - taken an initial guess (to be revised if played) - 30 / 60 / 45

#### minimum  age limit values 
If no minimum age limit, assume it is the maximum (21), revise values when played, or researched in more depth


## games_fe.csv
This a feature engineered version of games_clean.csv, which:
- Formats all text fields to ensure that labels with multiple words are distinguishable and easier to separate from other labels by replacing whitespace with an underscore, expect adjacent to the '//' separator

- Creates bag of words for each game by combining all the unique labels of mechanism, game designer and publisher to a new column 'bag of words'
