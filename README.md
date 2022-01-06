# Predicting aid given to ERA applicants

Check out the [jupyter notebook](https://github.com/jcummingsutk/fulton_county_ERA_applications/blob/master/notebook.ipynb) to see the code for the project described below.

Some useful links:

* [program details](https://www.fultoncountyga.gov/covid-19/rental-assistance)

* [additional program info](https://sharefulton.fultoncountyga.gov/stories/s/Emergency-Rental/22ag-mzc6)

* [dataset](https://sharefulton.fultoncountyga.gov/Health-Human-Services/Neighborly-ERA-Applications/std8-6vc9)


The Emergency Rent and Utility Assistance (ERA) program is a program throughout the united states that assists families that are in need of emergency assistance for rent and utilities resulting from the COVID-19 pandemic. Residents have to meet eligibility requirements by the federal government, including

* One or more individuals within the household has qualified for unemployment benefits or experienced a reduction in household income, incurred significant costs, or experienced other financial hardship due, directly or indirectly, to the COVID-19 outbreak;
* One or more individuals within the household can demonstrate a risk of experiencing homelessness or housing instability; and
* The household’s income is at or below 80% of the area median income.

Also, an initial exploration of the data shows that when the payment program pays out, it takes on average 100 days for the person to get the money. This is a long time to wait for someone who is struggling due to the pandemic!

With the above details in mind, this project aims to answer the question will I receive assistance from the ERA program?

Below is a summary of the 77% and 78% accurate logistic regression and gradient boosting classifiers that is built for the ERA program applicants.

# Summary

I began this project with promise. On exploring the data, however, there appeared to be a number of oddities that reduced the chances of a reasonable classifier. Firstly, the documentation is very poor. There are columns which are unclear. For example, there is a column for funding total amount, total assistance approved, and ams amount (which is the amount of the check given) and they all can differ from one another. Additionally, the data analysis and the logistic regression predictor indicate those with a lower housing ami ratio (ratio of their rent to average locally) have a higher chance of receiving aid, somewhat counter intuitively. People with less money likely need more aid. My hypothesis that could explain this is that there are other data that are not included that are influencing the decision. For example, there is no data indicating a recent job loss. If one lost their job and had higher rent requirements, then perhaps they would likely be approved for aid. However, if someone still kept their job and had low rent requirements, perhaps this program is not applicable to them.

There are some insights that align nicely with reality. In the data analysis and in the logistic regression predictor, higher household size indicates a larger chance of receiving aid. Also, the program specifically mentions that this aid is for non-Atlanta residents in the Fulton county area (much of Fulton county contains atlanta), and the data and the logistic regression predictor both reflect this fact.

Also optimistically we find that the logistic regression coefficients are large in magnitude for much of the location data. On visualizing this with a heatmap, we find that the areas with the higher coefficients correspond to parts of the poorer regions of the area.

All of this being said, the classifiers, logistic regression and gradient boosting trees, are 77% and 78% accurate respectively. However, I believe one should be careful in using classifiers that have oddities that contradict intuition, and these certainly leave something to be desired there.

I had planned on making these classifiers available publicly through a flask application, as I think it would be extremely helpful to an applicant to have some prediction on whether they will receive aid. But unless some further observation is made on the oddities of the data, I hesitate to do so.

# Figures from this project

Here is a picture of Fulton County, for reference
![Fulton County](https://github.com/jcummingsutk/fulton_county_ERA_applications/blob/master/img/fulton.png)

Below you find a heatmap of the lat/long locations with the higher logistic regression coefficients in red, indicating a higher likelihood of aid received In the next cell a map of the greater atlanta area's richer and poorer neighborhoods. Firstly, our heatmap outlines the fulton county area, as expected. More importantly, we see from our heatmap that the poorer areas are more likely to receive aid, as they have the higher coefficients indicated by the more intense red coloring, and that one is less likely to receive aid if they are an applicant from the altlanta area, as the city of atlanta has its own ERA program, indicated by the light green shade.

![Heatmap of Logistic Regression Coefficients](https://github.com/jcummingsutk/fulton_county_ERA_applications/blob/master/img/heatmap.png)

Image showing righer and poorer neighborhoods, with poorer in blue and richer in red. Notice how the general blue areas in Fulton county line up with

![Heatmap of Logistic Regression Coefficients](https://github.com/jcummingsutk/fulton_county_ERA_applications/blob/master/img/img/high_low_income_area.jpg)
