# rankhospital.R

## Introduction.

Download the ﬁle ProgAssignment3-data.zip ﬁle containing the data for Programming Assignment 3 from the Coursera web site. Unzip the ﬁle in a directory that will serve as your working directory. When you start up R make sure to change your working directory to the directory where you unzipped the data.

The data for this assignment come from the Hospital Compare web site (http://hospitalcompare.hhs.gov) run by the U.S. Department of Health and Human Services. The purpose of the web site is to provide data and information about the quality of care at over 4,000 Medicare-certiﬁed hospitals in the U.S. This dataset essentially covers all major U.S. hospitals. This dataset is used for a variety of purposes, including determining whether hospitals should be ﬁned for not providing high quality care to patients (see http://goo.gl/jAXFXfor some background on this particular topic).

The Hospital Compare web site contains a lot of data and we will only look at a small subset for this assignment. The zip ﬁle for this assignment contains three ﬁles:

* outcome-of-care-measures.csv: Contains information about 30-day mortality and readmission rates for heart attacks, heart failure, and pneumonia for over 4,000 hospitals.
* hospital-data.csv: Contains information about each hospital.
* Hospital_Revised_Flatfiles.pdf: Descriptions of the variables in each ﬁle (i.e the code book).

A description of the variables in each of the ﬁles is in the included PDF ﬁle named Hospital_Revised_Flatfiles.pdf. This document contains information about many other ﬁles that are not included with this programming assignment. You will want to focus on the variables for Number 19 (“Outcome of Care Measures.csv”) and Number 11 (“Hospital Data.csv”). You may ﬁnd it useful to print out this document (at least the pages for Tables 19 and 11) to have next to you while you work on this assignment. In particular, the numbers of the variables for each table indicate column indices in each table (i.e. “Hospital Name” is column 2 in the outcome-of-care-measures.csv ﬁle).

## Ranking hospitals by outcome in a state

Write a function called rankhospital that takes three arguments: the 2-character abbreviated name of a state (state), an outcome (outcome), and the ranking of a hospital in that state for that outcome (num). The function reads the outcome-of-care-measures.csv ﬁle and returns a character vector with the name of the hospital that has the ranking speciﬁed by the num argument. For example, the call

```
rankhospital("MD", "heart failure", 5)
```

would return a character vector containing the name of the hospital with the 5th lowest 30-day death rate for heart failure. The num argument can take values “best”, “worst”, or an integer indicating the ranking
(smaller numbers are better). If the number given by num is larger than the number of hospitals in that state, then the function should return NA. Hospitals that do not have data on a particular outcome should
be excluded from the set of hospitals when deciding the rankings.

#### Handling ties. 

It may occur that multiple hospitals have the same 30-day mortality rate for a given cause of death. In those cases ties should be broken by using the hospital name. For example, in Texas (“TX”), the hospitals with lowest 30-day mortality rate for heart failure are shown here.

```
> head(texas)
        Hospital.Name                       Rate    Rank
3935    FORT DUNCAN MEDICAL CENTER          8.1     1
4085    TOMBALL REGIONAL MEDICAL CENTER     8.5     2
4103    CYPRESS FAIRBANKS MEDICAL CENTER    8.7     3
3954    DETAR HOSPITAL NAVARRO              8.7     4
4010    METHODIST HOSPITAL,THE              8.8     5
3962    MISSION REGIONAL MEDICAL CENTER     8.8     6


The function should use the following template:

```
best <- function(state, outcome) {
    ## Read outcome data
    ## Check that state and outcome are valid
    ## Return hospital name in that state with lowest 30-day death
    ## rate
}
```

The function should check the validity of its arguments. If an invalid state value is passed to best, the function should throw an error via the stop function with the exact message “invalid state”. If an invalid outcome value is passed to best, the function should throw an error via the stop function with the exact message “invalid outcome”.

Save your code for this function to a ﬁle named best.R. Use the submit script provided to submit your solution to this part. There are 3 tests that need to be passed for this part of the assignment.
