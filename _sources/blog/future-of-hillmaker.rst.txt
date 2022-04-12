.. post:: Feb 28, 2013
   :tags: python, occupancy analysis
   :author: misken
   :exclude:
   
   From Access to Python

Future of Hillmaker
===================

Many years ago I created an MS Access add-in called Hillmaker for doing
time of day and day of week based occupancy analysis in health care
delivery systems. A typical use would be to find the mean and 95th
percentile of occupancy in a set of nursing units or an emergency
department. `Hillmaker <http://sourceforge.net/projects/hillmaker/>`__
was released as an open source project back in 2005 and has gotten quite
a bit of use. However, I never really did any more development on it
even though there were a number of enhancements that I (and many others)
would like to have seen. The only attention it has gotten from me was in
response to the object library problems caused by new releases of MS
Office. No fun.


While VBA is fine, I've always wanted to make Hillmaker less MS-centric
and to decouple it from MS Access. Installing Access add-ins can be a
hassle as they require changes to the Windows registry and some
corporate settings frown on this. So, I hacked together a proof of
concept version using Python with the
`pandas <http://pandas.pydata.org/>`__ module for some of the number
crunching and with `matplotlib <http://matplotlib.org/>`__ for plotting.
Seems to work. Seems to be fast. Made it work with text files, Excel,
Access and SQL Server based data.

Now I need to find the time to turn it into a real Python based app.



