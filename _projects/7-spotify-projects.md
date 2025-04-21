---
name: Analyzing Spotify's Hit Songs
tools: [Python, Pandas, Scikit-Learn]
image: assets/pngs/204-cover.png
description: Projects which analyze the Spotify hit songs dataset to identify trends in genre and popularity
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

## Analyzing Spotify's Hit Songs and How Genres Encapsulate Different Music Trends
*Final projects for [STAT 107](https://discovery.cs.illinois.edu/): Data Science Discovery and [IS 204](https://ischool.illinois.edu/degrees-programs/courses/is204): Research Design for Information Sciences at UIUC*

---

###### *Languages and Tools Used*
<a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/>
<a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/>
<a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/>
<a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/>
<a href="https://altair-viz.github.io/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Vega-Lite_Logo.svg/1920px-Vega-Lite_Logo.svg.png" alt="vega-lite" width="40" height="40"/>


<!-- #### 1. Exploring the Spotify Top Hits [2000 to 2019 Dataset](https://www.kaggle.com/datasets/paradisejoy/top-hits-spotify-from-20002019)
First, I conducted analysis on a dataset from Kaggle which contains data of the top 2000 *overall* hit songs on the popular music streaming platform, Spotify, that were <u>released</u> from 2000 to 2019. The dataset has 18 columns covering general information about the song (name, artist, genre, song duration, year of release) as well as other factors that Spotify itself uses to classify its top tracks such as scores for popularity, danceability, energy, and liveness. The following visualizations show the **Exploratory Data Analysis** of this dataset.


<vegachart schema-url="{{ site.baseurl }}/assets/json/chart1_107.json" style="width: 80%"></vegachart>

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart2_107.json" style="width: 80%"></vegachart>

<vegachart schema-url="{{ site.baseurl }}/assets/json/pie_chart_107.json" style="width: 60%"></vegachart>

<div class="left">
  {% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/python_notebooks/STAT107-Project.ipynb" text="View Full Analysis (Jupyter Notebook)" %}
</div>
<br>
<br> -->
<style>
  .left {
    display: inline-block;
    margin-right: 10px; /* Adjust the margin as needed for spacing */
  }
</style>

<div class="left">
  {% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/assets/pdfs/204-ResearchPaper.pdf" text="View Full Research Paper and Report" %}
</div>
<div class="left">
  {% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/python_notebooks/IS204-Project.ipynb" text="The Analysis (Jupyter Notebook)" %}
</div>
<br>

<br>
<br>

#### Exploring the Spotify Top 100 Hit Songs [2010 to 2022 Dataset](https://www.kaggle.com/datasets/josephinelsy/spotify-top-hit-playlist-2010-2022)
The second project uses another Kaggle dataset for Spotify's top 100 hit songs per year from 2010 to 2022. This data was extracted directly from the Spotify API and specifically their 'Top Hits' playlist for each year (with 100 songs per year). The dataset has 23 columns and 2400 rows with 13 track audio features consisting of danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, tempo, duration, and time signature. 

##### Research Questions:
- Why are specific music trends on Spotify the way they are?
- What aspects contribute to trends within a user’s music and listening history?
- How does a user most frequently discover their most listened to genre?
- Is someone who is interested in one genre more likely to be interested in another genre?

##### Analysis Results:
<img src="/assets/pngs/summarystats.png" alt="image tooltip here" width="450"/>
***Table 1* – Summary Statistics**

<div style="display: flex;">
    <vegachart schema-url="{{ site.baseurl }}/assets/json/scatter1_204.json" style="width: 50%;"></vegachart>
    <vegachart schema-url="{{ site.baseurl }}/assets/json/scatter2_204.json" style="width: 50%;"></vegachart>
</div>
***Figure 1.1* – Exploratory Quantitative Analysis on Popularity Factors**
- weak positive correlation for first chart shows that music trends are multifaceted
- energy variable contributes to more trends than expected

<vegachart schema-url="{{ site.baseurl }}/assets/json/line2_204.json" style="width: 80%"></vegachart>
***Figure 1.2* – Exploratory Quantitative Analysis on Average Duration of Songs**
- strong negative trend display how song duration has decreased significantly since 2014 
- future music releases may continue to decrease in duration or remain stagnant 

<vegachart schema-url="{{ site.baseurl }}/assets/json/linreg_204.json" style="width: 80%"></vegachart>
***Figure 2* – Linear Regression Analysis of Artist Popularity and Track Popularity**
- strong positive correlation implies artist popularity is closely tied to the popularity of a song and how a user finds hit songs 

<vegachart schema-url="{{ site.baseurl }}/assets/json/heatmap_204.json" style="width: 80%"></vegachart>
***Figure 3* – Correlation between Popular Genres**
- The rap genre has moderate positive correlation with hip-hop and trap genres
-  Users who like broad genres like rap or pop are may be more likely to be interested in closely related genres like trap