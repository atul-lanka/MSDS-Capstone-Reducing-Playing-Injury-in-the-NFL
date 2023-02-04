# MSDS-Capstone-Reducing-Playing-Injury-in-the-NFL
This project highlights 3 primary factors in the NFL for increased player injury - playing surface, punt return plays and multiple helmet to helmet collisions - and offers subsequent solutions to tackle each one


# Overview 
Injuries from the 2019 season have been attributed to over $500 Million dollars in expenses incurred by NFL teams according to Forbes. The quantity of injuries combined with the revenue ramifications present a unique opportunity to more heavily scrutinize the data surrounding player injuries and implement substantial changes in order to keep players healthy and in the game. Our project’s focus will be just that; analysis of injury data from past years through various regression analyses and Computer Vision to gain concrete recommendations and actionable insights that will lead to the reduction of player injuries and, in turn, minimize the injury-related expenses incurred by teams.

There are 3 key areas of focus that we narrowed this report down to. Given that football is a contact sport and we can’t change the very nature of the sport, our criteria was to mitigate injury where we deemed it was most avoidable. 

1.	Non-contact lower limb injuries that are sustained due to differences in playing surfaces – natural grass vs synthetic grass
2.	Players suffering concussions on punt return plays – both teams are running at each other full speed.
3.	Multiple helmet impacts that are generally sustained near the line of scrimmage – where the linebackers stand right as the play commences. 

For each of these sections, we will not only provide detailed analysis but also include solutions and recommendations. In addition, we will address rule changes, provide a dashboard as well as an app, and future investment or partnership opportunities to curb these injuries in the long term.


## Surface Analysis
 ![image](https://user-images.githubusercontent.com/74167574/216740175-2db5b4de-d571-4279-8c09-b5bd7c23022b.png)
 <img width="519" alt="image" src="https://user-images.githubusercontent.com/74167574/216740272-49cd1147-8d70-4c97-a845-08786f3da858.png">
<img width="470" alt="image" src="https://user-images.githubusercontent.com/74167574/216740283-e34885c0-9f17-43e0-8fe3-01142c38d413.png">

With no clear evidence that either surface benefits the players, designing cleats for each surface should be prioritzed. 

![image](https://user-images.githubusercontent.com/74167574/216740326-a0a3fa61-f5f2-431c-87de-f77836272b15.png)

### Tableau Dashboard

As mentioned in the Surface Analysis Management recommendations, an interactive dashboard was developed using Tableau software. It allows the user to filter through three different data elements to produce a “Forecasted Number of Injuries per Game” and then compares this number to the Average Non-Contact Injuries per Game of 0.311 to return the percent difference.   Below is an example of two different scenarios involving the Denver Broncos with different Weather and Temperature Settings 
 ![image](https://user-images.githubusercontent.com/74167574/216740391-d7c598d9-1945-4f26-aa81-d6209025589b.png)
 ![image](https://user-images.githubusercontent.com/74167574/216740413-83752c37-c00a-460a-a69c-27b1996dea1d.png)


## Helmet Impact Analysis
### Impact Occurrence 

Helmet impacts were determined from 2 camera views - Endzone and Sideline

From these frame by frame distribution plots, it appears most of the helmet impacts occur within the first second of the play and start to taper off as the play develops further. 
<img width="438" alt="image" src="https://user-images.githubusercontent.com/74167574/216740684-d62497cf-a4cb-4a83-bcce-e3bc63813140.png">
This is further reiterated in the second figure below, where the number of bounding boxes, or helmets visible in the frame significantly take a dive after 4 second mark. Our understanding is that once the ball is snapped, the players disperse from their formation which explains the number of helmets in the frame reducing. ![image](https://user-images.githubusercontent.com/74167574/216740692-bf44a7b6-115a-4e69-9468-cbd50c92ae7e.png)
<img width="449" alt="image" src="https://user-images.githubusercontent.com/74167574/216740698-2c935ede-a4e2-47da-9d26-eb3ef54d8690.png">

### Impact type
It is important to note that Helmet-to-Helmet impacts are the worst because of concussion risks for both players. With nearly 2/3rds of all helmet impacts being of that nature, that is a glaring issue the NFL needs to address.![image](https://user-images.githubusercontent.com/74167574/216740718-aa71116e-8333-4c4b-866f-0392bc4af9b3.png)
<img width="482" alt="image" src="https://user-images.githubusercontent.com/74167574/216740724-bd535b57-bb65-4d80-9e91-846cd1d71245.png">

###Computer Vision Model / Solution Overview

We created an application, hosted on Streamlit, to detect possible helmet collisions. Our solution consists of a two-step pipeline - detection and classification - We use 2D detection to find possible impact boxes, and then we use 3D classification to determine which boxes are impacts.

We used the DetectoRS(ResNeXt-101-32x4d) model for detecting impacts. Our detection model outputs the red box as a possible helmet impact.

<img width="470" alt="image" src="https://user-images.githubusercontent.com/74167574/216740943-d109ffca-2a32-44e8-9d23-9a678ede49dd.png">
After processing this video, the computer vision model we deployed onto this application will output a video that should apply a box over every player’s helmet. These boxes will flash red once the model determines that there has been a helmet impact.![image](https://user-images.githubusercontent.com/74167574/216740956-a62d5684-a2b1-4c40-a663-ed0ba9bdd359.png)
<img width="470" alt="image" src="https://user-images.githubusercontent.com/74167574/216740931-837018e9-e9c0-4d8a-8df3-67bb178f57a8.png">

Once the model has generated the output video, a player tracking table is also created. This summarizes the players that have sustained a helmet impact and also provide some tracking data for the approximate moment the player is struck on the helmet. ![image](https://user-images.githubusercontent.com/74167574/216740966-6a22a020-f8cb-4220-9b67-19395a7e0f4a.png)
<img width="468" alt="image" src="https://user-images.githubusercontent.com/74167574/216740970-f2d43fcb-bf34-49c7-98c1-75e6b315baa1.png">







