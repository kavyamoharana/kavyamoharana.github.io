---
name: IS 445 Final Project 3.1
tools: [Python, Altair, vega-lite]
image: assets/pngs/3.1_cover.png
description: This is a group final project for IS 445!
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


# Final Project Part 3.1
##### Team Members: Kavya Moharana, Sanjana Pai, Ridah Shaikh, Shreshika Bommana
---
### 'City of Urbana Police Arrests' Dataset:
We are exploring data from the [state of Illinois data portal](https://data.illinois.gov/dataset/police-arrests) which contains records of all arrests by the Urbana Police Department since 1988.
<!-- 
Direct [CSV link](https://data.illinois.gov/dataset/1d18ecc0-3c7e-4507-b8cc-7a5e30359d44/resource/ca1dceb3-01f8-4a56-935b-7e3035ff60a4/download/police-arrests-upload_20191226.csv) to dataset -->

<!-- <div class="left">
{% include elements/button.html link="https://data.illinois.gov/dataset/1d18ecc0-3c7e-4507-b8cc-7a5e30359d44/resource/ca1dceb3-01f8-4a56-935b-7e3035ff60a4/download/police-arrests-upload_20191226.csv" text="The Dataset" %}
</div>
<div class="left">
{% include elements/button.html link="https://github.com/jnaiman/online_cv_public/blob/main/python_notebooks/test_generate_plots.ipynb" text="The Analysis (Jupyter Notebook)" %}
</div> -->
<style>
  .left {
    display: inline-block;
    margin-right: 10px; /* Adjust the margin as needed for spacing */
  }
</style>

<div class="left">
  {% include elements/button.html link="https://data.illinois.gov/dataset/1d18ecc0-3c7e-4507-b8cc-7a5e30359d44/resource/ca1dceb3-01f8-4a56-935b-7e3035ff60a4/download/police-arrests-upload_20191226.csv" text="The Dataset" %}
</div>
<div class="left">
  {% include elements/button.html link="https://github.com/jnaiman/online_cv_public/blob/main/python_notebooks/test_generate_plots.ipynb" text="The Analysis (Jupyter Notebook)" %}
</div>
<br>


<br>
<br>
<br>

#### Chart 1:
*bar chart visualizing types of arrests made*

<vegachart schema-url="{{ site.baseurl }}/assets/json/3.1_chart1.v3.json" style="width: 100%"></vegachart>

#### Chart 2:
*bar chart visualizing the residency distribution of arrestees*

<vegachart schema-url="{{ site.baseurl }}/assets/json/3.1_chart2.v3.json" style="width: 100%"></vegachart>

#### Interactive Plot:
*interactive charts visualizing average age and arrest resolution alongside employment, from 1993 to 2019*

<vegachart schema-url="{{ site.baseurl }}/assets/json/3.1_interactive_v2.json" style="width: 100%"></vegachart>
---
#### Contextual Visualizations:
![image tooltip here](/assets/pngs/contextviz1.png)
Urbana, Illinois (IL 61802) Profile. https://www.city-data.com/city/Urbana-Illinois.html. Accessed 1 Dec. 2023.

<!-- <iframe width="720px" height="480px" src="https://datausa.io/profile/geo/urbana-il/demographics/race_and_ethnicity?viz=true" frameborder="0" ></iframe> -->
![image tooltip here](/assets/pngs/contextviz2.png)
Urbana, IL | Data USA. https://datausa.io/profile/geo/urbana-il#race_and_ethnicity. Accessed 1 Dec. 2023.

<br>
#### *Data Visualization for the Public* Write-Up
<br>

<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://github.com/vega/vega/blob/main/docs/data/cars.json" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/jnaiman/online_cv_public/blob/main/python_notebooks/test_generate_plots.ipynb" text="The Analysis" %}
</div>

