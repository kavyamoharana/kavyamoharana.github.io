---
name: The Heart of CampusTown - Analyzing Green Street’s Most Popular Restaurants
tools: [Python, NLTK, Scikit-Learn]
image: assets/pngs/campustown-3.png
description: Project using Python's NLTK library for text sentiment analysis of Yelp reviews for popular UIUC restaurants
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

## The Heart of CampusTown: Analyzing Green Street’s Most Popular Restaurants
*Final project for [CS 410](https://cs.illinois.edu/academics/courses/cs410): Text Information Systems at UIUC*<br />
Group Members: Pranav Chandra, Kavya Moharana, Sriya Mikkilineni, Aryan Vaswani

---

###### *Languages and Tools Used*
<a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/>
<a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://miro.medium.com/v2/resize:fit:592/1*YM2HXc7f4v02pZBEO8h-qw.png" alt="NLTK" width="40" height="40"/>
<a href="https://pytorch.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="pytorch" width="40" height="40"/>
<a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/>
<a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/>
<a href="https://altair-viz.github.io/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Vega-Lite_Logo.svg/1920px-Vega-Lite_Logo.svg.png" alt="vega-lite" width="40" height="40"/>


<style>
  .left {
    display: inline-block;
    margin-right: 10px; /* Adjust the margin as needed for spacing */
  }
</style>

<div class="left">
  {% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/assets/pdfs/410-Report.docx.pdf" text="View Full Report" %}
</div>
<div class="left">
  {% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/python_notebooks/CS410-Project.ipynb" text="The Analysis (Jupyter Notebook)" %}
</div>
<br>

<br>
<br>

#### Abstract
Green Street’s wide variety of restaurants and cafes is an integral part of student life at the University of Illinois at Urbana-Champaign. Known as the “Heart of Campustown”, these establishments provide an important cultural and social hub for students, faculty, and residents. We intend to conduct sentiment analysis of the Yelp reviews for multiple major restaurants on this historical street. We will analyze online reviews over time periods to determine how students and food enthusiasts perceive these restaurants. Through this evaluation, we can see how the reception of these popular food spots has changed over the past decade.

#### The Data
We utilized two different datasets during this project: the first from [Kaggle](https://www.kaggle.com/datasets/hhalalwi/yelp-light) for the testing of five different models and one for the evaluation of our actual project. To understand why we needed two  models, we need to look at [Yelp’s GraphQL API](https://docs.developer.yelp.com/docs/graphql-basic-usage) documentation. For this project, we have identified 12 restaurants on Green Street for which we were interested in understanding peoples’ sentiments towards them over time, as shown in Figure 1. However, because Yelp API is still in its beta stage, we are limited to only the first three reviews on each restaurant's Yelp page. While severely limits our ability in trying to understand Champaign’s preferences, our code still shows sentiments over a couple of months. When the API limits increase, we would only have to re-run the code as is to get all the data.

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart2_410.json" style="width: 100%"></vegachart>
Figure 1

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart1_410.json" style="width: 100%"></vegachart>
Figure 2