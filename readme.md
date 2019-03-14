# Group Project Write-Up
What’s Causing the Opioid Crisis?
By Team Git ‘er Done
Chelsea Monahan, Jason Winer, Holly Bergen, Robert Sayler
Presentation: https://docs.google.com/presentation/d/1WLSUhy88YHrzHDAVwsQzmrZIzP1JWgYabV4u_-cr2Ls/edit#slide=id.g528349431b_1_8

Our team looked at the opioid crisis in the United States, and attempted to determine if there were any variables that have an affect on predicting what is likely to cause opioid addiction. We approached this topic by having each team member find a potential variable of concern, and then do the relevant API pull or csv download followed by visualizations and analysis for their area of focus. We looked at the following questions:


- [Does the rate of opioid prescriptions in a county affect the opioid overdose death rate?](https://github.com/jwiner97/Data_Viz_Project/blob/master/Prescription%20Rate%20Analysis/Prescription%20Rate%20Analysis.ipynb)
- [Does the education level in a county affect the rate of opioid prescriptions?](https://github.com/jwiner97/Data_Viz_Project/blob/master/Education%20Analysis/education_level_analysis.ipynb)
- [Do poverty rates affect the rate of opioid overdose deaths?](https://github.com/jwiner97/Data_Viz_Project/blob/master/Income%20Demographics/IncomeDemographicsOpioids.ipynb)
- [Did unemployment rates during the Great Recession affect current overdose rates?](https://github.com/jwiner97/Data_Viz_Project/blob/master/Economic%20Downturn%20Analysis/Economic%20downturn%20and%20Opioid%20epidemic.ipynb)

We used a variety of sources in order to get all of the data we needed, including the Census API, the Bureau of Labor Statistics, the Kaiser Family Foundation in Partnership with the CDC, the Center for Disease Control Opioid Prescription Rate data, and the Google Maps API. Our results and analysis follow.



## Does the rate of opioid prescriptions in a county affect the opioid overdose death rate?

Opioids are responsible for a large portion of total overdose deaths in the US. In 2006 they accounted for 50% of all overdose deaths and rose to 67% by 2017


![](https://d2mxuefqeaa7sj.cloudfront.net/s_80488B502738A04D8EFAD289770E592A4C8D548E33C25E39F47ADDC9F608E713_1552163629946_image.png)
![](https://d2mxuefqeaa7sj.cloudfront.net/s_80488B502738A04D8EFAD289770E592A4C8D548E33C25E39F47ADDC9F608E713_1552170381283_image.png)


In looking at the total opioid prescribing rate in the US, we can see that in 2012 there was a peak in prescription rate, an increase of around 35 million from 2006. In the subsequent years following, that rate fell dramatically.


![](https://d2mxuefqeaa7sj.cloudfront.net/s_80488B502738A04D8EFAD289770E592A4C8D548E33C25E39F47ADDC9F608E713_1552519472474_image.png)


However, this did not mean a decline in opioid-related deaths. In fact, we can see that there was a sharp increase from 2012 to 2016, following the peak in prescription rate.


![](https://d2mxuefqeaa7sj.cloudfront.net/s_80488B502738A04D8EFAD289770E592A4C8D548E33C25E39F47ADDC9F608E713_1552163326257_image.png)


There are multiple possibilities here. One is that there is no correlation between prescription rate of opioids and opioid-related deaths. However, it is possible that being prescribed opioids becomes a gateway to addiction and once hooked, people are able to use underground markets to obtain the opioids they are no longer prescribed.

In fact, this may be visible in the data when looking at deaths by drug-type. While deaths by prescription opioids remain fairly steady, death by street opioids like heroin and fentanyl increase from 2012 to 2016.


![](https://d2mxuefqeaa7sj.cloudfront.net/s_80488B502738A04D8EFAD289770E592A4C8D548E33C25E39F47ADDC9F608E713_1552164164454_image.png)



“One study, published in the Journal of the American College of Surgeons in February 2018, noted that one in 16 surgical patients prescribed opioids becomes a long-term user” - https://www.clinicalkey.com/info/blog/opioid-prescribing-rates-drop-in-wake-of-cdc-guidelines/


Conclusions
- In looking at the total opioid prescribing rate in the US, we can see that in 2012 there was a peak in prescription rate, an increase of around 35 million from 2006. In the subsequent years following, that rate fell dramatically.
- However, this did not mean a decline in opioid-related deaths. In fact, we can see that there was a sharp increase from 2012 to 2016, following the peak in prescription rate.
- There are multiple possibilities here. One is that there is no correlation between prescription rate of opioids and opioid-related deaths. However, it is possible that being prescribed opioids becomes a gateway to addiction and once hooked, people are able to use underground markets to obtain the opioids they are no longer prescribed.
- 
- In fact, this may be visible in the data when looking at deaths by drug-type. While deaths by prescription opioids remain fairly steady, death by street opioids like heroin and fentanyl increase from 2012 to 2016.
Limitations
- Rate of actual addiction is also under-represented in the data, and difficult to track use of illicit opioids if they did not lead to death
- Not all opioid-related deaths are tracked, so data is likely well under-represented
- Looking at deaths alone does not account for opioid-related hospitalizations and overdoses


---------------------------------------------------------------------------------------------------------------------

## Do income demographics affect the rate of opioid overdose deaths?

We hypothesized that there were likely areas of the United States that were more adversely affected by the spike in opioid-related deaths. To determine if there was a correlation we extracted data by county from the American Community Survey 5-Year Data provided by the US Census, including categories such as Per Capita Income, Unemployment Rate, and Poverty Rate for the year 2017. 


![](https://d2mxuefqeaa7sj.cloudfront.net/s_DE5D95515E422550BB96E22D48ACE4A4DA360EBB246ECB92A54148F6B8AEA87D_1552337531076_image.png)


We then obtained the number of Opioid-related deaths for the year 2017 by county using the CDC Wonder application and merged the two dataframes by County FIPS Code:

![](https://d2mxuefqeaa7sj.cloudfront.net/s_DE5D95515E422550BB96E22D48ACE4A4DA360EBB246ECB92A54148F6B8AEA87D_1552337835029_image.png)


Once the DataFrames were combined we were able to drop any counties for which there was missing death data (note: the CDC data does NOT contain data for all US counties). With the DataFrame made we utilized a for loop to feed the county names for all rows in our DataFrame into the Google Maps API to gain a the discrete set of latitude and longitude coordinates for each county in our list. These lists are concatenated, zipped, and saved to CSV as the API takes approximately 5 mins to run.

With a set of lat and lon coordinates for each county we plotted a heat map with coordinates based on our aforementioned list and weighting (heat) based on the number of opioid deaths per 100K people. We chose per 100K instead of total deaths as total deaths tended to be more skewed towards larger more metropolitan cities. We also overlaid points to denote each county seat and info boxes once clicked on containing total opioid-related deaths in that county in 2017.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_DE5D95515E422550BB96E22D48ACE4A4DA360EBB246ECB92A54148F6B8AEA87D_1552338429678_image.png)


Particularly we found the area in the Rust Belt around Ohio, Kentucky, West Virginia, and Maryland of interest as these popped out as “hot spots”. Therefore we chose to investigate those areas to see if perhaps there was some kind of demographic reason for the high rate of opioid-related deaths in these counties.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_DE5D95515E422550BB96E22D48ACE4A4DA360EBB246ECB92A54148F6B8AEA87D_1552338482983_image.png)


To summarize our findings for the top 10 counties most affected by these deaths we created the following graphs:





![](https://d2mxuefqeaa7sj.cloudfront.net/s_DE5D95515E422550BB96E22D48ACE4A4DA360EBB246ECB92A54148F6B8AEA87D_1552338673529_image.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_DE5D95515E422550BB96E22D48ACE4A4DA360EBB246ECB92A54148F6B8AEA87D_1552338613110_image.png)



We prepared scatter plots for several different demographic measurements to ascertain whether or not these areas were particularly poor or faced with worse unemployment. Below are our results (Note, the red stars are the top 10 results from above), including San Diego.


![](https://d2mxuefqeaa7sj.cloudfront.net/s_DE5D95515E422550BB96E22D48ACE4A4DA360EBB246ECB92A54148F6B8AEA87D_1552338811180_image.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_DE5D95515E422550BB96E22D48ACE4A4DA360EBB246ECB92A54148F6B8AEA87D_1552338823740_image.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_DE5D95515E422550BB96E22D48ACE4A4DA360EBB246ECB92A54148F6B8AEA87D_1552338847670_image.png)



Conclusions
- West Virginia and other parts of the Rust Belt appear to be adversely affected relative to the rest of the country. 
- While these counties in the Rust Belt do tend to be poorer than the rest of the country, they appear to be outliers relative to the rest o the distribution which seems to have no relationship between opioid-related deaths and income demographics.
- Research from the West Virginia Department of Heath and Human Resources suggests that the high rate of death in these areas is possibly due to the number of factors. These include the high number of people on Medicaid, high number of jobs in the are which require physical labor or carry risk of physical harm that could necessitate a pain-killer prescription, and a lack of treatment options in the areas affected.
- San Diego, despite our homelessness problem, appears to do well relative to the rest of the country!


Limitations
- 2017 was only year analyzed (Snap shot)
- Measurement methodology of rates may vary from state to state.
- We looked at all opioid deaths including heroin, not specifically synthetic.
- CDC did not have death data for all US counties—some were missing.



## Does the education level in a county affect the rate of opioid prescriptions?

As discussed previously, 1 in 16 surgical patients who are prescribed opioids for pain management becomes a long-term user. Taking this into consideration, we decided to look at a possible correlation between weighted education levels in a county to the prescription rate in that same county, wondering whether those with a lower level of education are less likely to push back on a doctor’s prescription for the drug. Our hypothesis was that counties with a lower weighted education level would be more likely to have a higher prescription rate. 

Conclusions

Surprisingly, we found no relationship between weighted education levels and prescribing rates for counties in the US. It is possible that people who have lower levels of education are less likely to have insurance and therefore are less likely to be in a scenario where opioids could even be prescribed to them. It’s also possible that doctors in problem areas have cut back on prescribing opioids now that they are aware of how harmful they are, and that this correction could be happening unevenly based on a number of county or state-level policy or social factors

Limitations

We ran into two challenges while looking at the opioid crisis from this angle. 


1. We couldn’t simply pull the data we wanted for education levels as the Census API categories were much more specific than we needed and also were not necessarily in agreement with one another. We wanted education levels for all adults over 18 in seven bins: less than 9th grade education, didn’t graduate high school, high school graduate, some college, associate’s degree, bachelor’s degree, advanced or professional school degree. Instead, we had data as specific as “18-24 years old male with less than 9th grade education” and “25+ preschool education”. Although tedious, it was not difficult to process this data into useable categories.
2. The Census API does not automatically return a FIPS code for each county. Instead, it returns a state code and a county code within that state (i.e. every state had a county 001). It took us awhile to figure out that the FIPS code was a combination of the state code followed by the county code as the Census API documentation did not explain this. Once we figured this out, we were able to easily create a FIPS code column and merge the dataframe we had created from the Census API with the csv file from the Center for Disease Control showing prescribing rates per county in 2017.


![Snippet of code showing all variables pulled from Census API for Education Level by County](https://d2mxuefqeaa7sj.cloudfront.net/s_BA08E811A6879137D988B8CAB06A8188B53A0B0185AE9CFFCD39CB256FAB0BAE_1552347976978_Screen+Shot+2019-03-11+at+4.45.44+PM.png)

![Five lines of output from above code](https://d2mxuefqeaa7sj.cloudfront.net/s_BA08E811A6879137D988B8CAB06A8188B53A0B0185AE9CFFCD39CB256FAB0BAE_1552348227073_Screen+Shot+2019-03-11+at+4.50.03+PM.png)


Once we had cleaned up our merged dataframe, we had to create a weighting system in order to determine which counties were most educated and which were least. We decided on a simple system wherein the lowest category (less than 9th grade education) is worth 0, the next (didn’t graduate high school) is worth 1, and so on through graduate/professional degree being worth 6 points. These weights were multiplied by the percent of the population in the county with that education level, and then added together to create a weighted total for each county. This was the best way, we felt, to be able to compare levels of education between counties.

We were able to quickly create interactive coropleth maps of the United States by county using Plotly for both prescribing rates and education levels. We made the highest prescribing rates quartile and lowest education levels quartile both yellow so that we could do an immediate visual comparison between the two.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_BA08E811A6879137D988B8CAB06A8188B53A0B0185AE9CFFCD39CB256FAB0BAE_1552337212151_newplot.png)



![](https://d2mxuefqeaa7sj.cloudfront.net/s_BA08E811A6879137D988B8CAB06A8188B53A0B0185AE9CFFCD39CB256FAB0BAE_1552337242164_newplot+2.png)


To be absolutely sure, we also plotted the two variables against each other to see if the data points grouped along a regression line.


![](https://d2mxuefqeaa7sj.cloudfront.net/s_BA08E811A6879137D988B8CAB06A8188B53A0B0185AE9CFFCD39CB256FAB0BAE_1552337517704_prescriptions_v_ed_levels.png)


  


## Did unemployment rates during the Great Recession affect current overdose rates? 

Some of the cities hit hardest by the Great Recession never recovered. These cities saw over 20% decreases in employment and over 20% poverty rates. We decided to look at how those factors might impact the opioid crisis in these areas. Our hypothesis was that those areas would see worse opioid death rates than the rest of their state. To do this we analyzed the county unemployment levels from 2006-2017 and the opioid deaths in those counties over the same period. We then compared the data for the state and the county in 2017 to see if there was in fact a higher death rate in those counties. 
First we identified the cities that were hit the hardest during the Great Recession based on the current state of their economies. This information came a USA Today article that identifies cities that never recovered from the economic downturn. 

Then we took unemployment data from Bureau of Labor Statistics on the counties that were home to these cities to create a data frame and chart the trends over time. 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_644E905F51B0F8419318505F4314EB89F78C858FEEA3E55C09EC04960B4135BB_1552355141771_Screen+Shot+2019-03-11+at+6.12.38+PM.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_644E905F51B0F8419318505F4314EB89F78C858FEEA3E55C09EC04960B4135BB_1552355391322_Unemployment.png)


Then using the CDC’s website we pulled the deaths for these counties. We then created a data frame and line graph to chart this over time. 


![](https://d2mxuefqeaa7sj.cloudfront.net/s_644E905F51B0F8419318505F4314EB89F78C858FEEA3E55C09EC04960B4135BB_1552355216182_Screen+Shot+2019-03-11+at+6.13.40+PM.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_644E905F51B0F8419318505F4314EB89F78C858FEEA3E55C09EC04960B4135BB_1552355360141_County_Deaths_Over_Time.png)


The next step was to compare the state opioid death rates of states to these counties. The state data was pull from the Kaiser Family Foundation, which utilized CDC data to compile it’s information. From there the death rates per 100,000 were compared for the states and the counties. These were then charted on a bar graph to create a visualization of the data. 

![](https://d2mxuefqeaa7sj.cloudfront.net/s_644E905F51B0F8419318505F4314EB89F78C858FEEA3E55C09EC04960B4135BB_1552355256328_Screen+Shot+2019-03-11+at+6.13.14+PM.png)

![](https://d2mxuefqeaa7sj.cloudfront.net/s_644E905F51B0F8419318505F4314EB89F78C858FEEA3E55C09EC04960B4135BB_1552355273477_2017_DR_SvC.png)

Conclusions

Surprisingly, the counties we analyzed did not have higher death rates than the states they reside in, in most cases. Cook County, Illinois, Saginaw, Michigan and Wayne County, Michigan were the only counties to have a higher death rate than the rest of their state’s average. Some of the counties even have the death rate drop to 0 in 2017, which suggests that there is little correlation between the Great Recession the opioid epidemic. 

Limitations

Data was limited for each county. Some counties did not have significant employment data while others did not have sufficient opioid related death data. Another factor was the fact that the smallest area we could analyze was at the county level. This pulls in neighboring cities and towns that can distort the data on how these cities are actually fairing. 

Follow-Up Questions
- How have the poverty rate and overdose deaths varied over time for these most affected areas?
- Is there any relationship between medicaid dollars or benefits and deaths in these states?
- Is there any relationship between opioid type in these counties?
- How many treatment centers are available in each of these counties?

