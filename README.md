# 6202 Machine Learning - 1: 2019 Data Science Bowl

## PBS KIDS Measure Up App Assesment Result Prediction

![app](https://github.com/gayuc07/PBS-KIDS-Measure-Up-App-Assesment/blob/main/Images/app.JPG)

The "KIDS Measure Up" app is an educational application which helps kids explore and learn fundamental math concepts in a fun and interactive manner.

The dataset contains game analytics for KIDS Measure Up! app. In this app, children navigate a map and complete various levels, which may be activities, video clips, games, or assessments.

Each assessment is designed to test a child's comprehension of a certain set of measurement-related skills. There are five assessments: Bird Measurer, Cart Balancer, Cauldron Filler, Chest Sorter, and Mushroom Sorter.

The purpose of our analysis is to use the gameplay data to forecast how many attempts a child will take to pass a given assessment and hence predicting the accuracy group for user. The outcomes of this analysis are grouped into 4 groups (labeled accuracy_group in the data):

- 3: the assessment was solved on the first attempt
- 2: the assessment was solved on the second attempt
- 1: the assessment was solved after 3 or more attempts
- 0: the assessment was never solved

### Exploratory Data Analysis

#### Assessment type

We notice that the Cart Balancer(Assessment) is the most popular assessment followed by Cauldron Filler, Mushroom Sorter, Chest Sorter and Bird Measurer.

![assessment](https://github.com/gayuc07/PBS-KIDS-Measure-Up-App-Assesment/blob/main/Images/assess.JPG)

#### GamePlay Type

We notice that the Clip media type is most famous, followed by Activity and Game.

![Gameplay](https://github.com/gayuc07/PBS-KIDS-Measure-Up-App-Assesment/blob/main/Images/gameplay.JPG)

#### Game Time

Accuracy group 0 is highest, it means that kids who take more attempts to solve the assessment, play the game for a longer time period.

![Gameplay](https://github.com/gayuc07/PBS-KIDS-Measure-Up-App-Assesment/blob/main/Images/gametime.JPG)

#### Assessment vs Accuracy Group

![Gameplay](https://github.com/gayuc07/PBS-KIDS-Measure-Up-App-Assesment/blob/main/Images/accuracy_grp.JPG)

### Modelling
As a Classification problem, we plan to experiment various classifier and identify best classifier that suit the given dataset.

From exploratory data analysis and correlation matrix we could see most of the events id doesnt consitute to target values, so we aim to drop the feature from data. We trained whole data using random forest classifier and the event_id importance over the assesment target value is observed. Considering all these, we could able to select top 10 events that marginally influence the data.

![eval](https://github.com/gayuc07/PBS-KIDS-Measure-Up-App-Assesment/blob/main/Images/model_eval.JPG)

#### Feature Importance

![feature](https://github.com/gayuc07/PBS-KIDS-Measure-Up-App-Assesment/blob/main/Images/feature.JPG)

This is similar to EDA we analysed previously, each users events count, clips watched , game played before assessment are contributing factor for outcome of his assesment result. Also we could see,kid's experience over other assesment also helps them with current assesment.


### Conclusion

#### EDA Results

- Bird Measurer and Chest Sorter assesments are rare events, Kids usually prefer basic level assesment like cart balancer and cauldron filler than harder levels.
- TREETOPCITY is most played city by kids
- Kids are most interetsed to watch clips compared to games and activity
- From history of records provided, kids are able to perform well on their first attempt and falls into the accuracy group of 3. Kids are prone to complete assesments like cart balancer, cauldron Filler at their first attempt.
- Total time spent by group 3 is more compared to group 2 which infers kids take their time in their first assesment.
- Bird measurer and chest sorter have less accuracy level compared to other assesment.

#### Modelling

- Ensemble methods and catboost model performs better with accuracy of ~56%
- Previous assesment details, event count, game time are influencing factors for predicting the target groups

#### Recommendations

From above analysis, we could suggest kids are finding difficulities in completing chest sorter, bird measurer, if they could add more clips and activity, it will be helpful to perform better. Also, as Kids prefered to watch more clips compared to games/activity, clip contents can be improved and they could also concentrate on developing eye catching game/activity or check for issues with present content for its less usage compared to clips, so that kids can take max out of these resources as well.

#### Future Goals

Present Model produces result at accuracy of ~56%.This is mainly due to high difference on number of samples of each accuracy group. Although oversampling is performed, model couldnt able to capture perfect distinction among the accuray groups. If we able to get more samples for these records then we could able infer better details. Also in this project we have experimented only with aggregated play history of each kids. However, there are possibility event sequence plays vital role, LSTM Model with embedding on events can be experimented to check sequence level dominance to target prediction.Further analysis on the dataset is required to get more prominent features that constitute to the target variables like checking interval after which each game or assesment is taken, etc.









