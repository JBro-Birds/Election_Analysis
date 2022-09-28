# Election_Analysis

## Overview of Project
The project is to complete tasks that will provide congressional election audit details needed by the customer to discuss with the Colorado Board of Elections.  Initially the project called for candidate-based information, (total number of votes cast, complete list of candidates who received votes, total number of votes each candidate received, percentage of votes each candidate won, and the winner of the election based on popular votes), but the election board has requested additional data to complete the audit, (voter turnout for each county, percentage of votes from each county out of the total count, and county with highest turnout).  The election data is stored in the elections_result.CSV file and Python programming is being used to read the file, slice the data based on the info needed and write the output of the results to the electons_result.txt file. 

### Purpose
The purpose of this project is to complete the additional request made by the election board to determine voter turnout for each county, percentage of votes from each county out of the total count, and county with highest turnout.  The results of this county-based information will be included with the customer-based results to provide the customer, and in turn the election board, the requested election analysis needed as part of their election audit.  The data for this additonal request is included in the same elections_result.CSV file that contains the candidate-based data and a similar programming process will be followed using Python and writing the results to the elections_result.txt file.

## Results

### Election-Audit Results
* 369,711 votes were cast in the congressional election.

* The number of votes and the percentage of total votes for each county in the precinct is as follows:
  * Jefferson: 10.5% (38,855)
  * Denver: 82.8% (306,055)
  * Arapahoe: 6.7% (24,801)

* Denver County had the largest number of votes.

* The number of votes and the percentage of the total votes each candidate received is as follows:
  * Charles Casper Stockham: 23.0% (85,213)
  * Diana DeGette: 73.8% (272,892)
  * Raymon Anthony Doane: 3.1% (11,606)

* The winner of the election is Diana DeGette who has 272,892 votes which equates to 73.8% of the total votes.

## Election Audit Summary

### Re-use of this script for future election audits
This script provided for this election audit can be used for future election audits with some modifications.  One modification would be to include the time period (month/year) to the election_results.CSV and election_results.txt file names in order to better organize the result files.  The script can be updated for each election period run by editing the file names .CSV and .txt file names so the reader and write functions know the corresponding file to use.  The update would be needed in the following lines of code:
`file_to_load = os.path.join("Resources", "election_results.csv")`
`file_to_save = os.path.join("analysis", "election_results.txt")`
In addition the .txt file analysis output can include the "time period" as part of the "Election Results" title row by including the "month/year" after the "Election Results" string in the following print code: `f"\nElection Results\n"`

Another useful modification would be to show candidate data by county.  This could be done by defining `arrays` for candidate_county data, including a `for loop` to collect the candidate-by-county data and updating the output code to the .txt file to include the candidate-by-county outcome.
