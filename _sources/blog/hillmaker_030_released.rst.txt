.. post:: May 19, 2022
   :tags: python, hillmaker, occupancy analysis
   :author: misken
   :exclude:
   
   Performance improvements to hillmaker

numpy speeds up hillmaker dramatically
=======================================

The first Python versions of hillmaker (0.1.0 - 0.2.3) were focused on just getting it
working correctly. Speed was a secondary concern. Most computations were
done directly in pandas including a lot of "cell" updating of a pandas
dataframe. All of this dataframe updating made things slow.

Recently I overhauled the way that the occupancy by datetime values were
being computed:

- converted pandas ``Series`` to numpy ndarrays, 
- tried to do almost all computations via vectorized operations on numpy arrays.

I also fixed a dumb thing I was doing in computing the percentiles by making
sure I passed the entire list of desired percentiles to the pandas ``percentile``
function (I was iterating through a list of percentiles - oops).

It worked. My standard benchmark dataset (``ShortStay.csv``) is just under 60k records
with five unique category (patient type) values. Running hillmaker with
a bin size of 60 minutes took about one minute on a standard laptop. After
the numpy related changes, the same run is ~8 seconds. Of that, between 6-7
seconds are devoted to the summary statistic computations (pandas). Perhaps
that can be sped up, but it's not worth my time right now to worry about it.

This new version is 0.3.0. I haven't uploaded PyPi yet as I really need
to write some more documentation first. In addition to the speedup, I also:

* added a CLI
* added flow conservation checks (to make sure occupancy is conserved and all entities are counted)
* added logging using `logger` module
* deprecated use of multiple category fields and reverted to previous functionality of a single (optional) category field. Multiple categories are best handled with composite keys.

A few things haven't changed:

* main GitHub site is still `https://github.com/misken/hillmaker <https://github.com/misken/hillmaker>`_
* You can install this latest version using source from GitHub
* There still needs to be much better documentation.
* There's still no GUI (like as in the old MS Access version)

I'm really hoping to get documentation written this summer.
