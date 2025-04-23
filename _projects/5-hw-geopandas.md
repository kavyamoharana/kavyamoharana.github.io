---
name: Analyzing California Transporation Infrastructure with Python GIS
tools: [Python, Geopandas, Folium]
image: assets/pngs/gpd-cover.png
description: Continuation of an assignment that uses Geopandas and other GIS tools for map visualizations
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---
## Analyzing California Transporation Infrastructure with Python GIS
*This personal project applies concepts learned in [IS 445](https://ischool.illinois.edu/degrees-programs/courses/is445): Data Visualization at UIUC and is a continued exploration of Python GIS visualization libraries*

---
<p style="font-size: 14px; margin: 0;">Languages, Libraries, and Tools Used</p>
> 
<a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/>
<a href="https://geopandas.org/en/stable/index.html#" target="_blank" rel="noreferrer"> <img src="https://geopandas.org/en/stable/_images/geopandas_icon.png" alt="geopandas" width="40" height="40"/>
<a href="https://python-visualization.github.io/folium/latest/#" target="_blank" rel="noreferrer"> <img src="https://python-visualization.github.io/folium/latest/_images/folium_logo.png" alt="folium" width="25" height="25"/>
<a href="https://matplotlib.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/01/Created_with_Matplotlib-logo.svg/2048px-Created_with_Matplotlib-logo.svg.png" alt="matplotlib" width="40" height="40"/>


<!-- <iframe src="/assets/html/map_lic.html" width="90%" height="500" style="border:none;"></iframe> -->

<!-- <iframe src="/assets/html/map_transit.html" width="90%" height="500" style="border:none;"></iframe> -->

<!-- <iframe src="/assets/html/map.html" width="90%" height="500" style="border:none;"></iframe> -->

##### Census-Designated Counties of the San Francisco Bay Area
<figure style="text-align: left;">
    <iframe src="/assets/html/map_bay.html" width="89%" height="500" style="border:none;"></iframe>
<figcaption>It is important to highlight the geographic layout of the region prior to analyzing factors like access to transportation ('NAMELSAD' refers to the Census legal/statistical area description code for county)</figcaption>
</figure>

<br>

#### [Dataset 1:](https://gis.data.ca.gov/datasets/CAEnergy::low-income-or-disadvantaged-communities-designated-by-california-1/about) Low-Income or Disadvantaged Communities Designated by California
>
This GeoJSON dataset from the California State Geoportal, posted by the California Energy Commission, explores 2020 State Census data for designated **Low-Income Communities (LIC)** and **Disadvantaged Communities (DAC)**. 
- [Low-Income](https://calevip.org/faq/what-low-income-community-lic-0#:~:text=Low%2Dincome%20communities%20(LICs),Development's%202016%20State%20Income%20Limits.) applies to Census *tracts* (geographic areas) with median household incomes that are at or below either 80% of the statewide median income or the threshold designated by the Department of Housing and Community Development. 
- [Disadvantaged](https://calevip.org/faq/what-disadvantaged-community-dac-11#:~:text=Log%20In-,What%20is%20a%20disadvantaged%20community%20(DAC)%3F,CalEnviroScreen%204.0%20(1%2C984%20tracts).) designation is determined by the following categories:
    - have the highest (meaning higher pollution burden) 25% of overall scores in the [CalEnviroScreen](https://oehha.ca.gov/calenviroscreen/about-calenviroscreen) 4.0
    - have no overall scores but the highest 5% of CalEnviroScreen 4.0 cumulative pollution burden scores
    - were identified in the 2017 DAC designation as disadvantaged
    - are lands under the control of federally recognized tribes



<div style="display: flex; justify-content: space-between;">
    <figure style="width: 49%; text-align: center;">
        <iframe src="/assets/html/map_peninsula.html" width="100%" height="500" style="border:none;"></iframe>
        <figcaption>
            Peninsula Subregion (San Francisco, San Mateo)
        </figcaption>
    </figure>
    <figure style="width: 49%; text-align: center;">
        <iframe src="/assets/html/map_eastbay.html" width="100%" height="500" style="border:none;"></iframe>
        <figcaption>
            East Bay Subregion (Alameda, Contra Costa)
        </figcaption>
    </figure>
</div>

<br>
#### [Dataset 2:](https://gis.data.ca.gov/datasets/863e61eacbf3463ab239beb3cee4a2c3_0/about) California High Quality Transit Areas
>
This is a GeoJSON dataset from the California State Geoportal, posted by the California Department of Transportation (CalTrans). It provides information about estimated High Quality Transit Areas in the state. This data includes attributes such as type of transportation and primary transportation agency. 
- **'hqta_type'** refers to the half-mile surrounding high quality transit corridors and major transit stops

<div style="display: flex; justify-content: space-between;">
    <figure style="width: 49%; text-align: center;">
        <iframe src="/assets/html/pen_transit.html" width="100%" height="500" style="border:none;"></iframe>
        <figcaption>
            Peninsula Subregion
        </figcaption>
    </figure>
    <figure style="width: 49%; text-align: center;">
        <iframe src="/assets/html/east_transit.html" width="100%" height="500" style="border:none;"></iframe>
        <figcaption>
            East Bay Subregion
        </figcaption>
    </figure>
</div>



<br>
#### Focusing on Santa Clara County
Having grown up in San Jose, the county seat of Santa Clara and largest city in northern California, I wanted to analyze and visualize the relationship between LIC/DAC areas and major public transportation. 

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Side by Side Iframes</title>
    <style>
        .iframe-container {
            text-align: center;
        }
        .iframe-container iframe {
            display: inline-block;
            width: 47%;
            height: 500px;
            border: none;
            margin: 10px;
        }
        .iframe-container .iframe-big {
            width: 54%;
        }
        .iframe-container .iframe-small {
            width: 41%;
        }
    </style>
</head>
<body>
    <div class="iframe-container">
        <iframe class="iframe-big" src="/assets/html/map_sc_lic.html"></iframe>
        <iframe class="iframe-small" src="/assets/html/sc_transit.html"></iframe>
    </div>
</body>

<!-- ##### Low-Income & Disadvantaged Communities in Santa Clara County, CA
<iframe src="/assets/html/map_sc_lic.html" width="105%" height="540" style="border:none;"></iframe> -->
<br>

##### Transporation in Relation to LIC/DAC Communities
<iframe src="/assets/html/overlapped_sc.html" width="95%" height="570" style="border:none;"></iframe>
<br>
Overlaying the high quality bus and rail routes over underpriviledged or low-income areas of Santa Clara County gives us various insights for access to transportation in the subregion. While this dataset doesn't provide information for every single form of transportation, it is still apparent that there are areas (LIC/DAC or not) of the cities that are not connected by major bus or rail. This is particularly evident for parts of Milpitas in the North as well as Sunnyvale, Mountain View, and Palo Alto in the Southwest. Transportation infrastructure is a highly debated issue in the state, especially given the history of California's "car-centric culture". Going forward, it would also be valuable to cross-reference this information with data on actual usage of the high quality transportation stops.


{% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/python_notebooks/CATransporation-GIS.ipynb" text="Jupyter Notebook Analysis" size="sm" %}
{% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/python_notebooks/IS445-Assignment6.ipynb" text="Original Assignment" size="sm" %}