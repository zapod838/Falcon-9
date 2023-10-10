# SpaceX  Falcon 9 first stage Landing Prediction

### Summary

This project is a part of IBM's Data Science Professional Certification on Coursera. Throughout this project, conducted an in-depth analysis of SpaceX, known for significantly reducing aerospace manufacturing and launch costs by over 50%, with projections of a 99% reduction upon the completion of the Starship project. 

The analysis seeks to explore and validate SpaceX’s cost-effectiveness and the feasibility of their reusable booster technology in sustaining long-term market leadership and cost-efficient space exploration. 
Finally, achieved certification in Data Science from IBM, which was pursued and completed within six months, demonstrating a commitment to continual learning and skill application.

-------

### Approach

#### Data Collection and Data Wrangling Methodology
* Utilized the SpaceX API to get information about the launches such as rocket (Booster name), payloads(Mass of the payload), launchpad(Launch site), and cores(Landing Outcome, landing type). 
* Filtered the data-frame using the “BoosterVersion” column to only keep the Falcon 9 launches.
* Missing “PayloadMass” values were replaced using the .mean() function.
* Launch site “CCAFS SLC 40” have maximum number of launches, 55 and “VAFB SLC 4E” have the least launches, 13.
* While the highest number of landing took place on drone ship, 47, out of which 41 were successfully landed and 6 failed to land successfully.
* Created “Class” column which represents success outcome of each landing. Calculated success rate using Class column which comes out 67%.

#### EDA and Interactive Visual Analytics Methodology
* Used seaborn Python data visualization library based on matplotlib to plot scatter plot and bar plot.
* Utilized the function catplot to plot “FlightNumber” vs “LaunchSite”, set the parameter  hue to 'class’ to visualize the relationship.
* Likewise, the function scatterplot is used to plot the relationship between different parameters such as payload mass, launch site, flight number, orbit and outcome.
* Applied “groupby” method on Orbit column and get the mean of Class column then plotted bar chart to find which orbits have high success rate.
* Plotted a line chart with x axis as the extracted year and y axis as the success rate and observed that the success rate kept increasing since 2013 till 2020.

#### Predictive Analysis Methodology
* Used the function “train_test_split” to split the data X(Train data) and Y(Test data) and set “test_size” to  0.2 and “random_state” to 2.
* Created a logistic regression object then created a “GridSearchCV” object (“logreg_cv”) with cv = 10. Found the best parameters after fitting the object from the dictionary parameters.
* Displayed the best parameters using the data attribute best_params _ and the accuracy on the validation data using the data attribute best_score_.
* Calculated the accuracy on the test data using the method “score”.
* Same methodology is followed for Decision Tree Classifier and KNN to conclude which regression classifier works best for the given data. 


### Results

##### EDA with Visualization Results
* After plotting it seems the more massive the payload, the less likely the first stage will return.
* Also, it is observed that the different launch sites have different success rates. “CCAFS LC-40”, has a success rate of 60 %, while “KSC LC-39A” and “VAFB SLC 4E” has a success rate of 77%.
* From “Launch Site” and “Flight Number” scatter plot it is deduced that “CCAFS LC-40” have maximum number of flights, and “VAFB SLC 4E” launch site have least number of flights.
* Observed Payload Vs. Launch Site scatter point chart and found that for the VAFB-SLC launch site there are no  rockets  launched for  “heavypayload” mass(greater than 10000).
* Created a bar chart for the success rate of each orbit, launch sites “ES-L1”, “GEO”, “HEO” and “SSO” found to have maximum success rate, 100%.
*Plotted “FlightNumber” vs “Orbit” scatter plot and observed that in the LEO orbit the Success appears related to the number of flights; on the other hand, there seems to be no relationship between flight number when in GTO orbit.

#### EDA with SQL Results
* Displayed the names of the unique launch sites using “DISTINCT” SQL keyword. 
* Calculated Total Payload Mass (45596 kg) carried by boosters launched by NASA (CRS) using aggregate functions sum() and where.
* Total number of successful mission outcomes is 99 while only 1 mission was unsuccessful.
* Listed booster versions which has carried maximum number of Payload Mass, to name a few “F9 B5 B1048.4”,  “F9 B5 B1049.4”,  “F9 B5 B1051.3” were some boosters among the list of 12.
* Utilized Group by and Order By aggregate function to get landing outcomes between 2010 to 2017 and observed that only 31% were landed successfully.

#### Predictive Analysis (classification) Results
* Split the data into training and testing data and found that there are only 18 test samples.
* Displayed the best parameters and the accuracy on the validation data for logistic regression which comes nearly as 81.9%. Measured accuracy on the test data, which comes around 83.3%.
* Likewise found tuned hyperparameters and calculated accuracy on the validation data for Decision tree classifier and KNN. 
* For Decision tree classifier accuracy on validation comes around 88.5% and on test data comes around 77.7%.
* For KNN accuracy on validation comes around 66.4% and on test data comes around 61.1%.
* It can be concluded that Logistic Regression performs best for the given dataset with highest accuracy on train data.





