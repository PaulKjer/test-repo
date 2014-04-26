##	Getting and Cleaning Data Project

The script required to run this analysis can be found in **run_analysis.R** in this repo.
Command level documentation is provide in the run_analysis.R script.

####	Key Assumptions
*  	The data has been downloaded and unzipped and the directory is available within the working directory.
	This assumption is based on the evalation rubric, which says – “can be run as long as the Samsung data is in your working directory.“
*	For our purposes, the data in the “Inertial Signals” directories is not required.  
*	The subjects in the training dataset and the testing dataset are the same subjects – combining them into a single
	dataset will not invalidate the data. 
*  	For our purposes, only measurements ending in mean() and std() will be used - we will not include meanfreq(), for example.
*	All of the column names should be unique - some of the variable names in the initial train and test dataset are
	non-unique.  This is assumed to be an error and repeated column labels will be replaced with unique label values. 
*	A single tidy dataset, representing the means of the selected variables for each subject/activity combindation
	is the only desired output. 
	

####	Outline of Approach

#####	1.  COMBINE THE DATA INTO A SINGLE DATASET
*	Use _cbind_ to combine the variable descriptions with the measured values for both train and test, creating two 
	datasets from the six we started with
*	Use _rbind_ to combine the train and test datasets we created above into a single dataset.

#####	2.  LIMIT THE DATA TO ONLY MEASURES OF MEAN AND STANDARD DEVIATION
*	Use _grep_ to select only those variables that end in either mean() or std()

#####	3.  ASSIGN MEANINGFUL NAMES TO ACTIVITIES
*	assign meaningful labels by subsetting the six numeric activities one at a time and assigning the corresponding label from 
	activity label. 

#####	4.  CREATE UNIQUE COLUMN NAMES
*	use _colnames_ to replace non-unique column names 

#####	5.  DETERMINE AND ASSIGN THE MEAN VALUES FOR UNIQUE SUBJECT\ACTIVITY COMBINATIONS
*	Use _melt_ and _decast_ to reduce the dataset down to only the means of our selected variables and the identifiers

#####	6.  WRITE THE DATASET TO A CSV TABLE
*	Use write.table to write the resulting tidy dataset.

####	Output Table Format

The output table is a comma delimited CSV table with the structure outlined in the table below. 


| Subject-ID  |  Activity Name  |  First Measured Variable | 67 Other Measured Variables | Last Measured Variable |
|-------------|-----------------|-----------------------|---|----------------------|
| 1           |  meaningful activity name  | mean of variable for the combination of subject/activity
| 2 - 29 | each of the 30 subjects has six activties | | | |
| 30          |                 |                         |                        |
