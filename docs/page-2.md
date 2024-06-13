---
layout: page
permalink: /page-2/
show_sidebar: false
menubar: stages
title: Data Analysis
subtitle: Stage 2
# hero_link: /fake/
# hero_link_text: ACE!
# callouts: ethic_callout
# pre_callouts: pre_index
# tabs: tabs
---

# The Model


A recommender system can take a few forms, however this analysis will be model agnostic. Many ethical issues are universal (compared to model specific). The assumptions we will make about Course Caddie includes that it takes the data listed previously with information up-to-date to the previous school quarter except course grades/feedback.


## Analysis

Data wrangling, preprocessing, and feature selection involve many developer decisions which should encode stakeholder values. Some concerns tie in with discussions from the Collection stage. The temporal weights for the data in particular is an important decision that impacts generalizability and justice for newer courses and people. A large problem lies in feature selection. The choice of data sources to be included may restrict the model choices, for example a large quantity may be needed for content-filtering or GNN methods to be successful. This may come at the cost of including course ratings which could lead to biases against faculty and only include the voice of a subset of students. Even decisions about how to store the data, or how much granularity to include could impact the results of the model (justice and performance). 


### Response

We will discuss how model revisions can be made, but some choices on how to store data are destructive and irreversible. For this reason planning is paramount. If budget constraints allow, ideal if it is already being stored, then keeping all the listed data unaltered for experimentation and pivots would be keen. One effective, but not efficient, method to handle these concerns is a reductive technique[^1]. Start with all the data use for example a linear based model (SVD) or explainability post hoc methods (SHAP) to determine which features have the largest impact for some sample + edge cases. This raises an important point relating to a developer tradeoff for finite resources against thoroughness.  



## Evaluation


The choice of metric has many implications on whose values are most supported and which biases we would rather handle. 

<!-- E. identifies at least two different potential ethical concerns about analyzing/modeling these
data for that goal
F. explains how you would respond to the concerns in E. through choices in the analysis phase -->

[^1]: This is a made up/non-technical term!