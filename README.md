Reilly Dunn, Mateo Escobar, Owen Hoover, Minh Nguyen
Professor Maike Sonnewald
ECS 171
March 14, 2024
Wildfires: Predicting the Cost
Github Link: https://github.com/ReillyDunn-UCDavis/ECS-171-Wildfire-Project
Demo Video Link: https://drive.google.com/file/d/1uX1qRkTAR2GRR7SsL_c1m3eFLZ3clsvc/view?usp=sharing  
Outline
	Our project is about wildfires and predicting how much damage they’re going to cause. The official definition of a wildfire is “an unplanned, unwanted fire burning in a natural area.” If left unchecked, a wildfire can quickly grow out of control and become a serious threat to the local area. Unlike many other natural disasters, the vast majority are caused by humans, making them very unpredictable. This means that emergency responders need to be constantly ready for a fire breaking out. The goal of our project is to analyze a wildfire and the damage it’ll do.
Wildfires are chaotic and multifaceted natural disasters, and there are many predictions a firefighting agency wants to make. For example, they may want to predict how big the fire’ll get to determine if evacuations are necessary, or they may want to know what the financial impact of a wildfire will be. To that end, we have decided to build multiple models, each focusing on a different aspect of the problem.
Total area of the fire, in acres
This is recorded in two ways: The number of acres, and the “Size Class” of the fire.
Class A is < 0.25 acres, Class B is 0.26-9.99 acres, Class C is 100-299 acres, and so on until Class G which is >5000 acres.
Predicting the number of acres is a Regression problem, while predicting the Size Class is, shockingly, a Classification problem.
How long it took to contain the fire, in hours
This is a Regression problem.
What caused the fire
The cause of a wildfire is typically recorded as “Human” or “Natural”
This is a Classification problem.
The ‘Dollar Damage’ of the fire
Dollar Damage, as defined by the California Department of Forestry and Fire Protection, “Estimates of the total property and contents dollar loss in terms of replacement in like kind and quantity. This estimation of the dollar loss includes property and contents damaged by fire, smoke, water, and overhaul. This does not include suppression costs or indirect loss, such as business interruption”
While this may initially seem like a Regression problem, after some data exploration we determined that it would be more effective to group fires into classes based on the Dollar Damage and create a Classification model.
We are using data from a few different sources. The main source of data is a compilation of data about wildfires that occurred in the continental U.S., with information about when and where the fire occurred. This dataset includes fires from 1992 to 2020 and has approximately 2.3 million data points.
However, this data was lacking in two key areas: It had no environmental data and no Dollar Damage information. To amend this, we appended environmental data from the National Oceanic and Atmospheric Administration, to include the average temperature and precipitation in the month and the state that each fire occurred in. Secondly, the data was lacking in Dollar Damage information. For this, we used data from the California Department of Forestry and Fire Protection’s “Redbooks” about the historical costs of wildfires in California counties. Similarly, this data was appended with data from the NCEI to include the average temperature and precipitation, this time by individual counties.


Introduction
	
Wildfires are one of the worst kinds of natural disasters there is. They’re incredibly destructive and difficult to predict. Fires are also becoming more frequent due to climate change, and wildfires in turn contribute to climate change by releasing vast amounts of carbon dioxide. As Californians, this issue is of particular concern to us because our state experiences thousands of wildfires each year. In 2022, California experienced a total of 7,884 wildfires affecting 309,287 acres of land according to the National Interagency Coordination Center.
Wildfires have severe repercussions that go well beyond their immediate aftermath. Fighting fires, reestablishing communities, and repairing ecosystems all come at a hefty financial cost. Furthermore, the long-term consequences on an area's ecosystem and businesses, like tourism and agriculture, can last for decades, changing the local economy and landscape. These complex effects highlight how urgently new strategies for managing, predicting, and reducing the effects of wildfires are needed.
Our project aims to address this need by leveraging the key concepts we have learned throughout the quarter in machine learning to predict various factors related to wildfires. We aim to provide useful insights that can guide resource allocation and decision-making for wildfire prevention and response efforts by creating a suite of predictive models. Our team is focused on several key areas:
Fire Size and Classification: Owen is developing models to predict fire size and labeling those fires as a certain class size. Initial attempts have shown that while basic neural network models can achieve high accuracy by predicting the most common class, there's a significant room for improvement in understanding the nuanced dynamics of fire sizes. These insights are crucial for effective fire management and resource deployment.
Duration of Fires: Mateo's work involves using regression models to estimate the time of how long wildfires actually burn. These predictions are useful for emergency services and for planning evacuation and containment strategies.
Causes of Fires: Minh is tackling the prediction of wildfire cause and classification through a binary classifier and a neural network, respectively. Identifying the causes of wildfires is key to preventing future occurrences, whether they are human-induced or natural.
Financial Cost: Given the limited data on financial costs in our main dataset, Reilly is exploring additional sources, such as CAL FIRE's statistics, to build a model that estimates the economic impacts of wildfires. This effort is particularly challenging but essential for understanding and mitigating the broader economic ramifications of wildfires.
Our project seeks to provide useful tools for emergency services, policymakers, and environmental agencies in addition to advancing the academic understanding of wildfires through the division of the problem into these discrete areas and application of machine learning models. We hope to provide insightful information through this project that could completely change the way wildfires are anticipated, controlled, and mitigated. As we work together to close the gap between theoretical models and practical application, we are tackling one of the most important environmental challenges of our time with a forward-thinking approach. In the end, we see our project as a critical first step toward a more knowledgeable, adaptable, and proactive approach to managing the risks and effects of wildfires, protecting ecosystems and communities alike.
Literature Review
The United States Federal Emergency Management Agency (FEMA) defines a wildfire as “an unplanned, unwanted fire burning in a natural area.” These are mostly caused by humans, unintentionally, or intentionally, but can also have natural causes. Wildfires can have drastic impacts on both the environments they take place in and on surrounding human populations. Wildfires have been increasing in severity and becoming more costly to fight (EPA, 2022).
Wildfires can have an impact on air quality, water quality, and biodiversity (Gill et al. 2013). Many plants and animals can be killed during these fires, which can lead to extinctions of some species. Additionally, the effects on water quality can damage aquatic habitats and hurt the animals living in them. As a result, wildfires are often catastrophic for the plants and animals in the ecosystem around them, and can cause lasting damage to them. Wildfires can also affect the climate of the world as a whole by releasing large amounts of carbon dioxide, which can contribute to climate change (EPA, 2022).
	Human effects can come in the form of both health and property. The effects on air and water quality can have a negative effect on human populations. The detrimental effects towards climate change also threaten to lead to more issues for human health. In addition, wildfires can be very dangerous and costly for those living near wildland areas, in what is known as the wildland urban interface (WUI). The WUI is the area where wildland and human developed land meets and mixes (U.S. Fire Administration, 2022). These areas are at high risk of wildfire because of their proximity to the areas in which these fires can spread. Those living in the WUI face more direct danger to life and property loss in the case of wildfire. In other estimations of wildfire suppression costs, researchers have also considered geography, amount of private land, amount of housing, fuel characteristics, administrative designation, and decision making influences. (Mattioli et al. 2022)
	There are many areas to consider regarding the cost of fighting a wildfire. The monetary cost of the resources and firefighting units needed to contain and put out a wildfire is the area we are focusing on for our model. This cost can be seen as a result of fire size and severity, but can also be a result of firefighting strategy. In the WUI, more resources can be necessary to protect structures, which can lead to an increase in cost (Gorte 2013). 
In addition to the cost of firefighting units, there is monetary impact in property loss, effect on businesses, and relief efforts. People can lose their homes and businesses if a wildfire reaches populated areas. Wildfires can have long term economic effects on businesses such as the timber market (Butry et al.) As more people are affected, the cost of wildfire relief efforts goes up in order to help them recover. As a whole, an increase in wildfire severity and frequency leads to more firefighting units needed and more people affected, increasing cost in all areas.
	One important area to look at is the split between costs in wildfire prevention and wildfire response. As emergency firefighting costs rise, they cut into the money that can be spent on prevention measures (Gorte 2013). This can lead to an underfunding for wildfire prevention, which in turn leads to more wildfires. As a result, it is important to make sure that wildfire prevention measures are still taken into account when looking at the cost of reducing wildfires.
Overall, wildfires are a major issue that affects both people and the environment. While we will be looking at the cost of firefighting resources, there are many other costs of wildfires, such as in prevention, loss of property, injury, and more. When developing our models, the most important areas to consider will be fire size, fire severity, and geography, but many other variables will be important to include because of their influence on fire fighting. 
Dataset Description (1/2 page)
https://www.kaggle.com/datasets/behroozsohrabi/us-wildfire-records-6th-edition  

The "US Wildfire Records (6th Edition)" dataset is an extensive compilation of wildfire incidents across the United States, detailedly recorded offering insights into wildfire occurrences, characteristics, and impacts. It offers a historical record of wildfires from as early as the 1980s up to the present, allowing for long-term trend analysis and the study of wildfire behavior in the context of changing environmental conditions.

This dataset aggregates information from multiple authoritative sources, including the National Interagency Fire Center (NIFC), the United States Forest Service (USFS), and various state and local fire agencies. Data collection involves both on-the-ground reporting by firefighting personnel and the use of advanced technologies such as satellite imagery and remote sensing, helping to facilitate wildfire monitoring, research, and response coordination.

Due to the sheer size of the dataset, with 2.3 million data points, only the first 10,000 rows were considered to build the models. The dataset also includes 37 attributes, and while most of which were not helpful in the construction of our models, some are essential. These key attributes were fire size, fire year, duration, date of discovery, location in terms of latitude and longitude, average monthly precipitation, and average monthly temperature.

From the 10,000 data points selected, most are clean and well-organized. However, there were some missing data or discrepancies, particularly in historical records or less-documented regions, which requires careful data cleaning and validation steps.

Researchers have utilized this dataset for various projects, including the development of machine learning models to predict wildfire risk, analyses of the impact of climate change on wildfire frequency and severity, and studies on the effectiveness of different wildfire management and prevention strategies. These projects not only advance our understanding but also inform policy and practice in wildfire-prone areas.

This dataset was used for the size, cause, and duration models. Unfortunately, the dataset was missing information about Dollar Damage, a topic central to our project. So for the Dollar Damage model, we used information from the California Department of Forestry and Fire Protection’s “Redbooks” about the historical costs of wildfires in California counties. Similarly, this data was appended with data from the NCEI to include the average temperature and precipitation, this time by individual counties.
Proposed solution and experimental results (4-5 pages)
Linear Regression to Predict Fire Duration
Predicting the duration of fires is a critical challenge in natural disaster management and response planning. Leveraging a dataset of the first 10,000 fire incidents, this report outlines an analysis to develop a predictive model. The model aims to estimate fire durations based on three key variables: precipitation in the month, average temperature in the month, and the geographical state of the fire occurrence.
This analysis focused on four primary variables from our entire dataset: DURATION_HOURS, Precipitation_In_Month, Avg_Temp_In_Month, and STATE. Initial data exploration revealed outliers in fire duration, which were subsequently removed to enhance model accuracy. Outliers were identified beyond 22.25 hours of fire duration, a threshold established through statistical analysis. Moreover, to address the categorical nature of the STATE variable, one-hot encoding was applied, transforming it into a series of binary columns, thereby making the dataset amenable to regression analysis.
A Linear Regression model was employed to predict the duration of fires. The model was trained on a dataset split 80/20 into training and testing subsets, ensuring a robust evaluation of its predictive capabilities. The feature set included the numerical variables of precipitation and average temperature, alongside the encoded state data, providing a comprehensive view of the factors influencing fire duration.
The model's performance was assessed with the following metrics: 
Mean Squared Error (MSE): 29.191694266434713
Root Mean Squared Error (RMSE): 5.402933857307039
Mean Absolute Error (MAE): 3.9591167489271912
R-squared (R²) Score: 0.0965259933017889
Afterward, a function was created where a user can input a month’s average precipitation fall, temperature, and state location, to predict how long a fire may last given those three conditions.
Although the model ended up with a relatively low mean squared error given such a large dataset, it is important to point out a low accuracy of 9%. This can be attributed to many things such as working with very little numerical values and having a lot of fires being data-heavy in certain areas. For example, the majority of the fires seemed to be recorded in Arizona and California, so it may be easier to predict the fire duration in those states than other states with fewer fires. 
Further refinement of the predictive model could include the integration of additional variables, such as wind speed, humidity, and topography, which may offer deeper insights into fire behavior. In conclusion, this report demonstrates the feasibility and utility of using machine learning to predict fire duration, offering a foundational tool for enhancing preparedness and response strategies in the face of wildfires.
For fire size predictions, we tried both a classification model and a regression model. Both of these models used our main dataset, with input features of fire year, discovery date, latitude, longitude, duration, precipitation in month, and average temperature in month. These were chosen out of the dataset because they seemed to capture the most important factors towards a fire, such as location, time of year, and weather conditions.
We initially built the classification model, which takes the inputs and predicts the class of fire size. These classes are based on acres, with labels from A to G. We then trained a Multi-Level Perceptron Model and used grid search to optimize the hyper-parameters. These are:
3 hidden layers with sizes 25, 15, and 10
A learning rate of 0.4
300 maximum iterations
This resulted in a model with an accuracy of about 0.6289 and mean squared error of about 0.0995. I would have liked to see a higher accuracy, especially since looking at the confusion matrices for each class shows that the model only ever predicted classes A and B. This is likely an issue resulting from the dataset itself, as an overwhelming number of the fires in the dataset are from the smaller classes. This makes sense, since most fires will be relatively small, but unfortunately this leads to the model failing to capture the larger picture of size prediction.
	The next model for fire size prediction was instead a regression model that predicts fire size in acres. We used the same input parameters for this model, and used grid search to optimize the hyperparameters of our Multi-Level Perceptron Model. These are:
5 hidden layers with sizes, 10, 25, 15, 10, and 5
A learning rate of 0.4
300 maximum iterations
This gave a model with a mean squared error of about 2.4431e-6. This seems to indicate a better model than the regression model, although it could still be more accurate for better predictions. I think that this model likely suffered from similar constraints of the dataset to the classifier. Because much of the data is for smaller fires, this likely contributed to inaccuracies with predicting larger values.
Overall, the fire size models could likely be improved by getting more data on larger fires. This would provide more information for the models to use for predicting these fires. This would be especially important from a usefulness standpoint because these larger fires are likely to be the most dangerous and costly. Being able to know when these types of fires would happen is much more important than the numerous smaller fires. 
We also built models to predict the cause of the wild fire. Firstly, the cause of the fire can be categorized into 2 classes: human or natural causes.  The model that was constructed for this binary classification is, therefore a logistic regression model, taking in FIRE_SIZE, FIRE_YEAR, LONGITUDE, LATITUDE, Avg_Temp_In_Month, and Precipitation_In_Month as inputs  to predict the cause. In order to train the model, the data has to be remapped to take on binary values. WIth max iterations = 100, the trained model achieved the accuracy of 0.7307 and MSE of 0.2696, demonstrating decent capabilities to predict the causes as a binary classification. More performance metrics can be found here, with class 0 being natural causes and class 1 being human causes:

Beyond the binary classification as “human” and “natural”, however, there are more classifications of cause that give more context to how the fire occurred. For the second model, the same input attributes were used, but 13 total output classes of cause were considered. In order to effectively utilize the context clues provided in the form of inputs, an intricate model that is able to capture the complex relationships between each input is necessary. Hence why we opted for a Multi-Level Perceptron classification model, where the hidden layers allow for proper weighting of the inputs. Through 10 epochs, each with 100 iterations of grid search to optimize the parameters, the final model includes:
ReLu activation functions.
2 hidden layers with size 416.
Learning rate of 0.0055
	This resulted in a model that performs decently given the amount of output classes, with the accuracy score of 0.596. This accuracy, however, could be the result of the dataset being skewed towards “natural” cause, overlooking the performance of the model in distinguishing between “human” causes which consists of most of the output classes. So, to further improve the model, more data on wildfires caused by human activities are needed. 
	Lastly, we have the model to predict ‘Dollar Damage.’ Our main dataset doesn’t have information about this topic, so this model actually uses a second dataset. It comes from the California Department of Forestry and Fire Protection’s “Redbooks”, which contain statistics about wildfires each year from 2022 to 2008. Specifically, we used the data that listed the total dollar damage of fires in each class size, in each California county. Dividing that number by the total number of fires that occurred in each class size and county produced the average dollar damage per size class per county. That is the figure we want to predict. To convert this information in numbers, we replaced the size classes with the median acreage of that size class (ie ‘class A’ becomes 0.125 acres, ‘class B’ becomes 5.125 acres, and so on. Additionally, the county names were swapped out for their latitude and longitude. Finally, similar to the main dataset, ecological data was appended to give the model better predictors about the climate at the time of the fire.
	My first instinct was to build a polynomial regression model. Costs seemed to increase rapidly with the size of the fire so it seemed like a good fit. However, there wound up being too much variance in the model for it to be very useful. So instead we used a Neural Network classification model. To make it a classification problem, we grouped different dollar damage amounts into five classes, similar to how acres of a fire are split into classes. The class partitions were chosen such that each class composed approximately one fifth of the dataset. This was done to prevent any one class from being so common that the model just predicts it every time.
	The model itself is a Multi-Level Perceptron. After applying the Grid Search algorithm, the hyperparameters in use are:
Logistic activation functions
5 input nodes
14 nodes in hidden layer 1
9 nodes in hidden layer 2
5 output nodes
Learning rate of 0.2
The accuracy of the model changes each time it’s trained, but it ranges from 0.3 to 0.4. This isn’t ideal, but it’s significantly better than guessing, which would be an accuracy of 0.2. 
The model’s inputs included fire size, latitude and longitude, temperature, and precipitation. Based on the weights between the input layer and the first hidden layer, the most important predictor was precipitation, followed by temperature, longitude, latitude, and size, in that order. The key insight here is that the more precipitation existed at the time of the fire, the less expensive it was likely to be. In other words, if a new wildfire just started, you should be more worried if there hasn’t been a lot of rain recently.

Conclusion and discussion (1/2 page)
In conclusion, our models were able to make predictions regarding the size of a fire, how long it’ll take to get the fire under control, what caused the fire, and the financial impact the fire is going to have. Being able to predict this information would help firefighting agencies to make informed decisions. Additionally, one of the main insights we found by developing these models is the importance of environmental data. Precipitation and temperature in the month and location of a fire were consistently among the most important input variables to the model, indicating that fires pose a greater risk during hot and dry spells.
The importance of environmental data highlights an issue with firefighting practices: lackluster data collection. The main dataset, as well as many other datasets we considered when working on this project, left a lot to be desired. Information about the environment at the time of the fire was always missing. These datasets were mostly intended to serve as historical records of fires. We appended environmental data from a secondary source based on the time and location of the fire, and that data was still an important predictor. It is for this reason that we recommend firefighting agencies to invest more in data collection practices. Our recommendations for some new forms of data that should be collected include precipitation/humidity, temperature, wind, foliage in the area, and proximity to population centers. Collecting this data, as well as making it publicly available, will enable data scientists to create better models about wildfires, which will in turn help firefighting agencies understand individual wildfires and make informed decisions.

References
Climate Change Indicators: Wildfires | US EPA. (n.d.). US EPA. https://www.epa.gov/climate-indicators/climate-change-indicators-wildfires 

Wildland Fire Summary and Statistics Annual Report 2022. (2022). National Interagency Coordination Center.  https://www.nifc.gov/sites/default/files/NICC/2-Predictive%20Services/Intelligence/Annual%20Reports/2022/annual_report.2.pdf 

Gill, A.M., Stephens, S.L., & Cary, G.J. (2013). The worldwide “wildfire” problem. Ecological
Applications, 23(2), 438-454. https://doi.org/10.1890/10-2213.1. 

Gorte, R. (2013, June). The Rising Cost of Wildfire Protection. Headwaters Economics.
https://www.baileyhealthyforests.org/wp-content/uploads/2013/12/fire-costs-background-report.pdf. 

Mattioli, W., Ferrara, C., Lombardo, E. Barbati, A., Salvati, L., & Tomao, A. (2022, March).
Estimating wildfire suppression costs: a systematic review. International Forestry Review, 21(1), 15-29. https://doi.org/10.1505/146554822835224801. 

United States Environmental Protection Agency. (2024, February 2). Climate Change Indicators:
Wildfires. https://www.epa.gov/climate-indicators/climate-change-indicators-wildfires 

United States Federal Emergency Management Agency. Wildfire | What.
https://community.fema.gov/ProtectiveActions/s/article/Wildfire-What 

United States Fire Administration. (2022, June 8). What is the WUI?
https://www.usfa.fema.gov/wui/what-is-the-wui.html 






Roadmap/Timeline
January 23: We met and decided to choose wildfires as our topic. Found the dataset on Kaggle
February 4th: Data processing: Appended precipitation and temperature data from NOAA datasets. Used the dataset’s start and end times to calculate the duration of the fire.
February 13th: Created a rudimentary neural network model to classify fire sizes
February 18th: Decided to construct multiple models: fire size, duration, cause, and dollar damage
February 25th: Made improvements to fire size classification model
February 29th: Created neural network model to predict dollar damage
March 3rd: Created regression model for fire size, created logistic regressor for cause
March 6th: Created linear regression model for duration
March 7th: Made improvements to dollar damage model
March 11th: Created neural network model to predict cause, made improvements to fire size models
