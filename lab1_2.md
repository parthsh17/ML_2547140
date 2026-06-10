

**India Air Quality & Crop Yield — EDA Lab**  
**Data Preprocessing, Visualisation & Exploration**   
 **Combined Lab Sheet** 

June is globally recognised as [Environment Awareness Month](https://en.wikipedia.org/wiki/June_5), with World Environment Day celebrated on June 5 to encourage action to protect our planet and promote sustainable living.

In connection with this global initiative, this lab exercise focuses on exploring environmental and agricultural data through the lens of Machine Learning and Data Analytics.

**Aim**

To investigate whether worsening air quality across Indian states is linked to declining agricultural output  by independently choosing, applying, and justifying appropriate data analysis and visualisation techniques on raw, messy, real-world datasets.

**Objectives**

* Independently assess data quality and decide on appropriate treatment strategies  
* Select and justify suitable visualisation techniques for a given analytical problem  
* Detect anomalies, patterns, and relationships in environmental data  
* Derive and communicate meaningful inferences to both technical and non-technical audiences  
* Develop critical thinking around data limitations and confounding factors  
* Dataset provided

Two CSV files are provided: [dataset](https://drive.google.com/drive/folders/1gKlORDaoZ-zviCnN6KyRDEnLPanCEZnK?usp=drive_link)   
[city\_aqi.csv](https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india) contains city-level air quality readings (City, State, Date, AQI, PM2.5, PM10, NO2, CO) from 2015–2023. [crop\_yield.csv](https://www.kaggle.com/datasets/abhinand05/crop-production-in-india/data) contains state-level crop production records (State, Year, Crop, Season, Area, Production) for the same period.

 The files are raw and unverified. They may contain missing values, inconsistent entries, duplicate records, and extreme anomalies. It is your responsibility as an analyst to discover and address all issues before drawing any conclusions.  
 Each task below presents a real-world problem. You must decide what to do, how to do it, and why — then document your reasoning in a markdown cell alongside your code. There are no prescribed methods unless stated.

**Lab 1**  
                                                 **Data preprocessing and visualisation** 															10 marks  
**Task 1**

A junior analyst hands you two CSV files and says — "I have no idea what's in these. We need to use them to build a machine learning model next week." Before any analysis can begin, you need to understand what you are working with.

Investigate both files thoroughly. Produce a structured summary that gives a complete first-impression picture of the data — its size, its contents, and where it might be problematic. Decide what information a data scientist would need before trusting this data, and make sure your summary covers all of it.

A structured data profile for each file in a markdown cell  
At least one written observation about what concerns you after the inspection  
 *Think: What does a data scientist need to know about a dataset before using it? What functions help you find that?*			 2 marks Completeness of profile \+ written concern

**Task 2 The data has holes — and not all holes are equal**

After the inspection, it is clear that several columns have missing values. A colleague suggests simply deleting all rows with any null value. Another suggests filling everything with the mean. You are not sure either approach is right.  
Devise your own missing value treatment strategy. For each column with missing data, decide whether to drop it, drop affected rows, or impute — and explain why that choice is appropriate for that specific column. Apply your strategy and verify it worked.

A markdown cell that justifies each decision column by column  
Before and after null counts as evidence the treatment worked

 *Think: Does the volume of missing data matter? Does the column type matter? What does imputing with mean vs median assume about the data? 2 marks*   
**Task 3 The two files disagree on how to spell "Tamil Nadu"**

You need to combine both files later in the lab using the State column as the common key. But when you look closely, the same state appears with different spellings, extra spaces, or old names across the two files. There are also rows that appear more than once for no clear reason.  
Make both files agree on state names and remove any redundant records. Document every inconsistency you found and how you resolved it. Show that the files are now ready to be merged reliably.

A list of all inconsistencies found and the fix applied for each  
Record counts before and after to prove duplicates were removed  
 *Think: What could go wrong in a merge if state names don't match exactly? How would you systematically find all variants of a state name?*  2 marks 

**Task 4**  
**Where do most cities actually sit on the AQI scale?**

The pollution control board wants to know — are most Indian cities moderately polluted, or is the problem concentrated in just a few places? They also want to know whether the average AQI is a fair number to report publicly, or whether extreme cities are pulling it up unfairly.

Investigate the shape of the AQI distribution. Decide which visualisation(s) best answer both questions the board is asking, justify your choice, produce the plot(s), and record two specific observations that directly address their concerns.

Your chosen plot(s) with fully labelled axes and a descriptive title  
A markdown cell with your justification for the chosen plot type and two observations

 *Think: Which plot shows where values cluster? Which one reveals extreme values? Do you need one plot or two to answer both questions?*  2 marks

**Task 5**  
**Something is making the average AQI look worse than it is**

A data quality report flags that a few AQI readings in the dataset are implausibly high — values that no monitoring station should realistically record. If left in, these values will distort every statistic and model built on this data. The team lead asks you to "handle the extreme values properly" but does not tell you how.  
Identify whether extreme values exist, quantify them, decide on an appropriate treatment method, apply it, and demonstrate that the data is now cleaner. Justify every decision you make.

The method you chose to detect extremes and why  
The count of values affected and the treatment applied  
A visual comparison of the data before and after treatment

 *Think: Should extreme values always be deleted? What are the alternatives? How do you prove your treatment actually worked?*  2 marks

**Lab 2**  
**Data exploration and inferences**

10 marks  
**Task 6: Is India's air getting better or worse over time?**

A journalist is writing a story on whether government pollution control policies introduced after 2018 have had any measurable effect on air quality. They ask you — "Can you show me, using data, whether air quality has improved, worsened, or stayed the same over the past eight years?"

Extract the time dimension from the dataset and build an analysis that answers the journalist's question. Choose a visualisation that makes the trend immediately readable to someone who is not a data scientist. Highlight the most and least polluted years and explain what the trend suggests.

Your plot with the trend clearly visible and key years highlighted  
A markdown response to the journalist's question — one paragraph, plain language

 *Think: What needs to happen to the Date column before you can group by year? Which plot type communicates a trend over time most clearly?*  2 marks

**Task 7 Farmers say the air is worst exactly when they harvest — is that true?**

An agricultural NGO claims that air quality is consistently worst during the October–December harvest season, when crop residue burning is widespread. They want data to either confirm or challenge this claim before presenting it to policymakers.  
Investigate whether AQI follows a seasonal pattern across the year. Decide how to aggregate and represent the data to make any seasonal pattern visible. Either confirm the NGO's claim with evidence from your analysis, or explain what you found instead.

A visualisation that clearly shows how AQI varies across months or seasons  
A markdown cell that directly responds to the NGO's claim with data evidence

 *Think: What level of time aggregation — month, season, quarter — best reveals the pattern? How do you extract that from a date column?*  2 marks

**Task 8:  Can the two datasets talk to each other?**

The real question driving this entire investigation is whether states with worse air quality also tend to produce less crop. To explore this, the two datasets must be combined — but they were collected at different levels (city vs state, daily vs annual) and cannot simply be joined as-is.  
Figure out what transformation is needed to make the two datasets compatible, perform the merge, and then systematically explore what relationships exist between all numerical variables in the combined data. Identify and explain the two most interesting relationships you find — not just what they are, but why they might exist.

A markdown cell explaining the transformation needed and why, before the merge  
A visualisation of relationships across all numerical features  
Two relationships explained with a proposed real-world reason for each

 *Think: If one file has city-day rows and the other has state-year rows, what needs to happen before they can be joined? What does a correlation matrix actually tell you — and what doesn't it tell you?*  3 marks

**Task 9 : The minister needs to act — what do you tell her?**

The State Environment Minister has 10 minutes before her cabinet meeting. She has never opened a Jupyter notebook. Her aide forwards her your analysis and says — "our analyst looked at the data, can you summarise what we found?" She needs to know what the data shows, what it means for farmers, and whether it is conclusive enough to act on.

Write a clear, honest briefing addressed directly to the minister. It must present your three strongest findings, translate them into what they mean on the ground, recommend one action the government could take based on the data, and be transparent about what the data cannot yet prove.

150–200 words in a markdown cell, addressed to the minister. Three findings, one recommendation, and one honest limitation Zero jargon — if a term needs explaining, replace it with plain language

 *Think: Which of your findings actually matters to a farmer or a policymaker? What is the difference between correlation and proof? Would the minister act on what you found? 3 marks*

 **Optional — advanced task**  
**Build the case — or break it**

Attempt only after completing Tasks 1–9. The central hypothesis of this entire investigation is: states with higher pollution have lower crop yields. Your job here is to either build the strongest possible case for this hypothesis — or find evidence that challenges it.

**Task A: The two extremes — do they tell the same story?**

If the hypothesis is true, you would expect the most polluted states and the least polluted states to show a clear difference in crop output. But the data might surprise you.

Identify the states that represent the two extremes of pollution. Compare their agricultural output using a visualisation of your choice. Analyse what you see — does the pattern support the hypothesis, contradict it, or is it more complicated than that?

**Task B: Put a number on the relationship**

A research team wants to know not just whether a relationship exists between AQI and crop production, but how strong it is and in which direction. They will use your output to decide whether to fund a full causal study.  
Quantify the relationship between average state AQI and average crop production. Choose a method that both measures the strength and makes the pattern visible in a single output. Interpret your result for the research team — be honest about what it proves and what it does not.

 *Think: What does a correlation value of 0.2 vs 0.8 mean in practice? Does a strong correlation mean pollution is causing yield loss?*

**Task C: One plot to rule them all**

You have produced many visualisations across this lab. A data journalism outlet wants to publish just one chart from your work to accompany a story on India's air-agriculture crisis.

Choose the single visualisation from your entire lab that you believe most powerfully tells the story of this dataset. Write a 3–4 sentence caption for it — not a description of what the chart shows, but an explanation of why it matters and what it reveals that no other chart in your analysis does.

Caption reveals insight, not just description  
 Across all optional tasks, your writing must acknowledge that correlation is not causation and name at least one factor — rainfall, irrigation, soil type, economic conditions — that this dataset cannot account for but which could explain any relationship observed.  
Deliverables

Single Jupyter Notebook (.ipynb) — tasks numbered, code commented, every decision explained in a markdown cell  
Minimum 5 visualisations of your own choosing — axes labelled, titles present  
Markdown reasoning cells for every task — not optional, part of the marks

---

