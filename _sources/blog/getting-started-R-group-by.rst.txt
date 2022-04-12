.. post:: Feb 26, 2013
   :tags: R, plyr, ggplot2
   :author: misken
   :exclude:
   
   Group by analysis with R
   
Getting started with R (with plyr and ggplot2) for group by analysis
=====================================================================

We have a data file containing records corresponding to surgical cases. For each case we know some basic 
information about the patient’s scheduled case including an urgency code, the date the case was scheduled, 
insurance status, surgical service, and the number of days prior to surgery in which the case was scheduled. 
In data model terms, the first 4 variables are dimensions and the last variable is a measure. 
In R, a dimension is called a factor and each unique value of a factor is called a level. 
Of course, we could certainly use things like SQL or Excel Pivot Tables to do very useful things with this data. 
However, here we will start to see how R can be used to do the same things as well as to do some 
things that are much more difficult using SQL or Excel.

I thought I'd give RPubs a try to hosting this tutorial. `Check it out at RPubs <http://rpubs.com/misken/getting-started-R-group-by>`__.
