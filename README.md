# Movies Analysis - Data Analysis
In this repository, we will do some data analysis on the Movie Industry dataset obtained from: https://www.kaggle.com/datasets/danielgrijalvas/movies. 

## Technologies Used
- Python - pandas, numpy, matplotlib, seaborn

## Setup
- Download the Movie Industry csv file.
- Import the following libraries: 
  ```
  import pandas as pd
  import numpy as np
  import seaborn as sns
  import matplotlib
  import matplotlib.pyplot as plt
  plt.style.use('ggplot')
  from matplotlib.pyplot import figure
  
  %matplotlib inline
  matplotlib.rcParams['figure.figsize'] = (12, 9)
  ```
- Read the csv file: `df = pd.read_csv('<file_name>.csv')`

## Data Cleaning
Before doing any analysis, clean the data by using:
- `df = df.dropna()`: to drop any null values
- `df['<column_name>'] = df['<column_name>'].astype('<data_type>')`: to change the data type of the column
- `df['<column_name>'] = df['<column_name>'].str.extract()`: to get any relevant substring

## Correlation Analysis on Movies' Gross Revenue
### Hypothesis
Make an educated guess on what features/attributes will affect the gross revenue of a movie. Let's say we believe the budget of the movie affects how much a movie will generate. 

### Testing
Let's test our hypothesis. First, plot the data from the two columns, budget and gross, using:
```
plt.scatter(x=df['budget'], y=df['gross'])
plt.xlabel('Budget')
plt.ylabel('Gross Revenue')
plt.title('Budget vs Gross Revenue')
plt.show()
```
<img width="1005" height="783" alt="image" src="https://github.com/user-attachments/assets/6d8068d7-d94f-4e94-87c0-7bbaf64ef5cb" />

We can observe that the data is trending upwards, so there might be some signs of high correlation between gross revenue and budget.

### Revise Hypothesis
Let's take a closer look and use seaborn to plot a regression line that best fit the data using:
```
sns.regplot(x='budget', y='gross', data=df, line_kws={"color":"blue"})
```
<img width="1005" height="783" alt="image" src="https://github.com/user-attachments/assets/a0d5b9f5-f28a-4813-b408-acb7076a6cda" />

Now, we certainly see that the data is indeed trending upwards. So, take a look at the correlation between different numeric columns using:
```
sns.heatmap(df.corr(numeric_only=True), annot=True)
```
<img width="1005" height="783" alt="image" src="https://github.com/user-attachments/assets/18d14a5d-a013-48fd-b8c4-aec6d02f8eef" />

### Conclusion
As shown in the correlation matrix, gross revenue has a high correlation to budget of 0.74. So, if more budget is used, we can expect higher gross revenue.

## Acknowledgement
This project is a continuation from a video I stumbled previously from Alex The Analyst. However this time, this repository will focus on the technique from the youtube video titled "Data Analyst Portfolio Project | Correlation in Python | Project 4/4" from Alex The Analyst, again very cool stuff! So, I created this repository to practice my data analysis skills using Python and also to keep track of my progress in becoming a Data Analyst.

- Link to AlexTheAnalyst youtube video: https://www.youtube.com/watch?v=iPYVYBtUTyE
- Link to AlexTheAnalyst repository: https://github.com/AlexTheAnalyst/PortfolioProjects/tree/main
