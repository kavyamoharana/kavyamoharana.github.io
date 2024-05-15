---
name: The Heart of CampusTown - Analyzing Green Street’s Most Popular Restaurants
tools: [Python, NLTK, Scikit-Learn]
image: assets/jpegs/campustown-2.jpg
description: Project using Python's NLTK library for text sentiment analysis of Yelp reviews for popular UIUC restaurants
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

## The Heart of CampusTown: Analyzing Green Street’s Most Popular Restaurants
*Final project for [CS 410](https://cs.illinois.edu/academics/courses/cs410): Text Information Systems at UIUC*

Group Members: Pranav Chandra, Kavya Moharana, Sriya Mikkilineni, Aryan Vaswani

#### Abstract
Green Street’s wide variety of restaurants and cafes is an integral part of student life at the University of Illinois at Urbana-Champaign. Known as the “Heart of Campustown”, these establishments provide an important cultural and social hub for students, faculty, and residents. We intend to conduct sentiment analysis of the Yelp reviews for multiple major restaurants on this historical street. We will analyze online reviews over time periods to determine how students and food enthusiasts perceive these restaurants. Through this evaluation, we can see how the reception of these popular food spots has changed over the past decade.

#### The Data
We utilized two different datasets during this project: the first from [Kaggle](https://www.kaggle.com/datasets/hhalalwi/yelp-light) for the testing of five different models and one for the evaluation of our actual project. To understand why we needed two  models, we need to look at [Yelp’s GraphQL API](https://docs.developer.yelp.com/docs/graphql-basic-usage) documentation. For this project, we have identified 12 restaurants on Green Street for which we were interested in understanding peoples’ sentiments towards them over time, as shown in Figure 1. However, because Yelp API is still in its beta stage, we are limited to only the first three reviews on each restaurant's Yelp page. While severely limits our ability in trying to understand Champaign’s preferences, our code still shows sentiments over a couple of months. When the API limits increase, we would only have to re-run the code as is to get all the data.

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart2_410.json" style="width: 100%"></vegachart>
Figure 1

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart1_410.json" style="width: 100%"></vegachart>
Figure 2