
#############################################################################################
:date: 2013-12-18 16:11
:author: mark
:tags: python, pandas, matplotlib
:slug: learning-python-suggestions-and-resources-for-business-analytics-students-and-professionals

.. post:: Dec 18, 2013
   :tags: python, pandas, matplotlib
   :author: misken
   :exclude:
   
   Learning Python for analytics

Learning Python - suggestions and resources for business analytics students and professionals
==============================================================================================

.. note::
    (Apr 12, 2022) This post is hilariously old and outdated but it's fun to look back.
     
.. raw:: html

   <div
   class="field field-name-body field-type-text-with-summary field-label-hidden">

.. raw:: html

   <div class="field-items">

.. raw:: html

   <div class="field-item even" property="content:encoded">

As I've been learning and using Python more and more for business
analytics'ey things that I previously would have done in Excel or Access
with some VBA sprinkled in, I thought it would be a good idea to put
together a list of some of the resources I've found to be useful. As you
start to read this, you'll notice that there are quite a few references
to "scientific computing" and "scientists". There are many similarities
between the scientific computing (as done by computing inclined
scientists) and the business analytics computing done by business
analysts. Both are communities of folks whose full time job is NOT to
develop software but who do end up using sophisticated computing tools
and doing a fair bit of computer programming. Both are dealing with
increasingly large and varied data sets. Both need to worry about
efficient and reproducible workflows. Many in both camps do end up
developing software tools. Both are increasingly turning to tools like
Python and R. Both need good resources for learning to effectively use
such tools. Business analytics people are very comfortable creating
crazy big Excel spreadsheets, dabbling in SQL, and maybe doing some VBA
programming. The parallel world of tools like Python and R requires some
getting used to but is well worth the investment in time (IMHO).

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter toc-filter-number">

.. raw:: html

   <div class="toc-filter-content">

Contents
~~~~~~~~

#. `What is Python and why is it called
   Python? <#what-is-python-and-why-is-it-called-python->`__
#. `Which Python? <#which-python->`__
#. `Setting up your sci-computing Python
   environment <#setting-up-your-sci-computing-python-environment>`__
#. `Writing Python programs <#writing-python-programs>`__
#. `Collections of links to
   tutorials <#collections-of-links-to-tutorials>`__
#. `General and data science focused Python tutorials and
   [e]Books <#general-and-data-science-focused-python-tutorials-and-e-books>`__
#. `Open access courses <#open-access-courses>`__
#. `Toolbox <#toolbox>`__
#. `Musings on Python, open source software and reproducible
   analysis <#musings-on-python-open-source-software-and-reproducible-analysis>`__
#. `General Python resources <#general-python-resources>`__
#. `The Python packaging ecosystem <#the-python-packaging-ecosystem>`__

.. raw:: html

   </div>

.. raw:: html

   </div>

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top first">

`Back to top <#top>`__

.. raw:: html

   </div>

1. What is Python and why is it called Python?
----------------------------------------------

.. raw:: html

   </p>

`Python (programming
language) <http://en.wikipedia.org/wiki/Python_%28programming_language%29>`__

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

2. Which Python?
----------------

.. raw:: html

   </p>

As you get started learning Python, it's unavoidable that you'll run
into the `Python 2 vs Python 3
question <https://wiki.python.org/moin/Python2orPython3>`__ question.
For now, I'm still using Python 2.7.3. Before downloading Python from
`python.org <http://python.org/>`__, read the next section of setting up
your sci-computing Python environment.

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

3. Setting up your sci-computing Python environment
---------------------------------------------------

.. raw:: html

   </p>

While you can certainly get Python and the various modules needed to get
yourself setup to do some analytics or sci-computing, it's easier to
install one of the `prepackaged Python
distributions <http://www.scipy.org/install.html>`__ containing the
`SciPy Stack <http://www.scipy.org/stackspec.html#stackspec>`__. The
SciPy Stack specification contains the minimal set of Python packages
one should have for sci-computing and includes things like Python
itself, numpy, scipy, matplotlib, pandas, IPython, Sympy, and nose. Of
course, there are a zillion more useful packages, some of which I'll
mention below. I have had good luck with the `Enthought
Canopy <https://www.enthought.com/products/canopy/>`__ Python
distribution for scientific computing. It includes not only the SciPy
Stack but a ton of other useful packages. In addition, it's got an
integrated update manager that makes it easy to keep all your
sci-computing packages up to date. Since Canopy uses virtualenv to
create its own virtual Python environment, local users can handle all
their own updates and you don't mess around with your core Python
system. Canopy also has a built in code editor and embedded IPython
console.

.. raw:: html

   </p>

Recently (Feb 2014) I installed another leading sci-computing Python
distro - `Anaconda from Continuum
Analytics <https://store.continuum.io/cshop/anaconda/>`__. It looks
every bit as good as Canopy and I'm looking forward to working with it.

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

4. Writing Python programs
--------------------------

.. raw:: html

   </p>

Now that you've got Python installed, what tools will you use to write
Python programs? Also, since Python can be used in "interactive mode",
you'll also want some tools for doing that. Let's look at tools for
interactive use first since that's a natural way to start to learn to
program in Python.

.. raw:: html

   </p>

Using Python interactively
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

Python ships with a bare bones interactive console called
`IDLE <http://en.wikipedia.org/wiki/IDLE_%28Python%29>`__. A much better
interactive console is called `IPython <http://ipython.org/>`__. It is
an "architecture and toolset" for doing interactive computing with
Python. I love IPython. It's terrific for interactively hacking around
and doing analysis with Python. The interface is reminiscent of tools
like Matlab or Mathematica. There's a browser based tool called an
IPython Notebook that, well, let's you use IPython right from a browser
window. The ability to mix runnable Python code with
`markdown <http://daringfireball.net/projects/markdown/>`__ text makes
IPython great for developing tutorials and documenting analysis
workflows. It's a must-have. You can find links to several resources for
learning IPython further down in this document. Both Canopy and Anaconda
have various IPython shells built in.

.. raw:: html

   </p>

Text editors and IDEs for writing Python programs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

While certainly you can just write Python code in a text editor, I like
a good IDE. For Python on Windows, a nice lightweight IDE is
`PyScripter <http://code.google.com/p/pyscripter/>`__. I've also been
using `Spyder <https://code.google.com/p/spyderlib/>`__ on both Windows
and Linux (though it doesn't have a visual debugger, just a command line
debugger). An IDE that looks promising is is the new community edition
of
`PyCharm <http://blog.jetbrains.com/pycharm/2010/01/pycharm-py-is-for-python-charm-is-about-the-ide/>`__
which I just installed a few days ago. I've also been using the editor
built into Canopy. If you search StackOverflow (and Google in general)
for a discussion on Python IDEs, you get a good sense of the landscape.
Lots of folks are quite happy with editors like vim and emacs. Many
editors have syntax highlighting including widely used tools like
`Notepad++ <http://notepad-plus-plus.org/>`__ on Windows and
`gedit <https://wiki.gnome.org/Apps/Gedit/>`__ on Linux. For those used
to `Eclipse as their Java
IDE <http://www.eclipse.org/downloads/moreinfo/java.php#!>`__, there is
a plug-in called `PyDev <http://pydev.org/>`__. However, Eclipse is a
bit of overkill for cranking out beginner Python code. I'd start with
something like PyScripter or PyCharm or Spyder. I'm not sure about the
first two, but Spyder has both IDLE and IPython interactive consoles
embedded in them. Also, get comfortable with IPython Notebooks as they
are really useful for creating your own "tutorials" that contain a
mixture of interactive code and text written in markdown. My Python
tutorials on hselab.org were done this way and there are links to the
actual notebooks hosted on GitHub.

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

5. Collections of links to tutorials
------------------------------------

.. raw:: html

   </p>

`Collection of tutorials links for new Python
programmers <https://wiki.python.org/moin/BeginnersGuide/NonProgrammers>`__
From the official Python.org site.

.. raw:: html

   </p>

`The Best Way to Learn
Python <http://net.tutsplus.com/tutorials/the-best-way-to-learn-python/>`__
Kind of a meta-tutorial that guides you to a bunch of web based
resources for learning Python.

.. raw:: html

   </p>

`Python for Data Analysis: The Landscape of
Tutorials <http://datacommunitydc.org/blog/2013/07/python-for-data-analysis-the-landscape-of-tutorials/>`__
Another nice collection of links to tutorials and resources for learning
Python for doing data analysis.

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

6. General and data science focused Python tutorials and [e]Books
-----------------------------------------------------------------

.. raw:: html

   </p>

`The Official Python Tutorial <http://docs.python.org/2/tutorial/>`__
Straight from the source.

.. raw:: html

   </p>

`Software Carpentry <http://software-carpentry.org/>`__

.. raw:: html

   </p>

This is a fantastic resource aimed at teaching scientists how to be
better software developers. In their words:

.. raw:: html

   </p>

.. raw:: html

   <p>

    We run bootcamps all over the world, and provide open access
    material for self-paced instruction.

    .. raw:: html

       </p>

    .. raw:: html

       <p>

.. raw:: html

   </p>

Their Lessons section has a large number of scientific computing
tutorials which include screencasts and slides. The `Python
section <http://software-carpentry.org/v4/python/>`__ is just one of
many. Other topics include things like version control, the Shell,
regular expressions, databases, and many, many more.

.. raw:: html

   </p>

`Data Science in
Python <http://blog.yhathq.com/posts/data-science-in-python-tutorial.html>`__

.. raw:: html

   </p>

Nice collection of IPython notebooks to provide intro to using Python
for data science work. From `y-hat <http://www.yhathq.com/>`__.

.. raw:: html

   </p>

`Getting Started with Python for Data
Science <https://www.kaggle.com/wiki/GettingStartedWithPythonForDataScience>`__

.. raw:: html

   </p>

This is from the folks at `kaggle.com <https://www.kaggle.com/>`__ who
have turned data mining into a combination of a sport and community
activity.

.. raw:: html

   </p>

`Online Python Tutor <http://www.pythontutor.com/>`__

.. raw:: html

   </p>

Simply amazing web based tool that lets you visualize Python program
execution. You can even use it from within an IPython notebook. And you
can embed and/or share your program visualizations with others - the
Online Python Tutor generates embed code or a URL. Wow.
`learnpython.org <http://www.learnpython.org/>`__ An interactive Python
tutorial.

.. raw:: html

   </p>

`Wikibooks Non-programmers tutorial for
Python <http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6>`__

.. raw:: html

   </p>

Aimed at folks with little to no programming experience.

.. raw:: html

   </p>

`Learn Python the Hard Way <http://learnpythonthehardway.org/book/>`__

.. raw:: html

   </p>

Free HTML "book" with optional videos for purchase.

.. raw:: html

   </p>

`Think Python: How to think like a computer
scientist <http://www.greenteapress.com/thinkpython/thinkpython.html>`__

.. raw:: html

   </p>

Free eBook.

.. raw:: html

   </p>

`Code Academy Python
tutorial <http://www.codecademy.com/tracks/python>`__

.. raw:: html

   </p>

I haven't checked out this tutorial much myself but have had some
students mention that they were using it to learn Python. `Python
books <https://wiki.python.org/moin/PythonBooks>`__ List of Python books
compiled by the Python people.

.. raw:: html

   </p>

`Learning Python
(Lutz) <http://www.amazon.com/Learning-Python-Edition-Mark-Lutz/dp/1449355730>`__

.. raw:: html

   </p>

Nice first book for learning Python.

.. raw:: html

   </p>

`Practical Computing for Biologists <http://practicalcomputing.org/>`__

.. raw:: html

   </p>

Terrific book that covers all kinds of practical ground for becoming a
more effective scientific programmer. They use Python. Someone needs to
write "Practical Computing for Business Analysts".

.. raw:: html

   </p>

`A Primer on Scientific Programming with
Python <http://www.barnesandnoble.com/listing/2686727554569?r=1&cm_mmca2=pla&cm_mmc=GooglePLA-_-TextBook_NotInStock_75Up-_-Q000000633-_-2686727554569>`__

.. raw:: html

   </p>

Hardcover and pricey, but quite good.

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

7. Open access courses
----------------------

.. raw:: html

   </p>

`Udacity - Intro to Computer Science
101 <https://www.udacity.com/course/cs101>`__

.. raw:: html

   </p>

Learn Python while building a search engine

.. raw:: html

   </p>

`Udacity - Intro to Data
Science <https://www.udacity.com/course/ud359>`__

.. raw:: html

   </p>

Assumes basic knowledge of Python and statistics.

.. raw:: html

   </p>

`Coursera - Introduction to Data
Science <https://www.coursera.org/course/datasci>`__

.. raw:: html

   </p>

Not so much a Python course as a data science course that uses Python
among other tools. I really like the design of the course in terms of
topical coverage and the balancing act required in terms of trying to
serve both computing and analytics folks. Parallels between
sci-computing and business analytics computing are nicely covered.

.. raw:: html

   </p>

`MIT - A Gentle Introduction to Programming with
Python <http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-189-a-gentle-introduction-to-programming-using-python-january-iap-2008/>`__

.. raw:: html

   </p>

Part of the MIT Open Courseware initiative

.. raw:: html

   </p>

`Harvard - Intro to Data Science 109 <http://cs109.org/>`__

.. raw:: html

   </p>

Top notch data science course. Python used.

.. raw:: html

   </p>

`Quantitative Economics <http://quant-econ.net/index.html>`__

.. raw:: html

   </p>

A set of lectures on quant econ modeling using Python. Includes info on
getting your sci-computing environment set up.

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

8. Toolbox
----------

.. raw:: html

   </p>

There are a huge number of Python packages and tools for doing
analytical work. I'm just going to mention a few of the biggies. I want
to give a shout out to the very nice compilation of Python data analysis
related tutorial links at `Python for Data Analysis: The Landscape of
Tutorials <http://datacommunitydc.org/blog/2013/07/python-for-data-analysis-the-landscape-of-tutorials/>`__
as I've gotten a number of links from this post.

.. raw:: html

   </p>

`SciPy and numpy and friends <http://www.scipy.org/about.html>`__
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

.. raw:: html

   <p>

    SciPy (pronounced “Sigh Pie”) is a Python-based ecosystem of
    open-source software for mathematics, science, and engineering.
    numpy and SciPy are the bedrock of scientific computing in Python
    providing a powerful n-dimensional array construct as well as core
    scientific computing functionality.

    .. raw:: html

       </p>

    .. raw:: html

       <p>

.. raw:: html

   </p>

-  `SciPy2012
   Conference <http://conference.scipy.org/scipy2012/index.php>`__ - the
   conference for the SciPy world.

.. raw:: html

   </p>

`pandas - Python Data Analysis Library <http://pandas.pydata.org/>`__
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

A must-have library for doing data crunching in Python. Developed by
`Wes McKinney <http://blog.wesmckinney.com/>`__. Pandas includes
DataFrames and Series data structures and all kinds of methods for
working with them. It includes tools for data IO, data prep, data
transformation, data modeling, data analysis, data visualization, and
data presentation. It uses numpy and matplotlib under the hood.

.. raw:: html

   </p>

-  `pandas
   cookbook <http://pandas.pydata.org/pandas-docs/stable/cookbook.html>`__
   - *"This is a respository for short and sweet examples and links for
   useful pandas recipes."*
-  `Wes McKinney's 10 minute pandas overview
   vid <http://vimeo.com/59324550>`__ - get a quick demo from pandas
   founder. Longer tutorials from WM can be found
   `here <http://youtu.be/MxRMXhjXZos>`__ and
   `here <http://youtu.be/w26x-z-BdWQ>`__.
-  `Intro to pandas data
   structures <http://www.gregreda.com/2013/10/26/intro-to-pandas-data-structures/>`__
   - nice introductory tutorial aimed at those coming from the SQL
   world.
-  `Statistical analysis with SciPy and
   pandas <http://www.randalolson.com/2012/08/06/statistical-analysis-made-easy-in-python/>`__
   - an IPython notebook based tutorial on doing stats using Python +
   SciPy + pandas

.. raw:: html

   </p>

`IPython <http://ipython.org/>`__
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

An architecture and toolset for doing interactive computing with Python.
It was developed by `Fernando Perez and
others. <http://blog.fperez.org/2012/01/ipython-notebook-historical.html>`__
I love IPython. It's terrific for interactively hacking around and doing
analysis with Python. The interface is reminiscent of tools like Matlab
or Mathematica. There's a browser based tool called an IPython Notebook
that, well, let's you use IPython right from a browser window. The
ability to mix runnable Python code with
`markdown <http://daringfireball.net/projects/markdown/>`__ text makes
IPython great for developing tutorials and documenting analysis
workflows. It's a must-have.

.. raw:: html

   </p>

-  `Official IPython
   Tutorial <http://ipython.org/ipython-doc/stable/interactive/tutorial.html>`__
   - A very good place to start.
-  `A collection of notebooks for using IPython
   effectively <https://github.com/ipython/ipython/tree/master/examples/notebooks#a-collection-of-notebooks-for-using-ipython-effectively>`__
   - Become an effective IPython user.
-  `IPython Notebook Viewer <http://nbviewer.ipython.org/>`__ -
   *"IPython Notebook Viewer (or nbviewer in short) is a free webservice
   that allows you to see static html versions of hosted notebook files.
   As long as a notebook is publicly available, by giving its url to
   nbviewer you should be able to view it."*
-  `A gallery of interesting IPython
   notebooks <https://github.com/ipython/ipython/wiki/A-gallery-of-interesting-IPython-Notebooks>`__
   - Hosted at github, this is a HUGE, curated collection of notable
   IPython notebooks on many sci-computing related topics. Some are
   companions to books, some are tutorials, some are demonstrations,
   some are...
-  `Learning IPython for interactive computing and
   visualization <http://www.amazon.com/gp/product/1782169938/>`__ - A
   physical book. - You can find a bunch of great videos and slides on
   the development, evolution and how-to use of IPython at
   http://ipython.org/videos.html

.. raw:: html

   </p>

`matplotlib <http://matplotlib.org/>`__
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

Matplotlib is a widely used plotting library. It's very powerful and has
great documentation with tons of examples. It was developed by `John
Hunter <http://numfocus.org/johnhunter.html>`__ who sadly passed away in
2012. Part of Python's rise as a force in the sci-computing world is
certainly due to matplotlib.

.. raw:: html

   </p>

.. raw:: html

   <p>

    matplotlib is a python 2D plotting library which produces
    publication quality figures in a variety of hardcopy formats and
    interactive environments across platforms.

    .. raw:: html

       </p>

    .. raw:: html

       <p>

.. raw:: html

   </p>

matplotlib can be used in python scripts, the python and ipython shell
(ala MATLAB®\* or Mathematica®†), web application servers, and six
graphical user interface toolkits. You can use matplotlib as an
interactive plotting tool (ala Matlab) using its pyplot command or in
more of an API based programmatic way. Here are some good links to
matplotlib tutorials that I pulled directly from `A. Dasgupta's "Python
for Data Analysis: The Landscape of
Tutorials" <http://datacommunitydc.org/blog/2013/07/python-for-data-analysis-the-landscape-of-tutorials/>`__:

.. raw:: html

   </p>

-  `Official matplotlib.pyplot
   tutorial <http://matplotlib.org/users/pyplot_tutorial.html>`__ -
   `N.P. Rougier’s tutorial from EuroSciPy
   2012 <http://www.loria.fr/%7Erougier/teaching/matplotlib/>`__
-  `Jake VanderPlas’ tutorial from PyData NYC
   2012 <http://jakevdp.github.io/mpl_tutorial/>`__
-  `John Hunter’s Advanced Matplotlib Tutorial from PyData
   2012 <http://www.youtube.com/watch?v=DNRJwENqEUY>`__
-  `A tutorial from
   Scigraph <https://sites.google.com/site/scigraphs/tutorial>`__

.. raw:: html

   </p>

`scikit-learn <http://scikit-learn.org/stable/>`__
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

Tools for all kinds of "machine learning" algorithms and tools for
classification, clustering, regression, dimensionality reduction, model
selection and data preprocessing. It's built on top of tools like numpy,
SciPy, and matplotlib.

.. raw:: html

   </p>

`statsmodels <http://statsmodels.sourceforge.net/>`__
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

This is a Python package that contains all kinds of statistical analysis
functionality. It's not as comprehensive as R but but has the advantage
of being part of a general programming language, Python, instead of a
domain specific language like R. Regarding R on the data processing
side, I find myself preferring Python and then using R for the stats.
However, I do also end up doing a fair bit of data prep work in R during
course of an analysis (e.g. output dataframe needing some transforming
or reshaping for next stage of analysis). Having a full-fledged
programming language with strong support for data prep (including regex)
is really nice. I also find myself doing more and more statistical work
in Python, especially when I'm embedding some kind of statistical model
in some sort of analytical application or tool. Bottom line, it's worth
knowing both for both data handling and stats. The R and Python+(various
goodies) worlds are colliding:

.. raw:: html

   </p>

-  Using R from Python is pretty easy via
   `Rpy2 <http://rpy.sourceforge.net/rpy2.html>`__
-  Go the other direction with
   `rPython <http://rpython.r-forge.r-project.org/>`__
-  Closed but `good discussion on stackehange on R vs Python for data
   analysis <http://programmers.stackexchange.com/questions/181342/r-vs-python-for-data-analysis>`__
-  ggplot2 (R) is usually considered somewhat better than matplotlib
   (mainly due to "grammar of graphics" foundation of ggplot2) but
   `y-hat released ggplot -like plotting engine for
   Python <http://blog.yhathq.com/posts/ggplot-for-python.html>`__.
-  pandas and statsmodels are Python packages that are terrific for
   stats and data analysis

.. raw:: html

   </p>

`Sphinx <http://sphinx-doc.org/>`__
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

Sphinx is a
`reStructuredText <http://docutils.sourceforge.net/rst.html>`__ based
documentation generation system for Python. It makes writing
documentation fun.

.. raw:: html

   </p>

.. raw:: html

   <p>

    Sphinx is a tool that makes it easy to create intelligent and
    beautiful documentation, ...

    .. raw:: html

       </p>

    .. raw:: html

       <p>

.. raw:: html

   </p>

reStructuredText is an easy-to-read, `what-you-see-is-what-you-get
plaintext markup syntax and parser system <http://xkcd.com/1341/>`__.
reST is part of
`docutils <http://docutils.sourceforge.net/index.html>`__, an open
source text processing system that takes documentation written in plain
text and converts it to useful formats like HTML, pdf, LaTex, and
others. The official Python documentation is written in reST and reST is
used for `docstrings <http://www.python.org/dev/peps/pep-0257/>`__ in
Python code. Docstrings are just literal string comments included in
source code that can be read, parsed, and used to automatically generate
documentation. When you write docstrings, you write them in reST. Once
you get used to it, you'll wonder how you ever did without it. While
Sphinx and reST are ubiquitous in the Python doc world, you can use them
for general documentation and writing. I wrote documentation for a Java
based computer simulation model using Sphinx and reST. I generated HTML
but could have generated other output formats as well. Best of all, you
just write the documentation in a text editor (many of which are reST
aware). It's genius.

.. raw:: html

   </p>

`PyTables <http://pytables.github.io/>`__
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. raw:: html

   </p>

Built on top of `HDF5 - Hierarchical Data
Format <http://www.h5py.org/>`__, PyTables provides tools for working
with large datasets in Python. > PyTables is a package for managing
hierarchical datasets and designed to efficiently and easily cope with
extremely large amounts of data.

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

9. Musings on Python, open source software and reproducible analysis
--------------------------------------------------------------------

.. raw:: html

   </p>

`NumFocus: Open Code, Better Science <http://numfocus.org/about.html>`__

.. raw:: html

   </p>

A non-profit foundation dedicated to supporting better sci-computing.

.. raw:: html

   </p>

.. raw:: html

   <p>

    Mission: to promote accessible and reproducible computing in science
    and technology.

    .. raw:: html

       </p>

    .. raw:: html

       <p>

.. raw:: html

   </p>

`Fernando Perez's blog on open and literate scientific
programming <http://blog.fperez.org/2013/04/literate-computing-and-computational.html>`__

.. raw:: html

   </p>

The developer of IPython writes eloquently about these topics.

.. raw:: html

   </p>

`Living in an Ivory
Basement <http://ivory.idyll.org/blog/category/python.html>`__

.. raw:: html

   </p>

C. Titus Brown is a computational biologist at Michigan State
University. He's got a great blog on scientific computing with lots of
Python thrown in.

.. raw:: html

   </p>

`Wes McKinney <http://blog.wesmckinney.com/>`__

.. raw:: html

   </p>

The pandas developer who has recently launched a `new data analytics
venture <http://www.datapad.io/>`__.

.. raw:: html

   </p>

`yhat <http://blog.yhathq.com/>`__ (pronounced "why hat")

.. raw:: html

   </p>

This is a company focused on providing a cloud platform for analytics.
They create interesting tools with and write interesting things about
Python and R.

.. raw:: html

   </p>

`Software Carpentry
Blog <http://software-carpentry.org/blog/index.html#recent-posts>`__

.. raw:: html

   </p>

`Pythonic Perambulations <http://jakevdp.github.io/>`__

.. raw:: html

   </p>

`10 reasons Python rocks for
research <http://www.stat.washington.edu/~hoytak/blog/whypython.html>`__

.. raw:: html

   </p>

`Victoria Stodden's bloggings on reproducible
research <http://blog.stodden.net/category/reproducible-research/>`__

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

10. General Python resources
----------------------------

.. raw:: html

   </p>

`Official Python site <http://www.python.org/>`__

.. raw:: html

   </p>

`PyPI - the Python Package Index <https://pypi.python.org/pypi>`__

.. raw:: html

   </p>

The Python Package Index is a repository of software for the Python
programming language. It's the
`CRAN <http://cran.us.r-project.org/index.html>`__ of Python world.

.. raw:: html

   </p>

`pyvideo.org <http://pyvideo.org/>`__

.. raw:: html

   </p>

Index for Python related videos

.. raw:: html

   </p>

`StackOverflow <http://stackoverflow.com/>`__

.. raw:: html

   </p>

StackOverflow is your friend. It's a very good Q&A site for all things
programmatical. You can learn a lot just by browsing threads of
interest. It's the first place I go to when trying to figure out some
Pythonic thing. It uses tags to help you find things.

.. raw:: html

   </p>

.. raw:: html

   <p>

    Stack Overflow is a question and answer site for professional and
    enthusiast programmers. It's 100% free, no registration required.

    .. raw:: html

       </p>

    .. raw:: html

       <p>

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top">

`Back to top <#top>`__

.. raw:: html

   </div>

11. The Python packaging ecosystem
----------------------------------

.. raw:: html

   </p>

This is not a beginner topic but you'll have to deal with it eventually.
The following two articles will lead you into the morass.

.. raw:: html

   </p>

`A non-magical introduction to Pip and Virtualenv for Python
beginners <http://dabapps.com/blog/introduction-to-pip-and-virtualenv-python/>`__

.. raw:: html

   </p>

`Python Packaging: Hate, hate, hate
everywhere <http://lucumr.pocoo.org/2012/6/22/hate-hate-hate-everywhere/>`__

.. raw:: html

   </p>

.. raw:: html

   <div class="toc-filter-back-to-top last">

`Back to top <#top>`__

.. raw:: html

   </div>

.. raw:: html

   </div>

.. raw:: html

   </div>

.. raw:: html

   </div>

.. raw:: html

   <div
   class="field field-name-field-tags field-type-taxonomy-term-reference field-label-above">

.. raw:: html

   <div class="field-label">

Tags: 

.. raw:: html

   </div>

.. raw:: html

   <div class="field-items">

.. raw:: html

   <div class="field-item even" rel="dc:subject">

`python </taxonomy/term/1>`__

.. raw:: html

   </div>

.. raw:: html

   <div class="field-item odd" rel="dc:subject">

`business analytics </taxonomy/term/8>`__

.. raw:: html

   </div>

.. raw:: html

   </div>

.. raw:: html

   </div>

.. raw:: html

   <div
   class="field field-name-field-article-type field-type-taxonomy-term-reference field-label-hidden">

.. raw:: html

   <div class="field-items">

.. raw:: html

   <div class="field-item even">

`tutorial </article-type/tutorial>`__

.. raw:: html

   </div>

.. raw:: html

   </div>

.. raw:: html

   </div>

.. raw:: html

   </p>

