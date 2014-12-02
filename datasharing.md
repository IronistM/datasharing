How to share data with a statistician
========================================================
author: Manos P
date: 2014-05-11

What is this about
========================================================

This is a guide for anyone who needs to share data with an analyst. The target audiences I have in mind are:

- Business user who need analysts to analyze data for them
- IT members whose job it is to collate/clean data sets, and of course
- Analysts 


The goals of this guide are to provide some instruction on the best way to share data to avoid the most common pitfalls
and sources of delay in the transition from data collection to data analysis. The number one source of variation in the speed to results is the status of the data when they arrive at the analyst. *Based on my conversations with other analysts this is true nearly universally.*

Purpose
========================================================

My strong feeling is that statisticians should be able to handle the data in whatever state they arrive. It is important
to see the raw data, understand the steps in the processing pipeline, and be able to incorporate hidden sources of
variability in one's data analysis. On the other hand, for many data types, the processing steps are well documented
and standardized. So the work of converting the data from raw form to directly analyzable form can be performed 
before calling on a statistician. This can dramatically speed the turnaround time, since the statistician doesn't
have to work through all the pre-processing steps first. 

Taxonomics
========================================================
For maximum speed in the analysis this is the information you should pass to a statistician:

1. The raw data.
2. A [tidy data set](http://vita.had.co.nz/papers/tidy-data.pdf) 
3. A code book describing each variable and its values in the tidy data set.  
4. An explicit and exact recipe you used to go from 1 -> 2,3 

Let's look at each part of the data package you will transfer. 

Teh RaW dAta
========================================================
It is critical that you include the rawest form of the data that you have access to. Here are some examples of the
raw form of data:

* The strange [log file](http://en.wikipedia.org/wiki/Computer_data_logging) that [Splunk](http://www.splunk.com/) just spit out
* The unformatted Excel file with 10 worksheets the company you contracted with sent you
* The complicated [JSON](http://en.wikipedia.org/wiki/JSON) data you got from scraping the [Twitter API](https://twitter.com/twitterapi)
* The hand-entered numbers you collected from various Internet sources

You know the raw data is in the right format if you: 
========================================================
1. Ran no software on the data
1. Did not manipulate any of the numbers in the data
1. You did not remove any data from the data set
1. You did not summarize the data in any way

If you did any manipulation of the data at all it is not the raw form of the data. Reporting manipulated data
as raw data is a very common way to slow down the analysis process, since the analyst will often have to do a
forensic study of your data to figure out why the raw data looks weird. 

The tidy set
========================================================
The general principles of tidy data are laid out by [Hadley Wickham](http://had.co.nz/) in [this paper](http://vita.had.co.nz/papers/tidy-data.pdf)
and [this video](http://vimeo.com/33727555). The paper and the video are both focused on the [R](http://www.r-project.org/) package, which you
may or may not know how to use. Regardless the four general principles you should pay attention to are:

1. Each variable you measure should be in one column
1. Each different observation of that variable should be in a different row
1. There should be one table for each "kind" of variable
1. If you have multiple tables, they should include a column in the table that allows them to be linked

The code book
========================================================

For almost any data set, the measurements you calculate will need to be described in more detail than you will sneak
into the spreadsheet. The code book contains this information. At minimum it should contain:

1. Information about the variables (including units!) in the data set not contained in the tidy data 
1. Information about the summary choices you made
1. Information about the experimental study design you used

How to code variables
=========
When you put variables into a spreadsheet there are several main categories you will run into depending on their [data type](http://en.wikipedia.org/wiki/Statistical_data_type):

1. Continuous
1. Ordinal
1. Categorical
1. Missing 
1. Censored

What you should expect from the analyst
====================
<small>
When you turn over a properly tidied data set it dramatically decreases the workload on the statistician. So hopefully
they will get back to you much sooner. But most careful statisticians will check your recipe, ask questions about
steps you performed, and try to confirm that they can obtain the same tidy data that you did with, at minimum, spot
checks.

You should then expect from the statistician:

1. An analysis script that performs each of the analyses (not just instructions)
1. The exact computer code they used to run the analysis
1. All output files/figures they generated. 
<small/>
