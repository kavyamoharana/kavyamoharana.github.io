---
name: Project - Analyzing Global Temperature Trends Over Time
tools: [Python, Scikit-Learn, Pandas]
image: assets/pngs/327-cover.png
description: ML project which uses Python's scikit-learn library for linear regression modeling and clustering analysis on climate change trends
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


## Assessing Climate Change and Global Temperature Trends Over Time
*Final project for [IS 327](https://ischool.illinois.edu/degrees-programs/courses/is327): Concepts of Machine Learning at UIUC*

<div class="left">
  {% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/python_notebooks/IS327-Project.ipynb" text="The Analysis (Jupyter Notebook)" %}
</div>
<br>
<br>

#### Purpose and Problem Description
The Climate Crisis is one of the most critical and urgent issues of our time. For most of history there has been a general lack in well-funded, proper climate change related research. Machine Learning approaches to global warming problems can provide more nuanced insights into climate patterns, complexities of global temperature trends, and help predict future climate scenarios.

#### Exploring the [Berkeley Earth](https://berkeleyearth.org/data/) Global Temperatures Dataset
For this project, I analyzed a collection of global surface temperature data from Berkeley Earth (associated with the Lawrence Berkeley National Laboratory), an independent U.S. non-profit organization focused on environmental data science and analysis. Berkeley Earth provides a large range of temperature readings from around the year 1750 to 2015 that was split into datasets by country, state, major city, and land versus ocean temperatures in a packaged [dataset](https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data) on Kaggle. My primary focus was to analyze the **LandAverageTemperature** variable within the global, country-based, and major cities datasets. 

#### Research Question:
##### **What are the long-term trends in global surface temperatures and how do temperature patterns vary in different regions over time?**
<br>

##### 1. Exploratory Data Analysis and Preprocessing
- In order to analyze trends based on seasons and year, I removed NA values, converted dates to datetime data types, added ‘Year’ and ‘Month’ columns
- I split dataset into subsets to compare global trends versus US major city trends, and summer temperatures specifically

##### 2. Linear Regression
- I trained the linear model on the training set for global average land temperatures in the summer
- implemented the same steps for major US cities to analyze the differences

##### 3. K-Means Clustering 
- performed clustering analysis on subset of average land temperatures during the summer in only major US cities – grouping regions with similar readings
- did the same for overall US temperatures and compared clusters

#### Results
*with Interactive Visualizations*
<vegachart schema-url="{{ site.baseurl }}/assets/json/chart1_327.json" style="width: 100%"></vegachart>

```
Summer Surface Temperatures Globally --
R-squared: 0.2656132923936281
Mean Squared Error (MSE): 0.24252933133205157
Root Mean Squared Error (RMSE): 0.49247267064483036
```
<vegachart schema-url="{{ site.baseurl }}/assets/json/chart2_327.json" style="width: 100%"></vegachart>
```
Summer Surface Temperatures for US Major Cities --
R-squared: 0.06748822904532015
Mean Squared Error (MSE): 1.5149053265391863
Root Mean Squared Error (RMSE): 1.230814903443725
```
The linear model for overall Global temperatures had higher accuracy.


<vegachart schema-url="{{ site.baseurl }}/assets/json/chart3_327.json" style="width: 100%"></vegachart>
```
US Major Cities --
Silhouette Score: 0.3669338556145997
```

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart4_327.json" style="width: 100%"></vegachart>
```
US Overall --
Silhouette Score: 0.4357067013289608
```
The second clustering analysis of overall US temperatures had less chance of overlapping or ambiguity. 

#### Conclusion
The linear model had a trade-off between explanatory power and predictive accuracy and it could be further improved by focusing on more specific variables or periods of time. Both the linear regression and clustering models were around the same level of accuracy and although there did seem to be an upward trend in temperatures, further improvement of the models is necessary.




