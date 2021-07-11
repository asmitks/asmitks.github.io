---
layout: post
title: Is a Democrat more likely to wear a mask than a Republican??
cover-img: /assets/img/demorepub.jpeg
subtitle:  Unmasking the partisan combat, an analysis through Instagram
tags: [Analysis, pandas, Deep Learning, Instagram, OSN, Public Health, Covid-19]
image : /assets/img/alluvial.png
comments: true
---


## Introduction
The COVID-19 pandemic has drastically changed life in the world including, United States, with the country recording over 32.3 million cases and 574,000 deaths as of April, 2020. With the ongoing widespread vaccine rollout, the adoption of non-pharmaceutical interventions like mask-wearing mandates and stay-at-home laws have proved to be critical for stopping possible transmission routes.

In the lead-up to the 2020 presidential elections, mask-wearing and social distancing had become a partisan issue. According to Pew Research, people who lean Democratic are more likely than Republicans to say that they wore a mask, with conservative Republicans, being amongst the least likely to say they wore a mask, while liberal Democrats being amongst the most likely [2]. A significant difference was found between the percentage of people saying they wore a mask vs the percentage of people who said they saw others wearing a mask in the USA. Hence, quantifying the number of people actually wearing face-covering or following social distancing is a challenging task, which currently relies on on-ground surveys, or self-reported numbers [1]. Through this research, we move to social media for answers.

With its ease of access and global outreach, social media has a disproportionate influence on disseminating information during the COVID-19 pandemic. The general public and authorities have been using hashtags like #CoronaOutbreak, #COVID19, and #mask to disseminate important information and health advisories, which provides us with an opportunity to analyze behaviours. Realizing the potential of social media in capturing such events, we collect and utilize 3.9 million posts from Instagram to check for differences in mask-wearing and social distancing patterns between democratic and republican states.



## Data
We collected public Instagram posts for the 4 most democratic states (Vermont, Maryland, California, and Massachusetts), and 4 most republican states (Wyoming, Oklahoma, West-Virginia and North-Dakota) by vote percentages in the 2020 presidential elections between 1st March 2020 and 1st December 2020, in order to capture the buildup to the elections. The data was collected through crawling Instagram’s explore location page. For a given state we collected data for the state’s location along with locations for some of the most populous cities in the state. The figure presents the location wise data collecte

![Alluvial Diagram](/assets/img/alluvial.png)


We collected a total of 3,917,955 posts of which 78.3% (3,067,740) of the posts were collected from Democratic states, while 21.7%(850,215) of the posts were collected from the Republican states. This disparity in the number of posts is in line with the low number of Instagram users from the top 4 Republican states as compared to the top 4 Democratic states. Since our analysis is based on ratio and percentages, this difference in number was not a major issue.

## Analysis
To look at the political conversation going on in the collected data, we plot word clouds of the top political hashtags collected from the captions of posts from the Democratic and the Republican states.


![Alluvial Diagram](/assets/img/wc1.png)

We observe a higher occurrence of hashtags like ‘bidenharris2020’, ‘trumpsucks’, ‘dumptrump’ in the captions of posts collected from Democratic states, while captions from the Republican states include hashtags like ‘trump2020’, ‘trumpsupporters’ in higher numbers. The partisan polarity in these states is captured in the above hashtags effectively.


![Alluvial Diagram](/assets/img/wc2.png)

In order to see how differently the Democratic states and Republican states reacted to the pandemic in terms of face-coverings and social distancing, we plot a timeline of the average percentage of people wearing masks and group pictures. A group picture is defined as a picture with greater than or equal to 2 faces detected. Group pictures are used as an estimator of adherence to social distancing measures.


![Alluvial Diagram](/assets/img/anbalysis1.png)

We observe that the percentage of group pictures starts at around the same level for both Democratic and Republican states and diverges as the pandemic grows. The Democratic states have a lower percentage of group pictures, indicating a more likely behaviour to follow social distancing measures. The difference in the daily average percentage of group pictures for Democrats and Republicans was found to be statistically significant.

![Alluvial Diagram](/assets/img/analysis2.png)

Both Democratic and Republican states show a jump in the percentage of masks, at the beginning of the pandemic, but as the pandemic grows Democratic states show a higher percentage of people covering their faces online as compared to Republican states. The difference in the daily average percentage of masks detected for Democrats and Republicans was found to be statistically significant. This indicates higher mask-wearing among Democrats as compared to Republicans.

## Discussion

Our analysis of Instagram finds significant differences between Democratic and Republican states in reaction to non-pharmaceutical interventions against COVID-19. Our findings support the existing on-ground and self-reported surveys, showing significantly higher adoption of face-coverings and social distancing, by Democratic states as compared to Republican states. This goes on to show the relevance of Social Media as a critical tool for understanding and tracking real-world events and sentiments of the population.

[Preprint](https://link-url-here.org) submitted to JMIR

## Team
- Paras Mehan
- Dr. Ponnurangam Kumaraguru
- Dr. Tavpritesh Seth