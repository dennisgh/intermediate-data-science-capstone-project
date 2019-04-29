# 4.3.4 - CAPSTONE PROJECT - DATA WRANGLING

**Assignment:** Create a short document (1-2 pages) in your github describing the data wrangling steps that you undertook to clean your capstone project data set. What kind of cleaning steps did you perform? How did you deal with missing values, if any? Were there outliers, and how did you decide to handle them? This document will eventually become part of your milestone report.


## Data Wrangling: Challenges and Techniques Used

### Data_Acquisition.ipynb

1. The required dataset was provided across multiple .zip files.

Used BeautifulSoup (‘BS4’) to identify the hyperlinks to the zip files.  
Used Requests.get to download the zip files, and extract them with the zipfile module
Wrote the archive contents to disk.  

2. The dataset was large and needed an efficient file structure.

Used a dict of pandas (‘pd’) dataframes (‘df’).

3. The datasets were spread across quarterly files.

Combined them using the pd.DataFrame.append() method.  
Distinguished them by creating a new column [‘Quarter’].

4. The dict of dfs needed to be persistent across notebooks.

Used pickle to store the dictionary to disk.

### Feature_Generation_pt1.ipynb

5. The web scraping scripts were unstable due to conditions beyond my control (lost connection, blocked by website).

Process the companies in “chunks” and write the results to disk. That way, not much work is lost if the script fails.

6. The officer name and title were contained in full text documents.

Used REGEX to extract officer name and title from the filing forms. These forms had certain form elements in common, which I used to anchor the REGEX. I also hardcoded the 4 or 5 most common exceptions, and accepted the others as a loss.

### Feature_Generation_pt2.ipynb

7. For each company in the list, certain conditions had to be met.

Use DataFrame.groupby() to perform operations such as count and shift for each company.

8. The biographies contained executive features in freeform text.

Use rule-based extraction based on words present in the biography.