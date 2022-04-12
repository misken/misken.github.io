.. post:: Feb 26, 2013
   :tags: python, pandas, matplotlib
   :author: misken
   :exclude:
   
   Group by analysis with Python


Getting started with Python (with pandas and matplotlib) for group by analysis
=================================================================================

We have a data file containing records corresponding to surgical cases. 
For each case we know some basic information about the patient's scheduled 
case including an urgency code, the date the case was scheduled, insurance 
status, surgical service, and the number of days prior to surgery in 
which the case was scheduled. In data model terms, the first 4 variables 
are dimensions and the last variable is a measure. Of course, we could certainly 
use things like SQL or Excel Pivot Tables to do very useful things with this data. 
In a previous [tutorial](http://hselab.org/getting-started-R-group-by.html) I showed how R can be used to do the same things
as well as to do some things that are much more difficult using SQL or Excel. 
In this tutorial I'll do the same things as in the R tutorial but will use Python instead.
 
Check out the tutorial at <http://nbviewer.ipython.org/github/misken/hselab-tutorials/blob/master/ORSchedLeadTime_Python.ipynb>`__
