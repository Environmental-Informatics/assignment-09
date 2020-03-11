# Environmental Informatics

## Assignment 08 - Time Series Analysis with Pandas

### Lab Objectives

On completion of this lab, students will be able to:

1. Use Time and Date functions with pandas DataFrames to conduct time series analysis of a dataset.
2. Import a data file into a Pandas DataFrame that uses Datetime as the index.
3. Use Pandas Datetime methods to summarize time series data.

### Reading Assignment

Two journal articles related to data quality checking:

- Reek, T., S.R. Doty, and T.W. Owen, 1992: A Deterministic Approach to the Validation of Historical Daily Temperature and Precipitation Data from the Cooperative Network. Bull. Amer. Meteor. Soc., 73, 753–765, https://doi.org/10.1175/1520-0477(1992)073<0753:ADATTV>2.0.CO;2

- Hu, Q. and S. Feng, 2003: A Daily Soil Temperature Dataset and Soil Temperature Climatology of the Contiguous United States. J. Appl. Meteor., 42, 1139–1156, https://doi.org/10.1175/1520-0450(2003)042<1139:ADSTDA>2.0.CO;2

### The Lab Assignment

This week’s assignment is to conduct basic data quality checking on a meteorological data with some known problems.

1. Use the file **DataQualityChecking.txt** provided with this repository.

   - This file contains daily climate data for a single site.
   - Data file is white space delimited.
   - Columns are in order:
     - date,
     - precipitation (mm),
     - maximum air temperature (°C)
     - minimum air temperature (°C), and
     - wind speed (m/s)
     
2. Write a Python script called program-09.py which does the following:

   - Imports the entire file in as a DataFrame, using date as the index.
   - Removes `No Data` values (defined as -999 in this file).
   - Completes the following data quality checks:
     - **Check 1:** Check for gross errors: 0 ≤ P ≤ 25; -25≤ T ≤ 35, 0 ≤ WS ≤ 10.
     - **Check 2:** Swap Tmax and Tmin when Tmax is less than Tmin.
     - **Check 3:** Check for temperature range greater than 25°C
   - Where a check is failed, replace the value with NaN.
   - Record the number of data points replaced for each of the three check types.
   - Plot each dataset before and after correction has been made.
     - Use a single set of axis for each variable, and
     - provide a legend that indicates which variable is the original and which is after quality checking.
   - Write data that has passed the quality check into a new file with the same format as the input data file.
   - Output information on failed checks to a separate Tab delimited file that can be imported into your Metadata file.
   
(25% total) To complete the assignment, turn in:
(5%) Working program
(5%) Program should have clear and concise header and in-line comments
Metadata file (Word or PDF) that contains
(5%) Description of the data quality checks performed and how they influenced the contents of the file.
(5%) Table with the number of corrections made for all three checks.
(5%) Plots for each variable before and after quality checking.
All files should be placed into a folder whose name includes your username, and that can be zipped and submitted as a single file through Blackboard.



1. Start by cloning this assignment to the folder where you have been completing assignments.

2. Next, complete the tutorial [Time Series Analysis with Pandas](http://earthpy.org/pandas-basics.html), but include all of the tutorial code in a Python program called **PandasDatesDemo.py** that is included in this repository.

   - The "set_printoptions()" function does not appear to work with the current version of pandas.
   - Do not set your graphics to inline (see "ln[7]:"), graphics are already prepared in the spyder interface.
   - The `!wget` command will download the data file from within the console in spyder, but can also be run directly from the Linux prompt (drop the "!" from the start of the command, this is telling the Python interpretor that the command should be run at the Linux shell and not interpreted as a Python statement).
   - What dates should you use to define the correct record length?  From the Linux prompt, use "head" and "tail" to determine the start and end dates for your data file (the tutorial was written in 2013, but the data file continues to be updated).  
   - The length of record for the AO and NAO files may not be the same, despite what the tutorial document says.  If they are not the same length, what happens when they are combined into a single DataFrame?
   - Submit the following plots for evaluation: 
     - Daily Atlantic Oscillation (AO) plot (Out [23]:)
     - Annual median values for AO (Out [48]:)
     - Rolling mean for both AO and NAO (Out [52]:)
     
3. Once you have completed the tutorial, use your new skills to write a Python script called **program-08.py** that will do the following. 

   - Read the contents of the file **WabashRiver_DailyDischarge_20150317-20160324.txt** into a Pandas dataframe.
     - This file contains daily discharge for the Wabash River at the Lafayette, Indiana gauge from March 17, 2015 through March 24, 2016.
     - Use Columns 3 and 4 for a single Datetime element.
     - Use Column 6 (discharge in cubic feet per second) for the value.
     - For this process, the following additional information may prove useful:
       - The Pandas documentation on the [read_table](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_table.html) DataFrame method.
       - More information can also be found at the [IO Tools page](http://pandas.pydata.org/pandas-docs/stable/io.html), in particular help on how to get the read function to parse the date for you automatically can be found [here](http://pandas.pydata.org/pandas-docs/stable/io.html#datetime-handling).
       - Information on how to get read_tables to handle variable white space as a separator can be found at this [discussion page](http://stackoverflow.com/questions/12021730/can-pandas-handle-variable-length-whitespace-as-column-delimeters).
       - Also note that all of this does not have to all be done in a single line statement.  You may find it easier to import the data in a more raw format, and then work it into a usable final format.  I find this approach useful when datafile quality is suspect, as it provides more options to assess problems and catch errors.  The file I have given you is pretty clean, so not necessarily representative of the types of data you will find in real life. 
   - Create a plot of daily average streamflow for the period of record, written to a PDF or PS file.
   - Using the daily average flow data, identify and plot the 10 days with highest flow, written to a PDF or PS file.  Use symbols to represent the data on the same time axis used for the full daily flow record.
   - Create a plot of monthly average streamflow for the period of record, written to a PDF or PS file.

4. Be sure that the script has a complete header comment block, appropriate in-line comments, and runs without intervention relative to where the datafile is stored in the repository.

#### What to turn in...

The following should be included in your GitHub repository:

1. A working tutorial solution file called **PandasDatesDemo.py**.

2. The original data file, **WabashRiver_DailyDischarge_20150317-20160324.txt**, provided with the repository.

3. A working program called **program-08.py**.

4. Put your input file, output files, and processing script in the assignment repository and push to GitHub to submit.

#### Grading Rubric (50 pts Total)

| Question | Description | Score |
| -------- | ----------- | ----- |
| 1. | Write a Python script to complete the following analysis | (35 pts) |
| 1.1. | Import the entire file in as a DataFrame, using date as the index | 5 pts |
| 1.2. | Remove No Data values (set to -999) | 2.5 pts |
| 1.3. | Check 1: Check for gross errors: 0 ≤ P ≤ 25; -25≤ T ≤ 35, 0 ≤ WS ≤ 10 | 5 pts |
| 1.4. | Check 2: Swap Tmax and Tmin when Tmax is less than Tmin | 5 pts |
| 1.5. | Check 3: Check for temperature range greater than 25°C | 5 pts |
| 1.6. | Where a check is failed, replace value with NaN and record the number of data points replaced for each check. | 2.5 pts |
| 1.7. | Plot each dataset before and after correction has been made.  Use a single set of axis for each variable, and provide a legend that indiactes which is the original and which is after quality checking.  | 5 pts |
| 1.8. | Output data that has passed the quality check into a new file with the same format as the input data file. | 5 pts |
| 1.9. | Output information on failed checks to a separate Tab delimited file that can be imported into your Metadata file. | 5 pts |
(25% total) To complete the assignment, turn in:
| 2. | Working program | 5 pts |
| 3. | Program should have clear and concise header and in-line comments | 2.5 pts |
| 4. | Metadata file (Word or PDF) that contains: | (7.5 pts) |
| 4.1. | Description of the data quality checks performed and how they influenced the contents of the file. | 2.5 pts |
| 4.2. | Table with the number of corrections made for all three checks. | 2.5 pts |
| 4.3. | Plots for each variable before and after quality checking. | 2.5 pts |
