---
name: Exploring Altair and Vega-lite (IS 445)
tools: [Python, Altair, HTML, vega-lite]
image: assets/pngs/hw8.png
description: This is an assignment which uses Python, Altair, and vega-lite for interactive viz!
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

## Homework 8


**This homework assignment uses the [Bigfoot dataset](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv) !**

------

##### Plot 1: Scatterplot visualizing the relationship between low temperatures and dew point with humidity

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart2_final2.json" style="width: 100%"></vegachart>


------

##### Plot 2: Scatterplot visualizing the relationship between high temperatures and dew point by season and state


<vegachart schema-url="{{ site.baseurl }}/assets/json/chart3.json" style="width: 100%"></vegachart>

------
### Write Up
For this assignment, I created two visualizations displaying variables from the bigfoot dataset, which we used earlier in the semester. In contrast to homework 7, I decided to switch from the buildings dataset to the bigfoot one because the latter had a larger number of interesting quantitative variables.

The first plot highlights the relationship between lowest temperature readings and dew point along with a color scale showing humidity levels. For this plot I was able to apply similar methods from homework 7 while creating a scatterplot instead. This plot was relatively easy to build and I spent most of my time figuring out how to change axes ranges and add the standard interactive pan/zoom features. Using vega-lite example graphs and documentation, I was able to implement these features with a blue color scale.

The second plot displays the correlation between highest temperature readings and dewpoint categorized by the four seasons and the 10 states with the most bigfoot observations in the dataset. This interactive plot was more challenging to implement because I had to spend more time figuring out which selection tool to use and how to input element binding. Since I was dealing with categorical variables like 'state' and 'season', I decided to follow one of the examples on the vega-lite documentation but I changed the range slider to a dropdown menu. The resulting plot allows users to view all the points by color-coded seasons and then select a specific state and season combination, which greys out all other points.  

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/python_notebooks/homework8.ipynb" text="The Analysis" %}
</div>
 