# StudentPerformanceAnalysis

<b>Introduction:</b>

The data given was collected from a fully online nine-week-long course on machine learning. The goal of this mini-project is to use two different approaches to predict students’ final grades in an online course. 

<b>Data collection</b>
The given data contains several types:

•	Status0: course / lectures / content related

•	Status1: assignment related 

•	Status2: grade related 

•	Status3: forum related 

•	9 grades 

•	Overall, 36 logs 


The dataset was placed in Google Drive folder, to make access to it as easy as possible.
In the dataset, there is a missing value, namely week1_stat1. The reason for that is the fact that there were no assignments nor deadlines for the first week. So it is empty for the reason.
Another thing to mention, some students seem to take the class but did not participate in-class activities. Thus, they don’t have any grades and might be considered as empty values.

But in my opinion, we cannot disregard such students, because maybe they have this course as mandatory, so they should get the mark they deserve – 0.

<b>Feature selection</b>

Feature selection was based on logic and requirements:
1.	In the project description it was said that we should use week8_total because it is an overall grade.
2.	All features of Status0 group contains course-related information, that has no effect on grade. Therefore, it is not useful information for grade prediction, and we have to drop it.
3.	All features of Status1 group contains assignment-related information, that has no effect on grade. Therefore, it is not useful information for grade prediction, and we have to drop it.
4.	All features of Status3 group contains forum-related information, that has no effect on grade. Therefore, it is not useful information for grade prediction, and we have to drop it.
5.	All grades (Week2_Quiz1, Week3_MP1, ... Week7_MP3) affect directly grades of students, so we choose those features to perform machine learning
6.	For understanding if the predicted grade was the correct one, the machine will compare it with the Grade field in the dataset

After dividing the dataset into the training set and testing set, grade prediction was performed with the help of two different approaches: Random Forest and Linear Regression.

•	<b>Random Forest</b>

We don’t have a large dataset (only 107 enrolled students), so we can already predict that prediction may be not that accurate as other methods.

Random forest was successfully implemented and the performance of grade prediction we can see in fig.1. (Note: in this scenario, we did not have a grade 2 in the testing set, so we don’t have it in the table of predicted grades)

Accuracy of the model: 0.8000.





![image](https://user-images.githubusercontent.com/90958123/156223844-ef4b1235-bfa2-4bdf-8b98-aa21f9ca1bf4.png)






Fig. 1. Predicted grades, Random Forest. 


•	<b>Linear Regression</b>

Linear regression is used when we want to show or predict the relationship between two variables or factors. In our case – overall score from activities (Week2_Quiz1+ Week3_MP1+ ... + Week7_MP3) and actual Grade. 
For that purpose another column was created for storing scores of students called “Total”. In figure 2 the perfomance of predictions can be seen. 

Coefficient of determination: 0.95.





 ![image](https://user-images.githubusercontent.com/90958123/156223875-9ad9a2fd-2563-449d-bbae-d574ece2be2d.png)
 
 
 
 
 
 
Fig. 2. Linear Regression Output.


Comparing accuracy of two models, we can see, that Linear Regression was more accurate during grades prediction (see fig. 3).




 ![image](https://user-images.githubusercontent.com/90958123/156223906-89ba78fc-5203-4b69-b79c-f6c37e1617c4.png)
 
 
 

Fig. 3. Comparing accuracy of two models.

The linear regression did a better job at prediction because Random Forest is used in much larger datasets than the given one. Obviously, Random Forest Classifier will perfume a bit less effective. As for linear regression, the size of datasets in that sense doesn’t matter.

By visualizing feature by the order of importance in grading the student (see fig. 4), we can see, that three most important features are: 

•	Grade for mini project 3

•	Grade for mini project 2

•	Grade for mini project 1


The visualization was made with the help of bars in order to make it more understandable for users.  




 ![image](https://user-images.githubusercontent.com/90958123/156223947-9943e97c-2622-4755-9f80-04644157a0f3.png)




Fig. 4. Importance of feature in grading. 

<b>Conclusion</b>

The bottleneck faced:

•	Linear regression was not performing well in the first try. After correcting the testing set (making sure that it is not all zeros), the model performed perfectly. 

•	For the linear model the overall score for every student was created to get input X value 

In the conclusion, two models were built and two variations of predictions were made. 
