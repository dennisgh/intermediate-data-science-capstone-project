# Capstone Project Proposal

## 1. What is the problem you want to solve?

An investment bank wants to understand how the choice of C-level leadership
impact corporate performance across industries. They have asked their data
scientist to develop a model which will
(1) warehouse corporate performance for public companies and extract relevant performance metrics, and
(2) use Web Scraping and Natural Language Processing to identify characteristics
from current and past C-level leadership, such as tenure, international experience,
age, gender, career duration.
(3) use statistical analysis to identify strong correlations between C-level
characteristics and financial performance after hire.

## 2. What will your client DO or DECIDE based on your analysis that they wouldn’t have otherwise?

The investment bank will use the lessons learned to invest or divest following C-level personnel changes.
The investment bank believes that, due to the state-of-the-art nature of NLP,
they can glean new insights and gain an edge on the investment market.

## 3. What data are you going to use for this? How will you acquire this data?

1. Public financial data: SEC.gov tabular data of quarterly filings.
https://www.sec.gov/dera/data/financial-statement-data-sets.html
2. Public biographies of C-level personnel: bloomberg.com
e.g. https://www.bloomberg.com/research/stocks/people/person.asp?personId=50035778&privcapId=24937

## 4. In brief, outline your approach to solving this problem

1. Load corporate financials into Pandas. Reduce data, merge ca. 40 quarterly
data sets into a single file, perform EDA. Desired data table:
| Company | Quarter Ending | Fin Measure 1 | Measure 2 | CEO   | COO | CFO    |
|---------|----------------|---------------|-----------|-------|-----|--------|
| Apple   | 31-Mar-2013    | $10,000,000   | 32%       | Jim   | Jon | Jessie |
| Apple   | 31-Dec-2012    | $8,500,000    | 35%       | Julie | Jon | Jessie |

2. Develop a web scraping script to identify key corporate people, and download their public biographies.

3. Use Natural Language Processing to extract information from this biography.
https://www.nltk.org/book/ch06.html

4. Use statistical methods to identify statistically significant correlations between corporate performance and C-level personnel characteristics.

## 5. What are your deliverables?

1. Code on Github for each module.
2. Paper with contents as instructed.
3. Slide show with contents as instructed.

## 6. What issues do you foresee?

* The SEC data sets may push the limits of what can be processed on a personal computer. Mitigation: use of efficient data types, data pruning upon load.
* Web scraping may see low efficiency. Mitigation: Look for additional SEC data sets with corporate personnel.
* Natural Language Processing may see low success rate at Information Extraction. Mitigation: further research into Deep Learning techniques.
* Statistical analysis: correlations may be subtle and require analysis of a large number of features across time. Mitigation: further learning into statistical techniques.
