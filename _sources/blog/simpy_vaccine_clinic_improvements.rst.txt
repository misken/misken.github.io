.. post:: Apr 11, 2022
   :author: misken
   :tags: python, simpy, simulation
   :exclude:
   
   Improving our SimPy vaccine clinic model
   
Using SimPy to simulate a vaccine clinic - Part 2: model improvements
======================================================================

In `Part 1 <https://misken.github.io/blog/simpy_getting_started_vaccine_clinic/>`_, we created a simple simulation model of a vaccine clinic
using `SimPy <https://simpy.readthedocs.io/en/latest/>`_. Now we'll make
a number of improvements to our model and use it to explore a few scenarios. Some of
the things we'll do include:


* adding a command line interface,
* specifying simulation inputs via a configuration file,
* automating the post-processing of simulation outputs to create summary statistics,
* move our code out of a Jupyter notebook and into a Python script,
* explore several clinic capacity plans using the simulation model,
* make some model extensions including handling two arrival streams - random arrivals and scheduled arrivals.

This series of notebooks and Python scripts are part of a module I teach
in one of my analytics courses. In addition to all of the files needed
for the module, I have also created a number of screencasts that walk
you through all of the pieces. So, instead of trying to repeat all that
in a blog post, I'll just point you to the course web page for this module.
The entire courseweb is a Sphinx based site.

* `Discrete event simulation with SimPy <http://www.sba.oakland.edu/faculty/isken/courses/mis6900_s22/mod4_des_simpy.html>`_
