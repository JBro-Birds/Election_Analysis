# Election_Analysis

## Overview of Project
The project is to complete tasks that will provide election audit details needed by the customer to discuss with the Colorado Board of Elections.  Initially the project called for candidate-based information, (total number of votes cast, complete list of candidates who received votes, total number of votes each candidate received, percentage of votes each candidate won, and the winner of the election based on popular votes), but the election board has requested additional data to complete the audit, (voter turnout for each county, percentage of votes from each county out of the total count, and county with highest turnout).  The election data is stored in a .CSV file and Python programming is being used to read the file, slice the data based on the info needed and write the output of the results to a .txt file. 

### Purpose
The purpose of this project is to complete the additional request made by the election board to determine voter turnout for each county, percentage of votes from each county out of the total count, and county with highest turnout.  The results of this county-based information will be included with the customer-based results to provide the customer, and in turn the election board, the requested election analysis needed as part of their election audit.  The data for this additonal request is included in the same dataset .CSV file that contains the candidate-based data and a similar programming process will be followed using Python and writing the results .txt file.

## Results

### Coding
For the front-end user there are two macro buttons on the analysis worksheet, one for clearing data on the worksheet of a prior run and one for running the analysis for a given year.  The macro button asking the user for what year the analysis is for is an input box in which the user needs to enter a year.  The main part of the clear data script is `Cells.Clear` and for the the year selection input box script it is `yearValue = InputBox("What year would you like to run the analysis on?")`.  The year selection box is the first step in the `Sub AllStocksAnalysisRefactored()` refactored script.  After the user enters a year and clicks 'enter' a runtime timing variable `startTime = Timer` starts running as the starting point of the total process time that is shown at the end of the script; in addition the worksheet header in cell A1 is updated to include the year entered. 

A key component of the refractor script is defining the array `Dim tickers(12) As String` and initializing the 12 tickers; starting with the first ticker `tickers(0) = "AY"` and ending with the final ticker `tickers(11) = "VSLR"`.  Three output arrays are defined for the use in `for` loops and `if-then` statements in order for data to be stored as the script runs through the ticker index `tickerIndex = 0`  These three arrays are defined as follows:  `Dim tickerVolumes(12) As Long`, `Dim tickerStartingPrices(12) As Single`, `Dim tickerEndingPrices(12) As Single`.  These three arrays are initially set to "0" for the purpose of `for` loops and `if-then` statements.  

Next a `for` loop determines the dataset range `For i = 2 To RowCount` (with `Rowcount` defined as `RowCount = Cells(Rows.Count, "A").End(xlUp).Row`) and pulls the volume data by `tickerIndex` with the following formula:  `tickerVolumes(tickerIndex) = tickerVolumes(tickerIndex) + Cells(i, 8).Value`.  Next an `if-then` block determines the starting and ending rows for each `tickerIndex` and when to move on to the next `tickerIndex` in order to pull the `tickerStartingPrices(i)` and `tickerEndingPrices(i)`.  These formulas are as follows:  
`If Cells(i - 1, 1).Value <> tickers(tickerIndex) And Cells(i, 1).Value = tickers(tickerIndex) Then tickerStartingPrices(tickerIndex) = Cells(i, 6).Value` 

`If Cells(i + 1, 1).Value <> tickers(tickerIndex) Cells(i, 1).Value = tickers(tickerIndex) Then tickerEndingPrices(tickerIndex) = Cells(i, 6).Value`.

`If Cells(i, 1).Value = tickers(tickerIndex) And Cells(i + 1, 1).Value <> tickers(tickerIndex) Then tickerIndex = tickerIndex + 1`

After pulling the array data by `tickerIndex` a `for` loop is run to populate the defined and corresponding cells in the "All Stocks Analysis" worksheet. These values are for `tickers(i)`, `tickerVolume(i) and "Return" formulated as `tickerEndingPrices(i) / tickerStartingPrices(i) - 1`.

The script runs through a number of formatting statements and then the `endTime = Timer` is triggered.  The `endTime` less `startTime` is the total elasped time of the `Sub AllStocksAnalysisRefactored()` execution and a messagebox will appear to the end user stating the execution time.  `MsgBox "This code ran in " & (endTime - startTime) & " seconds for the year " & (yearValue)`.

### Original Script Runtimes
The original script runtimes for 2017 and 2018 are as follows:

#### 2017
![2017 Stocks - Original Script](https://raw.githubusercontent.com/JBro-Birds/stock-analysis/master/Resources/VBA_Challenge_2017_OriginalScript.png)

#### 2018
![2018 Stocks - Original Script](https://raw.githubusercontent.com/JBro-Birds/stock-analysis/master/Resources/VBA_Challenge_2018_OriginalScript.png)






### Refactored Script Runtimes

#### 2017
![2017 Stocks - Refactored Script](https://raw.githubusercontent.com/JBro-Birds/stock-analysis/master/Resources/VBA_Challenge_2017_RefactoredScript.png)

#### 2018
![2018 Stocks - Refactored Script](https://raw.githubusercontent.com/JBro-Birds/stock-analysis/master/Resources/VBA_Challenge_2018_RefactoredScript.png)


## Summary

### Advantages and disadvantages of refactoring code in general
