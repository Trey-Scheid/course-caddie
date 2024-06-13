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

### Output

The model output format is complicated decision. Assuming that we restrict our model to output the top X ranked recommendations based on most similar, most appropriate course offerings. (The rank condition may vary depending on the model). 
- One way to evaluate model results is to create a binary feature that tracks if the student enrolls in and passes at least one suggested course, or not. This choice reflects a desire for practical suggestions which lead to courses theres space for, and the student is succesful in.  
- Another method is to track how many courses students add to their cart/plan within the enrollment system. This prioritizes student interest in a course over the feasibility, this is more susceptible to noisy data considering behavior may include arbitrarily planning or not planning all the courses: this is not a perfect proxy for interest. 
The choice of X is also an ethical one. For small values 1-3, would injustices really be lowered, would more breadth classes ever reach the top? Would popular courses that gauruntee high interest due to name recognition, or easy grades intice enrollment? For large values 5-10 would students use the tool the same, spending effort to double check the course details (getting into Use), if not then would low energy or confused students still gain the benefit of the system? Low to high also affects the algorithmic optimization as the model has more or less flexibility. Forcing the model to choose a contant number of predictions is also a choice, (compared to thresholding), because, choosing one value creates these tradeoffs in the first place!

### Metric

Naturally, metric coincides with output format. The choice of metric has many implications on whose values are most supported and which biases we would rather handle. Make sure to research for your specific model what the tradoffs are for metric choices and test, maybe with post-hoc tools again, for demographic differences in output quality for each. A way to make this comparison of "output quality" would be a positive criteria for each metric if it leads to better performance on your chosen evaluation principle from the last discussion point (i.e. passing grade).

<!-- E. identifies at least two different potential ethical concerns about analyzing/modeling these
data for that goal
F. explains how you would respond to the concerns in E. through choices in the analysis phase -->

[^1]: This is a made up/non-technical term!