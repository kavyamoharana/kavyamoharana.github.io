---
name: Analyzing Trends in Electric Vehicle Usage
tools: [Python, Pandas, Zenodo]
image: assets/jpegs/477-project-cover.jpg
description: Data Curation project using Python and other tools for creating a reproducible research package, end-to-end workflow execution, and metadata
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

## Analyzing Trends in Electric Vehicle Usage: US and Global Perspectives
<p style="font-size: 16px; margin: 0;">
  <em>
    Final Project for <a href="https://ischool.illinois.edu/degrees-programs/courses/is477">IS 477</a>: Data Management, Curation, and Reproducibility at UIUC
  </em>
</p>
<p style="font-size: 14px; margin-top: 0;">By Kavya Moharana, Mahnur Khalid, Aisha Ziad</p>

---

<!-- ###### *Languages, Libraries, and Tools Used* -->
<p style="font-size: 14px; margin: 0;">Languages, Libraries, and Tools Used</p>
>
<a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/>
<a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/>
<a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/>
<a href="https://altair-viz.github.io/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Vega-Lite_Logo.svg/1920px-Vega-Lite_Logo.svg.png" alt="vega-lite" width="40" height="40"/>
<a href="https://snakemake.github.io/" target="_blank" rel="noreferrer"> <img src="https://avatars.githubusercontent.com/u/33450111?s=200&v=4" alt="snakemake" width="40" height="40"/>
<a href="https://about.zenodo.org/" target="_blank" rel="noreferrer"> <img src="https://about.zenodo.org/static/img/icons/zenodo-icon-blue.svg" alt="zenodo" width="40" height="40" /> 

<!-- [![DOI](https://sandbox.zenodo.org/badge/DOI/10.5072/zenodo.141771.svg)](https://handle.stage.datacite.org/10.5072/zenodo.141771) -->

<p>
  <a href="https://sandbox.zenodo.org/records/141771">Archival Record</a>
  <a href="https://handle.stage.datacite.org/10.5072/zenodo.141771">
    <img src="https://sandbox.zenodo.org/badge/DOI/10.5072/zenodo.141771.svg" alt="DOI Badge" style="vertical-align: middle;">
  </a>
</p>

{% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/assets/pdfs/477-ProjectReport-Final.pdf" text="Read the Full Project Report" style="secondary" size="sm" %}
{% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/python_notebooks/IS477-Project-Analysis.ipynb" text="The Analysis (Jupyter Notebook)" style="secondary" size="sm" %}

<!-- [Archival Record](https://sandbox.zenodo.org/records/141771) [![DOI](https://sandbox.zenodo.org/badge/DOI/10.5072/zenodo.141771.svg)](https://handle.stage.datacite.org/10.5072/zenodo.141771) -->

### Summary
The overall goal or motivation of this project is to conduct comprehensive analysis on Electric Vehicle (EV) data to understand potential trends in the use of fuel efficient vehicles both in the United States and globally. The Environmental Protection Agency categorizes EVs as ‘Green’ vehicles, as an alternative to conventional gasoline or diesel (fossil fuel) powered vehicles because they reduce emissions of CO2 or other harmful greenhouse gasses into the atmosphere. As the production and sales of such environmentally friendly vehicles have been growing in recent years, it may be indicative of a shift in perspective towards climate change or changes in affordability of EVs. Out aim is to analyze data from the Washington State Department of Licensing and the International Energy Agency to examine the differences between EV types, understand EV population differences between certain US states, and then to see if these insights are reflected within global electric vehicle sales.
<br>
### Research Questions
>
- What is the growth rate of electric vehicle registrations over time and are certain vehicle types (BEVs vs. PHEVs) growing faster in specific areas?
- How do electric vehicle registrations differ between states and how might this relate to factors like population density, income, or urbanization?
- How do trends in electric vehicle registration or sales in the USA compare to other countries globally and do they indicate a change in environmental consciousness?

<br>
### Data Profile

#### EV Population Data from [Data.gov](https://catalog.data.gov/dataset/electric-vehicle-population-data)
>
##### Data Dictionary as per [The Washington State Open Data Portal](https://data.wa.gov/Transportation/Electric-Vehicle-Population-Data/f6w7-q2d2/about_data)
The dataset contains **209709 observations**, where each row is a vehicle currently registered through Washington State Department of Licensing, and **17 columns** which include:
- **`County [object]`**
    - Geographic region of a state that a vehicle's owner is listed to reside within (vehicles registered in Washington state may be located in other states)
- **`City [object]`**
    - The city in which the registered owner resides
- **`State [object]`**
    - Geographic region of the country associated with the record (addresses may be located in other states)
- **`Model Year [int64]`**
    - Model year of the vehicle, determined by decoding the Vehicle Identification Number (VIN)
- **`Make [object]`**
    - Manufacturer of the vehicle, determined by decoding the Vehicle Identification Number (VIN)
- **`Electric Vehicle Type [object]`**
    - Distinguishes the vehicle as all electric or a plug-in hybrid
- **`Electric Range [float64]`**
    - Describes how far a vehicle can travel purely on its electric charge
- **`Base MSRP [float64]`**
    - The lowest Manufacturer's Suggested Retail Price (MSRP) for any trim level of the model in question
- **`2020 Census Tract [float64]`**
    - The census tract identifier is a combination of the state, county, and census tract codes as assigned by the U.S. Census Bureau in the 2020 census, also known as Geographic Identifier (GEOID)

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart1_477.json" style="width: 90%"></vegachart>
<br>
<vegachart schema-url="{{ site.baseurl }}/assets/json/chart2_477.json" style="width: 40%"></vegachart>

<br>

#### EV Population by US County from [Kaggle](https://www.kaggle.com/datasets/sahirmaharajj/electric-vehicle-population-size-2024/data?select=Electric_Vehicle_Population_Size_History_By_County_.csv)
>
##### Data Dictionary as per Kaggle's [Data Card](https://data.wa.gov/Transportation/Electric-Vehicle-Population-Data/f6w7-q2d2/about_data)
The dataset contains **20733 observations**, where each row represents the vehicles registered by the Washington State Department of Licensing (DOL) each month between 2017 to 2024, and **10 columns** which include:
- **`Vehicle Primary Use [object]`**  
    - Describes the primary intended use of the vehicle, one of either Passenger or Truck  
- **`Battery Electric Vehicles (BEVs) [object]`**  
    - The count of vehicles that are known to be propelled solely by an energy derived from an onboard electric battery  
- **`Plug-In Hybrid Electric Vehicles (PHEVs) [object]`**  
    - The count of vehicles that are known to be propelled from energy partially sourced from an onboard electric battery  
- **`Electric Vehicle (EV) Total [object]`**  
    - The sum of Battery Electric Vehicles (BEVs) and Plug-in Hybrid Electric Vehicles (PHEVs)  
- **`Non-Electric Vehicle Total [object]`**  
    - The count of vehicles that are not electric vehicles  
- **`Percent Electric Vehicles [float64]`**  
    - Comparison of electric vehicles versus their non-electric counterparts  

#### Global EV Sales: 2010 - 2024 from [Kaggle](https://www.kaggle.com/datasets/patricklford/global-ev-sales-2010-2024/data)
>
##### Data Dictionary as per Kaggle's [Data Card](https://www.kaggle.com/datasets/patricklford/global-ev-sales-2010-2024/data)
The dataset contains **12654 observations**, where each row represents electric vehicle sales, stock, or stock share data for various regions of the world from 2010 to 2023, and **8 columns** which include:
- **`Region [object]`**  
    - Geographic region of the world either by country name, continent, etc.  
- **`Category [object]`**  
    - Type of data reading, either historical or IEA future projection  
- **`Parameter [object]`**  
    - Type of EV business/finance data insight—either sales, stocks, or shares  
- **`Mode [object]`**  
    - Type of vehicle  
- **`Powertrain [object]`**  
    - Main battery component type, such as BEV, PHEV, FCEV, etc.  


<br>
### Findings
**1\. What is the growth rate of electric vehicle registrations over time and are certain vehicle types (BEVs vs. PHEVs) growing faster in specific areas?**

<span style="font-size: 14px;">For regional trends of BEVs and EV adoption, I looked at registration counts and percentage for major counties and cities in the state of Washington. Counties like King, Snohomish, and Pierce along with the Seattle metropolitan area expectedly had the most EV registrations which aligns with population density. Then, I grouped and aggregated vehicle counts by county, vehicle type, and model year, before calculating the year-over-year growth rates for each EV type. This analysis compares BEV and PHEV growth rates to identify counties where BEVs are growing faster. The resulting barplot visualization lists the top 15 counties with significant BEV growth advantages. We see that Pierce, Thurston, and Spokane counties had the largest BEV Growth Advantage percentages over time. Finally, the last figure shows the growth trends of BEVs over different model years in the top 10 most populated counties of Washington State. The line chart highlights variations in Battery EV adoption across densely populated regions of Washington. From this visualization it is clear that King County, the 12th-most populous county in the United States, had the highest BEV count along with Snohomish and Pierce. Most counties show a gradual upward trend from 2010 to 2020 with a sharp decline around 2023.</span>


![alt text](/assets/pngs/477-q1-viz3.png)

![alt text](/assets/pngs/477-q1-viz4.png)

<span style="font-size: 14px;">In summary, the growth rate of electric vehicle (EV) registrations in Washington State has shown a clear upward trend from 1999 to 2023, with a slight decline in 2023 and 2024. Battery Electric Vehicles (BEVs) significantly outnumber Plug-in Hybrid Electric Vehicles (PHEVs) in registrations, with BEVs consistently showing higher growth rates. Regional analysis revealed that areas with high population density, such as King, Snohomish, and Pierce counties, have the largest EV registration counts. Pierce, Thurston, and Spokane counties also have the highest BEV growth advantage. This indicates that BEVs are growing faster in these counties compared to PHEVs, highlighting upward regional trends in EV adoption.</span>


### Analysis

We conducted research of these questions through Data acquisition, Data integration, Cleaning and Quality assessment, Python Pandas Analysis, and Data Visualization. 

Our findings show that there is significant growth in electric vehicle (EV) adoption in the United States over time, with Battery Electric Vehicles (BEVs) outpacing Plug-in Hybrid Electric Vehicles (PHEVs) in most regions. Densely populated counties like King, Snohomish, and Pierce in Washington State show the highest EV registration counts, while counties like Thurston and Spokane show faster BEV growth advantage rates. Comparatively, states like Arkansas and Iowa stand out with high EV density, which may be influenced by their lower population densities and other potential socio-economic factors. On a global scale, we found that the U.S. and China dominate the EV market. Countries such as Norway and Iceland are also leading, potentially due to their focus on environmental policies. The general upward trend in EV registrations and supporting infrastructure, both nationally and internationally, indicates growing environmental consciousness and an overall shift toward sustainable transportation.