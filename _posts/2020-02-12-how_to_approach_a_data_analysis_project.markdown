---
layout: post
title:      "How to Approach a Data Analysis Project"
date:       2020-02-13 02:55:53 +0000
permalink:  how_to_approach_a_data_analysis_project
---


Our first project at Flatiron School is now wrapping up and it has been a very exciting process! I have learned a great deal about data analysis, including how much there still is to learn. Our first project was centered around a hypothetical scenario in which Microsoft is interested in entering the film production business as other tech giants have been doing in recent years. Students were provided with the necessary data to begin to understand what makes a successful movie in the box office. Let us know explore the generic outline for conducting a data analysis project using the Microsoft Movie project as an example. 

**Step 1: Domain Research**

As with any data analysis project the firs step is *domain research*. Unless you are already an expert in the project's domain this is a critical step in the process. It is simply not possible do do effective data analysis without understanding the context of the problem. For the Microsoft Movie project I began exploring how, and how often, profitable films are produced, and which key crew members perhaps contribute the most to this. Once sufficient domain research has been conducted it is possible to formalize the goal of the project. 

For this project, the formalized goal was to maximize profitability, specifically return on investment (ROI) as defined by the worldwide gross revenue divided by the production budget. The assumption here is that these films were to be produced and premier in theaters. A note was made that this definition of ROI is not a perfect metric as it neglects other forms of of revenue such instant video rentals and video subscription service deals. On the other side of the equation the *production budget* is just that - production buget. This buget is entirely separate from the *promotional budget* which deals with costs associated with advertising and marketing which can be significant. 

Note that none of these insights would have been possible without doing the bare minimum domain research. 

**Step 2: Review Available Data (and possibly search for more if neccessary)**

The next step was to review our available data and try to identify which parameters could contribute to a profitable film. Given thousands of rows of tabular data in different tables it can be a bit overwhelming at first, however, it is easy to piece together once you began looking at small chunks. 

For the Microsoft Movie project the process was as simple as importing the available data, viewing the first few rows for each table, and thinking about what types of questions that data could answer which could be useful in reaching our goal (creating films with maximum rates of return). 

If you feel that the data you have available in insufficient reach our goal then it may be neccessary to go out and find more (or more relevant) data. 

**Step 3: Get to Know Your Target Variable**

The next step of this process is to *get to know your target variable* (ROI for the Microsoft movie project). If the target variable is numerical look at it's distribution and summary statistics. Just how common are profitable movies? How often will we get a blockbuster, homerun 20x return? Are there any correlations between our target variable and independent variables? Try to answer these questions with easy to understand visualizations for the non-technical stakeholders. 

**Step 4: Formalize and Answer Your Questions **

The third step is to formalize the questions you would like to ask of the data. This is partially done in step two, however, now is finally the time for formalize and answer these questions. This may be up for the debate, however, my process is to first figure out the questions I want to answer and *then* figure out what data I need and how I'm going to "clean" it. There is no sense in prepping a ton of data that is not going to be used to answer your questions. Once the data is clean all that is left to do is the analysis itself. 

**Step 5: Make Reccommendations and Suggest Further Work**

Finally, it is time to convey to the non-technical stakeholders how our questions will lead us to accomplishing our goal and to make recommendations based on the answers to said questions. Again it is import to make these recommendations using easy to conceptualize visualizations which offer *clear* answers to our questions posed. 

In an effort to stay employed it is also wise to offer up what further work can be done on the problem and how it will contribute even more to reaching the goal. All jokes aside there are numerous angles from which to analyze data, not to mention even more data "out there", and it is impossible to explore every angle under the time constraints of a professional project.

That is all to put it very briefly. Five steps to solving your first data analysis project. 
