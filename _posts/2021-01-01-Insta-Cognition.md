---
layout: post
title: Instagram Cognition
cover-img: /assets/img/cov.jpg
subtitle:  Social Media Analysis for tracking location wise masks and collction of people.
tags: [Analysis, kibbana, elastic, Instagram, OSN, Public Health, Covid-19]
image_cover : /assets/img/instagram.png
comments: true
---


## Introduction
The adoption of non-pharmaceutical interventions and their surveillance is critical for detecting and stopping possible transmission routes of COVID-19. A study of the effects of these inter-ventions in terms of adoption can help shape public health decisions. Social media analytics can offer crucial public health insights. The methodology used provides a directional indication of how government policies can be indirectly monitored through social media. This tool can be used to gauge traffic at a location, along with other statistics, including the number of mask wearers and number of group pictures, using posts scraped from instagram's explore page.
![Alluvial Diagram](/assets/img/main.png)

we develop a django based web application as an analysis tool for various organisations to see location wise trends in any particular through instagram images. Number of posts, group pictures and number of masked faces can be used as
indicators for analysing adherence to various policies.

## Data
We collected public Instagram posts for any desired location. The data was collected through crawling Instagram’s explore location page. All the available reports worldwide are visible in the explore map


## Pages
### Explore Page
The explore page presents the user with a screen-wide world map with markers placed at different
locations. These locations are the ones whose data we have collected and analysed. The user
can zoom in and out of the map, and select the marker. The user is redirected to the report
page for the particular location.

![Alluvial Diagram](/assets/img/map_page.png)
### Explore Page
On the request page the user is presented with a basic form to submit request for the location
the user want to see the summary report of.

![Alluvial Diagram](/assets/img/request.png)

### Report
This is the most information dense page in the application. On being redirected from the map
marker, A report is opened for the user. The report consists to two sections. The upper section
of the report page shows the name of the location and an array of images. The images are a
random selection of posts collected from the specific location.

![Alluvial Diagram](/assets/img/report-cov.png)
The second section of the report contains the snapshot from the Kibana dashboard. The Kibana
dashboard consists of the following visualisations
- Day wise timeline of the collected posts.
- Wordcloud of the most occuring hashtags in the post captions.
- Weekly and daily average percentage of masks.
- Daily trend of the average number of group pictures.

## Data Pipeline
The following steps are involved in the collection and processing of data in this dashboard.
- The location is collected from the user.
- The Graphql based instagram scraper scrapes the location page within the chose time range.
- The scraped data and images are stored in a server, the data is stored as jsonls, while the images are sent to the mask classifier.
- The results from the mask classifier and the original data are combined and saved into the elastic search database.
- The Kibana dashboard accesses data from the elastic database and the snapshot of the kibana dashboard is sent to the django application.
![Alluvial Diagram](/assets/img/pipeline.png)

[Preprint](https://preprints.jmir.org/preprint/26868) submitted to JMIR

## Team
- Paras Mehan
- Dr. Ponnurangam Kumaraguru
- Dr. Tavpritesh Seth