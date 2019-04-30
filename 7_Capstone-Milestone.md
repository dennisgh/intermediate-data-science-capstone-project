# 7 - CAPSTONE PROJECT MILESTONE

**Assignment**
Overview  

The project milestone is an opportunity for you to practice your data story skills. You will reach the milestone when you have produced an early draft of the final Capstone Project 1 report.  

Learning Objectives  
Write a draft of your Capstone project milestone report with the following included:
Define the problem
Identify your client
Describe your data set, and how you cleaned/wrangled it
List other potential data sets you could use
Explain your initial findings
Share the Capstone Project 1 code and milestone report related to Github repository  

Prior Knowledge Recap  

You have proposed a project, collected a data set, wrangled and cleaned up the data, and explored it with descriptive + inferential statistics techniques.  

Key Terms & Concepts  
Client: name of the individual or business you are working with for your Capstone Project
Business problem:  What questions or issue you are looking to answer/solve through the proposed project

## 0. Related notebooks: code and graphs.

[Data Acquisition](https://github.com/dennisgh/intermediate-data-science-capstone-project/blob/master/PHASE_I/Data_Acquisition.ipynb)  
[Feature Generation pt.1](https://github.com/dennisgh/intermediate-data-science-capstone-project/blob/master/PHASE_I/Feature_Generation_pt1.ipynb)  
[Feature Generation pt.2](https://github.com/dennisgh/intermediate-data-science-capstone-project/blob/master/PHASE_I/Feature_Generation_pt2.ipynb)  
[Exploratory and Statistical Data Analysis](https://github.com/dennisgh/intermediate-data-science-capstone-project/blob/master/PHASE_I/EDA.ipynb)  
  
[434 Capstone Data Wrangling](https://github.com/dennisgh/intermediate-data-science-capstone-project/blob/master/434_Capstone_Project-Data_Wrangling.md)  
[641 Capstone Inferential Statistics Report](https://github.com/dennisgh/intermediate-data-science-capstone-project/blob/master/641_Inferential-Statistics.md)  

## 1. Define the problem

An investment bank wants to gain greater insight into the characteristics of C-level leadership of American corporations. They want to understand how education, age and tenure and more varies across industries and geographical regions. More specifically, they have asked the Data Scientist to:  

1. Identify the CEO and CFO for American public companies, past and present.
2. Identify the industry and region for these companies.
3. Identify characteristics from current and past C-level leadership such as, education, age, gender, career duration.
4. Use statistical analysis to explore the characteristics of the leadership in function of industry and region.

## 2. Identify your client

The client wants to gain insight into the profile of leadership at each industry and region. This way, they can judge the leadership of potential acquisitions in a larger context.

## 3. Describe your data set, and how you cleaned/wrangled it

The analysis is based on the SEC’s Quarterly Filings datasets. These datasets contain company information and quarterly financials for all American companies that file with the SEC.  

The names of CEO and CFOs came from the certification forms, also provided by the SEC. CEO and CFO sign the filings with their name and title.  

The features of CEO and CFO came from bloomberg.com, who offer biographies for many American executives. Features were extracted from these biographies.

The following techniques and `modules` were used:
1. Using `requests`, download the quarterly filing data files. Unzip with `zipfile` and write to disk with `os`.
2. Using `pandas`, merge the data files for processing and further processing.
2. Determine the URLs to the SEC certification forms for each filing.
3. Using REGEX, extract the name and title of the executives responsible for each quarterly filing.
4. Using Google, find the URL to Bloomberg’s executive biography. Open the pages with `requests` and interpret them with `BeautifulSoup`.
5. Using `selenium` (Firefox browser interface), open these urls and extract the biography.
6. Using rule-based logic, extract features from the biography.
7. Using `matplotlib.pyplot`, `pandas.pivot_tables`, and `sklearn.tree.DecisionTreeClassifier`, explore the executive features.

For more info, see [434 - Capstone Project Data Wrangling](https://github.com/dennisgh/intermediate-data-science-capstone-project/blob/master/434_Capstone_Project-Data_Wrangling.md)

## 4. List other potential data sets you could use

Wikidata.org offers API-based access and could also have been used to determine executives and their features, but preliminary tests showed only few executives showed up on this website.

The analysis can be expanded further by incorporating quarterly financial data (already available in the SEC data sets) in the analyses. This is beyond the scope of this 3-month project, but would make a great follow-up analysis.

## 5. Explain your initial findings

### 5.1 Subject Matter

Let's take a look at hospital CEOs:

![Hospital CEOs on Google](http://www.velorepar.ca/7_Capstone-Milestone_img1.jpg)

It looks like your average hospital CEO is quite established in their career.  
Now, let's take a look at CEOs in Manufacturing:

![Manufacturing CEOs on Google](http://www.velorepar.ca/7_Capstone-Milestone_img2.jpg)

Though not exactly college-aged, I count 5 relatively young CEOs. In fact, it would not be hard to group CEO's in *young* and *old*.
We also see that, out of the 16 CEO's pictured, 2-3 appear to be "featured" or are receiving an award.
And finally, none are women.

**How many of these first impressions are supported by data?**

* The average age of CEOs is just over 60 across most industries, **except in *Health, Legal and Professional Services*, where it is just over 70**. CEO’s in *Agriculture, Forestry and Fishing* are just over 50.
* Career length generally follows average age with notable exceptions. CEOs in *Mining, Oil and Heavy Construction*, and *Transport, Communications and Utilities* have been in their career for 30 years, whereas those in *Agriculture, Forestry and Fishing*, **and *Manufacturing*, and *Consumer Services and IT* have been in theirs around 25 years. In *Health, Legal and Professional Services*, the average CEO has been in their career for nearly 40 years.**

**Interesting. What about the awards?**

* One-third of CEO’s in *Health, Legal and Professional Services* hold a academic or industry award, compared to **the global average of 15-20%**. Less than 3% of CEOs in *Agriculture, Forestry and Fishing* or *Mining, Oil and Heavy Construction* do.

**And gender?**

* Around 10% of American CEOs are female. On the West Coast however, this shoots up to one-third.

**What else do you know about CEOs?**

* Interesting observations about *age distribution*, about *who holds degrees and who doesn't*, and where *those degrees came from*. What industry do you think holds the most *doctor*ates?
* The industry with the highest share of CEO's *without* a degree also has one of the highest rates of *degrees from Top-25 Universities*. And no, it's not IT!
* And what about that grouping of young and old CEOs? Any truth to that? Take a look at [the Exploratory and Statistical Data Analysis report](https://github.com/dennisgh/intermediate-data-science-capstone-project/blob/master/PHASE_I/EDA.ipynb) to see what the *machine learn*ed about that.

Related: [641 Capstone Inferential Statistics Report](https://github.com/dennisgh/intermediate-data-science-capstone-project/blob/master/641_Inferential-Statistics.md)

### 5.2 Technical and Meta
* It is easy to underestimate the work needed for such a project. Important to “under-promise and over-deliver” for Data Science projects.
* Beauty in code matters. Time invested in reviewing, commenting, re-factoring and carefully choosing descriptive variable, function and instance names pays dividends when re-visiting a notebook a week or a month later.
* Study your libraries. This means the difference between 10 to 15 lines of `for`-loops, lists, slow performance and bugs vs. a single function call.