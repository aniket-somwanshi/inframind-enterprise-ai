# Match-day Alerts
###### Customer engagement: During the live match, the viewers are given alerts whenever a "big" moment is about to occur in the match. So that even if the viewers can't watch the whole match, they will not miss the exciting moments from the match.
## Environment Setup
The models are built on the [Google Colab](https://colab.research.google.com/) platform. The following setup will let you reproduce the whole directory and get it up and running.
1. Clone the repository.
2. Open [Google Drive](http://drive.google.com/).
3. Create new Folder `Inframind`.
4. Upload the repository contents inside the folder.
5. Go to [Google Colab](https://colab.research.google.com/).
6. Mount Google Drive.

![Enterprise AI Cycle](https://github.com/aniket-somwanshi/inframind-enterprise-ai/blob/master/Resources/md_paths.png)
The paths defined throughout the repository are now consistent with your Google Drive directory as shown in an example above.

## Download models
### Boundary Models
1. Go to [Boundary Models archive](https://drive.google.com/file/d/1dPGOSWrmUkAmkttLy7m9eVBIbbPpgqxz/view?usp=sharing)
2. Download the .zip file.
3. Navigate to `/Customer engagement/boundary_prediction/model_training`.
4. Extract the downloaded .zip file in the current directory.
5. Make sure `model_training_inning_1.pkl` and `model_training_inning_2.pkl` are in `/model_training` directory.

### Wicket Models
1. Go to [Wicket Models archive](https://drive.google.com/file/d/126Q-COcVVF0vUOLjA_UYcllGsu8Pboeu/view?usp=sharing)
2. Download the .zip file in the current directory.
3. Navigate to `/Customer engagement/wicket_prediction/model_training`.
4. Extract the downloaded .zip file.
5. Make sure `model_training_inning_1.pkl` and `model_training_inning_2.pkl` are in `/model_training` directory.

## 1. Introduction to use case
Consider the use case of HotStar, a subscription based
model for live sports-streaming. There are several other
competitors out there which provide free sports livestreaming services. Customer acquisition and retention
are huge challenges. Cricket ODI matches last for about 7
hours. Majority of viewers don’t have the time to watch
the whole live match. At the same time, the viewers don’t
want to miss the exciting moments in the match.

The proposed solution for the use case is **Match-day
Alerts**. Viewers will receive alerts during the live
match when big moments are about to occur.


## 2. Approach to Solution
The goal is to predict whether a “big” moment will occur in the current
over or not. Big moment will be the predictive feature defined as:
`wicket in this over` or `multiple boundaries in this over`.
We may start with analysing some preliminary ball by ball data of ODI
matches.

![Features](https://github.com/aniket-somwanshi/inframind-enterprise-ai/blob/master/Resources/md_features.png)

Although these features seem relevant, we will need the following complex features that can better
quantify all the aspects of the match.  
**State of the game:** wickets_so_far, runs_so_far, run_rate_last_5_overs,
balls_in_partnership, balls_since_last_boundary.  
**Players:** bowler’s_average, bowler’s_strike_rate, batsman’s average,
batsman’s strike_rate


## 3. High Level Architecture
![Enterprise AI Cycle](https://github.com/aniket-somwanshi/inframind-enterprise-ai/blob/master/Resources/md_architecture.png)


## 4. Challenges & Considerations
- **Highly Imbalanced Dataset:**
  In a 50-overs match, the number of “big” overs are a minority,
  making our positive predictive class population to be only 10% of the total population.    
- **High Amount of Noise:**
  Cricket is a game of unexpected events, often the boundaries are
  un-intentional or the batman’s strategy of play might change from
  game to game, leading to a lot of noise in the data.  
- **Prone to Overfitting:**
  Modelling such a complex problem may demand complex features, but
  they can often lead to overfitting and may fail to generalise for
  unseen data.


## 5. User Interface
![UI](https://github.com/aniket-somwanshi/inframind-enterprise-ai/blob/master/Resources/ui_md_2.png)

