---
name: Analyzing Popular Movies & TV Shows on Netflix and Prime Video
tools: [Python, Pandas, Scikit-Learn]
image: assets/pngs/207-cover.png
description: Project which analyzes a dataset of popular movies and shows on Netflix and Prime Video to identify trends in genre, ratings, and popularity
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

## Analyzing Popular Movies & TV Shows on Netflix and Prime Video
*Final project for [STAT 207](https://exploration.stat.illinois.edu/): Data Science Exploration at UIUC*

---

###### *Languages and Tools Used*
<a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/>
<a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/>
<a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/>
<a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/>
<a href="https://altair-viz.github.io/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Vega-Lite_Logo.svg/1920px-Vega-Lite_Logo.svg.png" alt="vega-lite" width="40" height="40"/>

<div class="left">
  {% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/python_notebooks/STAT207-Project.ipynb" text="View Full Analysis (Jupyter Notebook)" %}
</div>
<br>
<br>

#### Motivation behind the Analysis:
The main motivation behind exploring this dataset would be the popularity and widespread use of Netflix and Amazon Prime Video as the top 2 streaming platforms for movies and television. I enjoy using these platforms for binging TV shows or movies and believe that analyzing such data would be helpful to us and others with similar hobbies. Ultimately the goal is to determine if either streaming platform contained certain movies or shows with higher ratings and if the ratings differ based on genre or year of release.

#### Research Questions:
1. How does the relationship between genre and the year it came out affect the overall Rotten Tomatoes rating of the movie?
2. Is there an association between Action and Adventure titles and higher rated Rotten Tomato scores from the population of popular movies and tv shows on Netflix and Amazon Prime Video?
3. Is there a linear relationship between the Rotten Tomatoes rating of a movie and the year it was released, the age rating, and whether the movie is on Netflix or Amazon Prime Video?
4. Can we predict whether a movie is available on Netflix based on its age rating, genre, Rotten Tomatoes score, and IMDb rating?

##### Details & Limitations of the Dataset:
This dataset is from Kaggle and presents a collection of popular movies and TV shows on both Netflix and Amazon Prime Video. The dataframe contains 10 columns and 24664 rows before cleaning for missing values and other factors. The data includes titles from 1912 all the way to 2021 but we will be focusing in on the programs from the most recent decade of 2011 to 2021. There are some limitations to the data as it does not include any variables which allow for us to differentiate between TV shows and movies in the dataset. Therefore, we have chosen to look at both of these forms of media hollistically instead of differentiating between the two.

##### Descriptive Analytics
<br>
*Version 1 - Matplotlib/Seaborn Bar Plot*
<img src="/assets/pngs/chart207.png" alt="image tooltip here" width="750"/>
*Version 2 - Interactive Vega-Lite Bar Plot (Scores Combined)*
<vegachart schema-url="{{ site.baseurl }}/assets/json/barplot_207.json" style="width: 100%"></vegachart>
*Version 3 - Interactive Vega-Lite Scatter Plot*
<vegachart schema-url="{{ site.baseurl }}/assets/json/scatter1_207.json" style="width: 100%"></vegachart>

##### Inference
***Visualizing the top 25% of Rotten Tomatoes scores for the Titles***
<vegachart schema-url="{{ site.baseurl }}/assets/json/boxplot_207.json" style="width: 100%"></vegachart>
<br>

##### Logistic Regression
***Predicting whether a movie is available on Netflix based on its age rating, genre, Rotten Tomatoes score, and IMDb rating***
<div style="display: flex; justify-content: space-between;">
    <img src="/assets/pngs/logit_207.png" alt="image tooltip here" width="400"/>
    <vegachart schema-url="{{ site.baseurl }}/assets/json/rocchart_207.json" style="width: 100%"></vegachart>
</div>

<!-- <img src="/assets/pngs/ols_207.png" alt="image tooltip here" width="400"/> -->
- The pseudo R-squared value of 0.1837 shows that the final logistic regression model had a statistically significant relationship with whether a movie is available on Netflix or not. This means that the model explains about 18% of the variability in the response variable.
- We also found that the age rating, year of release, Rotten Tomatoes score, and IMDb rating were significant predictors of whether a movie is available on Netflix or not. Specifically, movies with higher age ratings and higher Rotten Tomatoes and IMDb scores were more likely to be available on Netflix.
- The AUC of 0.7724 indicated that the model has some ability to distinguish between positive and negative cases, although there is still room for improvement. Choosing an appropriate threshold of 0.2, we prioritized correctly predicting positive cases (i.e., movies that are on Netflix). 
- Shows that we can use the model to identify movies that are likely to be available on Netflix within a reasonable degree of accuracy

#### Analysis Summary
- There may be an association between the genre of a movie, year of release and the Rotten Tomatoes score, with Action & Adventure and Drama consistently having higher scores and the median score by year increasing steadily from 2011 to 2021. 
- We analyzed the concentration of Action and Adventure movies' Rotten Tomatoes scores, and the confidence intervals provided more information about the possible association between genre and Rotten Tomatoes score.
- We gained insight into the lack of a linear relationship between the year, rating, and streaming platform of movies. 
- Age rating, year of release, Rotten Tomatoes score, and IMDb rating were significant predictors of Netflix availability. 
- The ROC curve and AUC with a threshold of 0.2 suggested that the model can identify movies available on Netflix with a reasonable degree of accuracy, providing insights for content targeting by producers and distributors.