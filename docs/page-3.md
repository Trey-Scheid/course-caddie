---
layout: page
permalink: /page-3/
show_sidebar: false
menubar: stages
title: Deployment and Use
subtitle: Stage 3
# hero_link: /fake/
# hero_link_text: ACE!
# callouts: ethic_callout
# pre_callouts: pre_index
# tabs: tabs
---

# Deployment

As mentioned previously, this model will only be trained and then used at the University of California San Diego. Course Caddie provides course recommendations to all students with enrollment access and will be integrated into that system for easy viewing. 

The tool ideally updates live with course enrollments, not suggesting courses that are full for example during first pass (although this is yet another decision). 

# Prediction Use


Being deployed in a Secure-Sign-On environment the main ethical concerns relate to the quality of predictions more than the security and privacy. The predictions which should be clearly visible to the student should be accessible only to them. Recommendations are personalized and should only be used by the student logged in, not for peers who happen to peek!


> ### Faculty View
> 
> One caveat, aggregate statistics could be shown to faculty and administration on what quantities and possibly demographics were show suggestions for their courses. This could be helpful for resource allocation, course preparation, and adjusted offerings. However, this may also lead to faculty gaming. Adjustments to course titles, descriptions, targeted "advertising" etc may be utilised to increase suggestability of their course taking away from the validitiy of the measurement methods (Goodhart's Law). This may be limited if they can only see statistics for their own course offerings, not very much data to go off of. 

When a student views the recommendations they should interpret the results according to the model metric. For example, if we use content-based filtering optimized for similarity among interactions or users or courses then a message indicating that would be useful. Alternatively, for black box methods it should be mentioned what data the recommendations are based on. Otherwise it may be confusing, students may look at the list and confuse them for requirements, available classes, popular classes, or other incorrect interpretations. 

This could ironically have the opposite effect, students may believe that courses which are not recommended to them are worse in some aspect. The output which only includes a small subset of total possible courses should not be a strict limiting factor for any student. The pattern here is that most student misuse stems from misunderstanding. 

## OverReliance

A major concern with a tool which reduces student work load is the over-reliance possiblities. Students may entirely replace their course research and use the course suggestions as a checklist. It may help to give the suggestions without any kind of order or rank. There should be a tooltips which after the disclaimers have links to course descriptions, availabilities and prerequisites for student research purposes. This keeps some skills available, can be an introduction to them for new students even, while advising they do not enroll blindly. Despite training efforts, the developers cannot ensure that skill gaps are closed, all requirements are hit and only classes which the student will be succesful in are recommended in. That means students still need the skills to do research on their own, discover new departments, majors, courses and faculty. 


# Revision

The education system although sometimes slow does change over time. The developer needs to stay engaged and aware of how this affects the application, not just functionality but generalizability and perfmormance. These are some examples of when an intervention would be needed.



## Data Sources

The system relies on a wide array of data from various sources. These sources need to be kept up to date on their cleaning and connection points. UC San Diego recently went through a transition on feedback systems which would have required a revisit to how the data was preprocessed and possibly which features were selected. 

Developers should pay attention to additional sources, if student, faculty, or course, profiles get beefed up by other internal systems or efforts they can be leveraged for stronger personalization. This might look like additional student surveys for new students, this could lead to better cold start performance so developer attention here is key. 


### Biases

As mentioned in other stages, the outputs need to be monitored to ensure they are reducing injustice. Minimally is should be an analysis of student demographics within outputs including highly relevant characteristics such as units completed, degree program, and academic history. Survey (comments or recommendation reactions) or structured experiments collect feedback on outputs. Both the quantitative and qualitative feedback validates the goals of Course Caddie and leave room for stakeholder involvement. 


### Application Limits

The project should be abandoned in a few circumstances. In particular, with low performance where recommendations are rarely followed even in successive quarteres, where injustices are made worse, or if the model is severely underfit due to scarse data or other issues. If the model cannot perform where any recommendations are useful, where it lowers student research time and is expanding their knowledge of offerings. Then it would be misleading and a baseline with no recommendations would be preferred!  

<!-- describes appropriate and inappropriate contexts-of-use for the model
H. explains how to interpret the model’s outputs, perhaps in a context-sensitive manner
J. describes and explains at least two potential situations—contexts, uses, etc.—in which the model should be updated or revised (perhaps no longer using it) for ethical reasons --> 

