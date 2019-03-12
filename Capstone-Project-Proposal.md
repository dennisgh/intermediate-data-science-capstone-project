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

### PHASE I: Feature generation with text analysis and web scraping

1. Ingest SEC datasets, load data into Pandas. Reduce data, merge ca. 40 quarterly
data sets into a single file. Do this for: NUM file, SUB file.

2. Extract the full list of companies from the SEC dataset.

3. For each company:
	* Determine the CEO, CFO at various points in time. This can be extracted from the 10-K filings.

4. For each executive, identify:
	* Year_of_birth [int]
	* Gender [cat]
	* Hire Quarter (see 3.)
	* Year_of_career_start [int]
	* International education [Bool]
	* Ivy League education [Bool]
	* International career experience [Bool]
	* FirstTimeExecutive [Bool]

This will be accomplished as follows:
	* Query structured, API-accessible data sources: https://www.wikidata.org/wiki/Wikidata:Tools/For_programmers
	* Query structured, web-accessible data sources: LinkedIn
	* Query unstructured, web-accessible data sources: general web search, bloomberg biographies.

	* On the Bloomberg biographies, apply Natural Language Processing to determine features: https://www.nltk.org/book/ch06.html
	Heuristics used in the analysis, would include:
	
	* A list of foreign universities. (int'l education)
	* A list of foreign cities/countries. (int'l experience)
	* Regex for common expressions such as "joined company in", "graduated in",
	"started his/her career"
	* Deep learning techniques?

PHASE II - CLASSIFICATION OF PERFORMANCE GROWTH WRT. EXECUTIVE FEATURES.

Specifically,  

* The analysis will focus around 3 pairs:  
  CEO and Revenue/Sales.  
    CEO: responsible for Sales performance.  
  CFO and Net Income Margin LESS Operating Margin.  
    CFO: responsible for taxes paid, financing expenses and depreciation.  

* Two sets of target data will be considered:  
  Short-term: n=2 and x=5%, Long-term: n=5 and x=10%:  
  [(Fin_metric_n_yr_after_hire)/(Fin_metric_at_hire)]/
  [(Fin_metric_at_hire)/(Fin_metric_n_yr_before_hire)] > (1+x)

  Or in words: did the hire improve the growth rate of the  
  metric in question by at least x % over period of n years,  
  compared to the preceding period of n years?

  eg. in 2008, ACME Sales totalled $5MM. in 2010, they totalled $6MM (+20%).  
  In 2010 a new CEO joined. In 2012, sales totaled $7.4MM (+23.3%).  
  Our target metric yields False, as x = (1.233/1.2)-1 = 2.8% < 5%.  
  The hire of the CEO did not lead to an increase  
  of sales growth larger than 5%.

 * The short-term and long-term benchmark pairs are subject to change.  
   If EDA reveals a typical boost in performance of 15% after 3 years,  
   that could be the long-term pair.

 * Ultimately, 4 machine learning models will need to be fitted:  
   	X: CEO_chars  
	Y: Short_term_sign_grwth_Rev, Long_term_sign_grwth_Rev  

	X: CFO_chars  
	Y: Short_term_sign_grwth_FinMet, Long_term_sign_grwth_FinMet  


## 5. What are your deliverables?

1. Code on Github for each module.
2. Paper with contents as instructed.
3. Slide show with contents as instructed.

## 6. What issues do you foresee?

* The SEC data sets may push the limits of what can be processed on a personal computer. Mitigation: use of efficient data types, data pruning upon load.
* Web scraping may see low efficiency. Mitigation: Look for additional SEC data sets with corporate personnel.
* Natural Language Processing may see low success rate at Information Extraction. Mitigation: further research into Deep Learning techniques.
* Statistical analysis: correlations may be subtle and require analysis of a large number of features across time. Mitigation: further learning into statistical techniques.
