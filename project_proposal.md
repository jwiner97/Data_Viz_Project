# Project Proposal
Project Title: What factors affect opioid overdose deaths

Team Name: Git 'er Done

Team Members:
* Jason
* Chelsea
* Holly
* Robert

## Questions and Charts:
* Question: Does the rate of opioid prescriptions per 100,000 people in a county affect the opioid overdose death rate per 100,000 people?
    * Opioid overdose deaths per 100,000 people/county vs. opioid prescriptions per 100,000 people/county
* Question: Does the amount of money that doctors in an area receive from opioid companies in a county affect the opioid overdose death rate?
    * 
* Question: What are the education level rates in each county and does this affect opioid overdose deaths?
* Question: Do income levels in a county affect the opioid overdose death rate?
    * Per capita income/county vs. opioid overdoses/county and poverty rates
    
*--> Do we want to drop one of these questions in order to streamline what we're looking at? Maybe the income level question? I think it would be interesting to keep the question about education levels to see if lower education levels mean that patients are less likely to question their doctors and thus more likely to become addicted.*

* Idea: final chart could be changes over time in SD County

**Guidelines:**
https://ucsd.bootcampcontent.com/UCSD-Coding-Bootcamp/UCSDSAN2019DATA1/tree/master/01-Lesson-Plans/07-Project-1/1/ProjectGuidelines

## Process/To Do:
1. Pull data for analysis (which have APIs we can call?)
    * Opioid prescriptions by provider, zip code: https://data.cms.gov/Medicare-Part-D/Medicare-Part-D-Opioid-Prescriber-Summary-File-201/6wg9-kwip/data
    * State and county medicare spending: https://data.world/adamhelsinger/county-state-medicare-spend
    * Robert's zip code file (posted to Slack)
    * Opioid overdose deaths by county or zip code (did we find this yet?)
    * Per capita income by county
    * Poverty rates by county
    * Average education level by county
    * Holly's dataset showing how much $ docs receive from medical companies (INSERT LINK HERE)
2. Pull APIs (if needed)
    * Google Maps API
3. Clean data
    * Drop missing data, or find a way to represent it in our final charts
    * Drop unnecessary columns
4. Merge data by county
5. Determine and create appropriate charts
    * Save PNG files of all visualizations to distribute to class and instructional team as well as for presentation
6. Analyze data & charts to answer our questions
    * Create a write-up summarizing major findings. This should include a heading for each "question"  asked of the data, and under each heading, a short description of what you found and any relevant plots.
7. Create PPT presentation (sample presentation guidelines: https://ucsd.bootcampcontent.com/UCSD-Coding-Bootcamp/UCSDSAN2019DATA1/blob/master/01-Lesson-Plans/07-Project-1/1/ProjectGuidelines/PresentationGuidelines.md) 
    * 8-10 minutes
    * Describe core message/hypothesis
    * Describe questions we found interesting and what motivated us to answer them
    * Summarize where and how we found the data we used to answer these questions
    * Describe the data exploration and cleanup process (accompanied by Jupyter Notebook)
    * Describe the analysis process (accompanied by Jupyter Notebook)
    * Summarize  conclusions. This should include a numerical summary (i.e., what data did  analysis yield), as well as visualizations of that summary (plots of the final analysis data)
    * Discuss the implications of your findings. This is where you get to have an open-ended discussion about what your findings "mean".
    * Tell a good story! Storytelling through data analysis is no different than in literature. Find your narrative and use your analysis and visualization skills to highlight conflict and resolution in your data. (Discuss current news articles on this topic and how we are collectively still both coming to terms with this and are still not 100% sure how we got to this point; also helpful for coming up with solutions)
    * Propose policy solutions? May be out of our realm.
