.. post:: Mar 15, 2022
   :tags: python, conda
   :author: misken
   :exclude:
   
   Use the right pip when installing into conda envs

Using pip with conda for local development projects
====================================================

**UPDATE: 2022-07-19** While working on my `hillmaker <https://github.com/misken/hillmaker>`_ project,
I made another finding on this issue and have updated the blog post accordingly. You can see this
new method in the context of hillmaker by checking out the `basic usage notebook (html version) <https://misken.github.io/hillmaker-examples/basic_usage_shortstay_unit_043.html>`_ and
scrolling down to the part about installing hillmaker using pip.

I've wasted so much time on this issue over the last few years that I finally decided to better
document a process for doing it correctly.

**tldr:** How to use pip to install your own local Python modules in a conda virtual environment:

* Create your conda environment and make sure you install pip using conda
* Activate your conda environment
* When pip installing a local Python project (either in "editable mode" or not) you need to make sure that you are using the pip that is part of your conda env and NOT the pip that's in your base conda env nor the pip that is in your system Python.
* While supposedly running pip from a conda env *should* use the pip installed in that env, it is **not** necessarily true.
* To ensure you run the correct pip, include the path to the pip executable inside your conda env.
* To make this easier you can create an alias or shell function to call the correct pip without typing a long path.
* Ideally, avoid doing additional conda installs into this env after doing any pip installs. If needed, better to recreate the env, include the new conda installs, and then redo the pip installs.

Key resources include:

* `Using pip in a conda environment (from Anaconda blog) <https://www.anaconda.com/blog/using-pip-in-a-conda-environment>`_
* `Using Pip to install packages to Anaconda Environment (SO post) <https://stackoverflow.com/questions/41060382/using-pip-to-install-packages-to-anaconda-environment>`_

Background
-----------

Here's the scenario. You do scientific computing in Python and as part of your work you end up
developing some useful little library - let's call it ``qng.py``. Yes, it's a library of queueing related
functions. You might not have it in good enough shape to release
into the wild via PyPI but you find yourself using it quite a bit and are tired of (and embarassed by) copying the
``qng.py`` file into multiple projects that use it. So, you create a proper Python project structure so that you
can create a deployable package. Here's a simplified version of the actual project structure:

.. code-block:: console

	├── docs
	├── LICENSE
	├── README.md
	├── .gitignore
	├── setup.py
	├── src
	│   ├── qng
	│   │   ├── __init__.py
	│   │   └── qng.py
	├── tests
	│   ├── test_ipython.py
	│   └── test_qng.py


To create my project folder structure I use a simple `cookiecutter template <https://drivendata.github.io/cookiecutter-data-science/>`_ that I've adapted for my projects.

Here's what my ``__init__.py`` file looks like:

.. code-block:: python

	from qng import qng

Doing this will allow to do my imports as ``from qng import qng`` so that within my code
I can do things like calling ``qng.<some function>(<some args>)``.


My conda virtual environment
-----------------------------

I've got a standard conda virtual environment called ``analytics`` containing a bunch of the standard packages I use such as
numpy, pandas, scikit-learn, simpy and a number of others. Here's what my YAML file looks like:

.. code-block:: console

	name: analytics
	channels:
	  - defaults
	  - conda-forge
	dependencies:
	  - numpy
	  - pandas
	  - scipy
	  - scikit-learn
	  - matplotlib
	  - seaborn
	  - ipykernel
	  - simpy
	  - networkx
	  - statsmodels
	  - cookiecutter
	  - pyyaml
	  - pytest
	  - pip

**Notice that I'm using conda to install pip.**

The problem
------------

Now I want to install my ``qng`` module into my ``analytics`` virtual environment. I need
to use ``pip -e .`` from my main ``qng`` project folder to do this. 

.. note::
   For a while there was a ``conda develop`` command which worked like ``pip install -e .`` (install in “editable mode”) but 
   this seems to have been (or planned to be) deprecated. 
   This `SO post <https://stackoverflow.com/questions/49474575/how-to-install-my-own-python-module-package-via-conda-and-watch-its-changes>`_ 
   and `linked Github issue <https://github.com/conda/conda-build/issues/4251>`_ discusses the reasons for deprecating ``conda develop``.

Let's confirm that 
pip is indeed installed in my ``analytics`` conda env:

.. code-block:: console

	(analytics) user:~$ conda list | grep 'pip'

	pip                       21.2.4                   pypi_0    pypi

	(analytics) user:~$ which pip
	/home/user/anaconda3/envs/analytics/bin/pip


But, if I do the following:

.. code-block:: console

	cd ~/Documents/dev/qng
	pip install -e .
	
the ``qng`` package does **NOT** get installed in the ``analytics`` env, but ends up getting installed 
in the Anaconda base environment.

.. code-block:: console

	(analytics) user:~$ deactivate
	(base) user:~$ conda list | grep 'qn'
	qng                       0.1.0                     dev_0    <develop>

I then confirmed that ``qng`` gets installed as ``/home/user/anaconda3/lib/python3.8/site-packages/qng.egg-link``. This
egg-link file contains:

.. code-block:: console

	/home/user/Documents/dev/qng/src
	../

But, if I explicitly use ``pip`` in the analytics environment, then qng gets installed in that environment:

.. code-block:: console

	(analytics) user:~/Documents/development/qng$ ~/anaconda3/envs/analytics/bin/pip install -e .
	Obtaining file:///home/user/Documents/development/qng
	Installing collected packages: qng
	  Running setup.py develop for qng
	Successfully installed qng-0.1.0
	(analytics) user:~/Documents/development/qng$ conda list | grep 'qn'
	qng                       0.1.0                     dev_0    <develop>

Furthermore, I launched Jupyter Lab from the ``analytics`` env and was able to import and use the ``qng`` library:

.. code-block:: python

	from qng import qng
	print(qng.erlangb(5.0, 6))
	
	0.19184725888636506

.. note::
	The ``erlangb`` function returns the probability of loss in an $M/G/c/c$ queueing system - see `Erlang B formula <https://en.wikipedia.org/wiki/Erlang_(unit)#Erlang_B_formula>`_

Of course, it's a pain to type ``~/anaconda3/envs/analytics/bin/pip install -e .`` and easy to forget to include the path.
So, I created a few aliases to use ``pip`` from whichever Anaconda env is activated. Here's the lines I
added to my ``.bash_aliases`` file.

.. code-block:: console

	alias cpip='"$CONDA_PREFIX"/bin/pip'
	alias cpipdot='"$CONDA_PREFIX"/bin/pip install --use-feature=in-tree-build .'
	alias cpipedot='"$CONDA_PREFIX"/bin/pip install -e .'


Notice the use of the environment variable ``$CONDA_PREFIX``. It gets set automatically whenever a
conda env is activated. This makes the aliases usable from any conda env. If the ``analytics``
env is activated, then ``$CONDA_PREFIX=/home/user/anaconda3/envs/analytics``

Then, if I want to ``pip`` install some package from PyPI, I just do ``cpip <package-to-install>``.


To do an install of a local package, I can just do ``cpipdot`` for a regular install and ``cpipedot`` for an editable install.

BTW, this same issue of the system ``pip`` getting used by default (even if run from an active conda environment prompt) 
also applies to running python (i.e. which ``python.exe`` file gets used) from the command line! I need to do /home/user/anaconda3/envs/analytics/bin/python if 
I want to get an IDLE prompt within the active conda environment.

As I mention at the start of this post, I have an update on this very issue.

UPDATE 2022-07-19
------------------

My hillmaker package has both a CLI and is importable. By following the steps above, I was able
to make it importable from within my conda virtual environment, but the runnable `hillmaker` script
kept getting installed into the base conda environment. More digging led to the following solution.

.. code-block:: console

	$ ~/anaconda3/envs/<conda venv name>/bin/python -m pip install hillmaker


The reason for the more convoluted install command when using conda virtual environments is that it turns out to be rather tricky to properly pip install something into a conda virtual environment. This is the source of much confusion and much discussion on StackOverflow. It boils down to making sure that you are using the `pip` executable **in your conda virtual environment** and **NOT** in your base conda environment. This `SO post <https://stackoverflow.com/questions/41060382/using-pip-to-install-packages-to-anaconda-environment/56889729#56889729>`_ explains how the use of the `-m` flag helps in this regard. However, this post doesn't appear to mention that the same issue applies to the `python` executable itself. Again, you **MUST** make sure you are using the `python` executable in your conda virtual environment and not in your conda base environment. 


PS - Notes about non-editable local installs and eggs
------------------------------------------------------

In the ``cpipdot`` alias we are doing a ``pip install --use-feature=in-tree-build .`` command. I'm using
the ``--use-feature=in-tree-build`` option due to a deprecation warning I got when I tried a standard
``pip install .`` command. This is just confirming that the install will still work correctly when
``pip`` changes to *in-tree builds* (i.e. not using an "out of tree" temporary folder) - see `https://github.com/pypa/pip/issues/7555 <https://github.com/pypa/pip/issues/7555>`_. 

Anyway, after installing in this manner, I just wanted to confirm and document where the local package ends up
getting installed. As expected, we got a ``qng`` folder containing source code in
``/home/user/anaconda3/envs/analytics/lib/python3.10/site-packages/``. I also confirmed that after installing
in this way, I could successfully use the ``qng`` module from Jupyter Lab launched from the ``analytics`` env.

I did also notice that I had a ``qng.egg-info`` folder in my ``qng/src`` folder:

.. code-block:: console

	(base) user:~/Documents/development/qng/src/qng.egg-info$ ls
	dependency_links.txt  PKG-INFO  SOURCES.txt  top_level.txt

Was this residue from the -e build? Actually, it seems that this folder gets created whether I install my package in
editable or non-editable model. I knew that eggs were similar to Java JAR files and were simply compressed archives
used to distribute code bundles. Eggs appear to be somewhat obsolete and superceded by wheels and at least
for non-editable installs, nothing bad seems to happen if I delete the ``qng.egg-info`` folder. A few good
resources on eggs (and pip and conda) include:

* `What is a Python egg? <https://stackoverflow.com/questions/2051192/what-is-a-python-egg>`_
* `What is the difference between pip and conda? <https://stackoverflow.com/questions/20994716/what-is-the-difference-between-pip-and-conda/68897551#68897551>`_

 
