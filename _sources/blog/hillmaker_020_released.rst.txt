.. post:: Feb 05, 2020
   :tags: python, hillmaker, occupancy analysis
   :author: misken
   
   Some updates to hillmaker

Hillmaker updates
==================

Finally got around to making some enhancements to `hillmaker <https://github.com/misken/hillmaker>`_. 
The enhancements were motivated by a couple of real projects - one involving healthcare staffing
and the other involving using hillmaker to analyze the number of CPU cores in use in a 
high performance computing cluster. The primary changes are:

* Can specify multiple category fields and they can be strings or integers.
* Can get aggregate statistics over all the category fields.
* Can specify an occupancy weight field to use for creating workload hills.
* Can specify which, if any, occupancy percentiles to compute (default is [0.50, 0.75, 0.95, 0.99]).
* Fixed use of deprecated pandas functions to be compliant with pandas 1.0.0+.
* Added ability to treat arrival and departure bins as either full occupancy or partial occupancy based on fraction of bin actually there (this is now consistent with old Access version). Default is still fractional contribution in arrival and departure bins.
* Did a bunch of code cleanup both involving style as well as replacing some of my homegrown datetime functions with new pandas functions.
* Made sure all functions have proper docstrings.

A few things haven't changed:

* main GitHub site is still `https://github.com/misken/hillmaker <https://github.com/misken/hillmaker>`_
* You can install using pip or conda or using source from GitHub
* There still needs to be much better documentation.

In order to illustrate the new features and help users get started with the new version, I've created
a `new Jupyter notebook for getting started with the new version <https://github.com/misken/hillmaker-examples/blob/master/notebooks/basic_usage_shortstay_unit_multicats.ipynb>`_. Just follow the link to see the rendered version.

In addition to the new notebook, you can find other example Python scripts at my  `hillmaker-examples repo on GitHub <https://github.com/misken/hillmaker-examples>`_. 

