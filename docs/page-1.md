---
layout: page
permalink: /page-1/
show_sidebar: false
menubar: stages
title: Data Collection
subtitle: Stage 1
toc: true
# hero_link: /fake/
# hero_link_text: ACE!
# callouts: ethic_callout
# pre_callouts: pre_index
# tabs: tabs
---
# Data

## Data Types

What data might be useful to predict someone's best next courses to take? In general it may look like: degree program, previous courses (including how they performed and if they liked it), and most importantly, what is being offered. 

    This challenge requires historical data of student enrollments, academic performance, details about students as people, and lastly scraped information about each department (offerings and requirements). Previous enrollment and current requirements are the bare minimum to address the challenge while information about individuals and past performances on enrollment data aims to improve and personalize recommendations (this is a tradeoff with added responsibility).

Faculty/Course ratings can also be considered to truly mimic and reduce student selection process. Feature selection later may be advantageous, some variables such as this could be correlated with enrollment numbers etc. 

## Methods of Collection and Measurement

The focus of Course Caddie initially is deployment at UC San Diego, and therefore we can tap into the existing collection systems as long as we make some assumptions and get access. Here is the summary of data sources:

| Name                     | Source           | UCSD                 |
|--------------------------|------------------|----------------------|
| Planned Course offerings | Department Sites | ucsd.edu             |
| Degree Requirements      | Internal         | Degree Audit         |
| Interests                | Survey           | Profile, CCR etc.    |
| Ratings                  | Student Reviews  | CAPES/SETS/3rd party |
| Academic History         | Internal         | Academic History     |

These inputs each have flexbility and nuance and their own concerns. However generally we believe they contain enough information about a person and the course environment to predict what a student would find through their own research, and maybe even more!


Course Caddie will start as an internal tool with no outside motivations aside from serving the students with the best recommendations. Based on other UCSD initiatives, student given _consent_ through enrollment includes the use of our data for such developments. This is a huge benefit: infrastructure already exists through SSO that secures and protects individuals data while allowing for aggregation and modelling within. Students have profiles which include their registered major and/or minor programs including a breakdown of what they have completed and what can be used for credit towards them. Their is a history of their grades including optionally given course feedback. These measurements are almost entirely qualitative, with little room for instrument error or loss of precision. However, the issues become how to interpret and handle these types of data considering the meaning in light of stakeholder values. 


# Considerations

A main concern with data collection is its purpose. Our model ideally provides a way to give _personalized_ recommendations to future students, which requires detailed and accurate descriptions of relevant information for *all* demographics. In particular we need enough data that all new students will have a _useful_ tool[^1]. Keep in mind a senior (by units) has only completed around 35 courses worth (data points) while a freshman has (near) 0.

These considerations all focus on the quality and availability of data. They relate to the downstream generalizability which steams from population represenation during collection. This assumes that all data is already collected and consented for use through the university, otherwise in further application areas there may be many more complications!

## A. Data Representation

The data needs to represent the students' ideal choices given current constraints, however, the data we have access to only indicates the union of their ideal, with reality (course availability). This distinction means that data collected does not capture ground truth, there is a bias towards available classes. This bias can be impacted by enrollment time (credits completed/age), course size, and annual frequency of offerings.

### Response

To tackle this concern, Course Caddie ought to incorporate rating information as well as pure enrollments. Some students may enroll in courses they did not want initially. We could consider collecting an entire new dataset including survey questions asking students what they wanted, add a tool in the enrollment for ranking, planning etc to capture this. This would be at the expense of suggesting classes that are practical as well as ideal choices. The developer can decide to play with this tradeoff, the baseline would be using the minimum viable data, whats already being collected, and checking performance with that. Specifically, a post hoc analysis checking for enrollment time (or credits completed) vs performance to find any subtantive algorithmic unfairness.

## B. Cold Start

1. The cold start problem is a common one among recommender systems, when a new subject lacks any history to allow for personalization. This becomes an ethical issue since it unfairly gives worse recommendations to incoming freshman who need the most help selecting classes. This problem appears during deployment however is due to collection issues. It is a hard problem because you cannot directly change that a freshman will have taken any specific University course and given it feedback. The effect of this disparity could lead to worse scaling effects of recommendations depending on how this is handled. For example, if popular courses, or the entry courses for their GE's or major are defaulted as the recommendations for all new subjects this would lead to a large portion of the population recieving an identical recommendation, enrolling in the same courses and not suggesting any variety. This would lead to impaction, false sense of security in course availability as the recommendation has changed the dynamics of the enrollment landscape. This default solution therefore introduces new problems.

2. The cold start problem can occur for courses and faculty as well. Missing data in these categories means that the system may not have any information which would lead it to suggest the course. This means that interesting, requirement fulfilling. This leads to problems as only recommended courses may get filled, only experienced, motivated students will find new offerings, and generally new biases will be introduced. 

### Response

1. This concern is not as problematic as it seems! The freshman lack experience selecting classes for themselves, but they have the most requirements to fullfill. One technique people learn is to target GEs, explore their major lower divisions and follow plans made by their advisors. This indicates less reliance on a recommender system, and priotizes historical data of other types besides personal (what other freshman have done). The recommender system may recommend an identical reponse to all students, but they will be able to check the only source they know, their GE or department requirements to find another replacement. If possible, the system could tag courses that are more likely to fill up fast using some color or marking system on its outputs.

2. The baseline currently exists where students must do their own research to determine what classes to take, this should lead them to discover new course offerings through the enrollment site, department offerings and newsletters. The issue with these courses never being discovered then moves to a deeper one: model over-reliance. This bias hopefully can be overcome in later stages through efforts like messages about lack of comprehensibility, model tuning to prioritize breath with new offerings. 

## C. Update Speed

One more challenge the data poses for Course Caddie is the temporal volatility. Courses, Students and faculty all change each quarter, sometimes drastically. Under the same profile these subjects may have conflicting information between historical and current: if students switch major, a course may be restructured, a teacher may adopt new methodologies or policies. This issue will lead to a performance cap on the model. It becomes an ethical issue when these misleading recommendations are not randomly distributed.

### Response

The best a system can do here is to adapt to the new conditions. This means incremental learning, a sort of weighted short term memory which considers new data as more informative. The diverse approach with varying sources should help offset dramatic changes in one area, however it can still lead to misleading suggestions. 


[^1]: See Analysis for evaluating the recommenders. 

<!-- [] at least two significant (potential) ethical and/or societal concerns -->
<!-- [] responses to these concerns -->