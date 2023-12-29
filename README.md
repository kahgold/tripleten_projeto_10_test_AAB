# Project: Integrated Project 2

You work at a startup that sells food products. You need to analyze user behavior for your company application. It is an integrated project that combine all of previous subject, especially Business Analytics, A/B Testing, and Data Storytelling.

As a data analyst for a startup that sells food products, it's essential to understand user behavior for the company's app. In this project, we'll investigate the **sales funnel** and study **user behavior** using an **A/A/B test** to see how **changes to the app's font** will **impact user engagement**. We'll begin by analyzing the sales funnel to understand how users **reach the purchase stage**, how many users make it to this stage, and **which stages have the most drop-offs**. Then, we'll move on to the A/A/B test, where users are split into three groups: two control groups that receive the old fonts and one test group that receives the new fonts. We'll determine **which** set of fonts **produces better results** and confirm if the test groups were split correctly.

We'll be using a dataset that combines general data and A/A/B analysis data to conduct our study. This project will test our abilities in data cleaning, data visualization, hypothesis testing, and statistics. Let's dive in and see what insights we can uncover from this analysis.

To complete this project, we'll need to perform the following steps:
- **Open the data file and read the general information**.
- **Prepare the data for analysis** by renaming columns, checking for missing values and correcting data types. Add a date and time column and a separate column for dates.
- Study and check the data to determine:
    - the **number of events and users in the logs**,
    - the **average number of events per user**, and
    - the **period of time the data covers**.
    - Plot a **histogram** by date and time to determine whether you have equally complete data for the entire period. Find the moment at which the data starts to be complete and ignore the earlier section. Make sure you have users from all three experimental groups.
- Study the **event funnel** by determine:
    - the **frequency of occurrence for each event** in the logs,
    - the **number of users who performed each action**, and
    - the **proportion** of users who **performed** each action **at least once**.
    - Use the event funnel to **find the share of users that proceed from each stage** to the next. Identify the **stage at which you lose the most users** and **determine the share of users that make the entire journey** from their first event to payment.
- Study the results of the experiment by determining the **number of users in each group**, checking for a **statistically significant difference between samples** 246 and 247, and **comparing the results** of the group with altered fonts to those of the control groups. Calculate the **significance level** and determine the number of statistical hypothesis tests you carried out. If necessary, adjust the significance level and repeat the previous steps.

**Data dictionary**

**The logs_exp_us table:**
    
- `EventName` — event name
- `DeviceIDHash` — unique user identifier
- `EventTimestamp` — event time
- `ExpId` — experiment number: 246 and 247 are the control groups, 248 is the test group

**Conclusions**

- This **project's aim** is to **investigate the sales funnel** and study user behaviour using an **A/A/B test** to see how **changes to the app's font affect user engagement**.
- Some **data pre-processing** was performed, such as **renaming columns**, **replacing values** with more practical names, as well as **converting** some columns to the appropriate **data types**. There was some **duplicated data**, but it was **removed** e there was **no missing data**.
- Preliminary **data exploration** reveals that our dataframe **contains** some **unnecessary data** from before the testing time. Removing this data **removed only 1.16% of the events** that occurred and **0.23% of the users**. This figure is insignificant in comparison to the total data and will not skew the analysis results.
- **Event Funnel Analysis**:
    - **Users follow a similar route** of main screen appear -> offers screen appear -> cart screen appear -> payment screen successful.
    - The stage with the **greatest loss is between the first and second**, with nearly 39% of users (more than 2,826 unique id) failing to advance to the next level.
    - More than **47% of users undergo the entire journey** from main screen to succesfully make a payment.
- **A/A/B Testing**:
    - **Mann Whitney U test** is used in this project
    - The test outcome demonstrates how the **test group outperformed the control group** in terms of **visitors** (main screen appear) and **interested users** (offers screen appear). However, the font change should have no effect on this stage of the event funnel because it has no effect on convincing first-time users to use the app and continue to the offer page.
    - The test reveals that the **test group are fail** to have an increase that is enough **to pass the signicant threshold** in terms of ***Add-to-Cart users*** (cart screen appear) and ***Buyers*** (payment screen successful).
    - The conversion value of test group are also failing to shows any increment compared to one of the control group.
- **A/A/B testing proved that changing the font of the app does not have the expected positive impact on user engagement**.
