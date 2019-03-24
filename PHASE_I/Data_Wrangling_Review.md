# Markdown
## Title

Note: While working with the data, it became evident how efficiently pandas
stores data. During a first attempt, I stored all quarterly datafiles (120)
as seperate dataframes in a dictionary. This took ages to process, required
massive amounts of RAM during processing, and took 8.2GB when pickled to disk.  

During a later version, I merged all dataframes to a dictionary
of 3 master dataframes. This file takes only 238MB on disk (!!).
RAM use of the python kernel during processing never exceeded 1GB.
