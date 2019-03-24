# 4.3.4 - CAPSTONE PROJECT - DATA WRANGLING

**Assignment:** Create a short document (1-2 pages) in your github describing the data wrangling steps that you undertook to clean your capstone project data set. What kind of cleaning steps did you perform? How did you deal with missing values, if any? Were there outliers, and how did you decide to handle them? This document will eventually become part of your milestone report.


## Data Wrangling: Challenges and Techniques Used

### Data_Acquisition.ipynb

1. The required dataset was provided across multiple .zip files.

Used BeautifulSoup (‘BS4’) to identify the hyperlinks to the zip files.  
Used Requests.get to download the zip files. To save time (the files were 34MB), they were streamed with parameter stream=True.  
Used io.BytesIO to stream the data to the zipfile module.  
Wrote the archive contents to disk.  

2. The dataset was large and needed an efficient file structure.

Used a dict of pandas (‘pd’) dataframes (‘df’).

3. The datasets were spread across quarterly files.

Combined them using the pd.DataFrame.append() method.  
Distinguished them by creating a new column [‘Quarter’].

4. The dict of dfs needed to be persistent across notebooks.

Used pickle to store the dictionary to disk.

### Feature_Generation.ipynb

