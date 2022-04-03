.. post:: Sep 15, 2020
   :tags: python,sphinx
   :author: misken
   
   Create course websites with Sphinx.
   
Building coursewebs with Sphinx
================================

At my institution we use `Moodle <https://moodle.org/>`_ as our LMS (Learning Management System). I'm a longtime Moodle user and am quite happy with it. However, I'm also a big proponent of open educational resources and this is where Moodle (or any LMS) can present a challenge. I definitely want all of the interactions and activities between me and my students such as quizzes, forums, and assignments, to be behind the secure Moodle wall. However, for much of my course content (in the form of explanatory text, screencasts and a menagerie of files), I want a publicly accessible course website to facilitate sharing of curricular materials. In the past, I have experimented with running my own instance of Moodle (hosted on this hselab.org site) that had open guest access, but found it to be a pain to maintain. I didn't want to have to worry about Moodle upgrades, security issues, and the fact that the material within this Moodle still wasn't that easily findable or accessible. That suggested that creating my own `static courseweb <https://dev.to/gtanyware/what-is-a-static-website-4k3o>`_ might be the way to go. For this to work, I wanted a few things:

* easy to create and edit pages using a text editor,
* easy to create a well structured website with built in navigation and search,
* easy to update and publish,
* free and open source.

As a regular Python user (and documentation reader) and `pelican <https://docs.getpelican.com/en/stable/>`_ blogger, I was already familiar with `Sphinx <https://www.sphinx-doc.org/en/master/>`_ and `restructured text <https://docutils.sourceforge.io/rst.html>`_. As I had seen in the `Sphinx docs examples page <https://www.sphinx-doc.org/en/master/examples.html>`_, people use Sphinx for all kinds of things beyond just writing documentation. It clearly hits all the items I listed above. 

Creating the sites
-------------------

I just followed the `Sphinx Getting Started tutorial <https://www.sphinx-doc.org/en/master/usage/quickstart.html>`_ to create my skeleton sites
and then created content pages in a text editor (Geany on Linux, Notepad++ on Windows).

Sphinx makes it easy to create a structured and hierarchical site. Here's what my
*index.rst* file looks like for one of my courses, `Practical Computing for Data Analytics <http://www.sba.oakland.edu/faculty/isken/courses/mis5470_f20/index.html>`_:

.. code-block:: rest

    .. toctree::
       :maxdepth: 2
       :caption: Course outline:

       course_logistics
       foundation
       data_science_r
       data_science_python
       additional_topics

and here's what one of the section level table of contents files (*data_science_r.rst*) looks like:

.. code-block:: rest

    .. toctree::
       :maxdepth: 1
       :caption: Intro to data science with R

       r_intro
       git_intro
       eda_r
       data_wrangling_r
       modeling1_mlr_r
       modeling2_class_r


You can view the source of any page. Here's the `eda_r.rst page <http://www.sba.oakland.edu/faculty/isken/courses/mis5470_f20/_sources/eda_r.rst.txt>`_.

You can find links to my complete course websites for the past few years at `my teaching page <http://www.sba.oakland.edu/faculty/isken/pages/teaching.html>`_.

Version control
---------------

Since the coursewebs are just a bunch of text files and images, it's easy to put them under version control with git. Each course gets its own GitHub repo. For now, these are private repos but I'll be
creating a public one as soon as I get some housekeeping done on it.


Hosting and publishing
----------------------

Since these coursewebs are just static websites (basically a bunch of html, css, images, and client-side JavaScript files), they can be uploaded to any web server. The whole publishing process boils down to 

* running ``make html`` to generate the static pages using Sphinx
* uploading the resulting ``html`` folder contents (including subfolders) to the desired folder on your web server.

Since Sphinx is cross-platform, I've used this same approach with Linux and Windows. I just write simple bash scripts or Windows batch files to do the file coping to the server. I use the Anaconda Python distribution on all of my machines.


But I thought Sphinx was for writing documentation
--------------------------------------------------

It is, but it works quite nicely for things like course websites. Restructured text is easy to learn , quite powerful and extendable via `directives <https://docutils.sourceforge.io/docs/user/rst/quickref.html#directives>`_. You get niceties like navigation and site search with very little effort. It all just works. You can change the way things look through `Sphinx themes <https://sphinx-themes.org/>`_.

Some advantages from a teaching perspective
-------------------------------------------

The biggest advantage to me is that it is super easy to make changes to my courseweb. Edits are done using any text editor and the publish and post process is quick and easy. Making large scale changes in LMS GUI editors can be painful.

Porting courses from one semester to the next is as easy as cloning the desired GitHub repo and modifying things for the next semester (creating a new remote repo for the new course).

As mentioned at the start of this post, using something like Sphinx makes it very easy to share my course materials with a wide audience. One specific use case is for when I teach multiple sections of the same course. Each section has its own "course" in our LMS, but both can share the content via my public Sphinx based coursewebs. Anything that is specific to a certain section of the course goes into that course's Moodle page. The only stuff that goes in the public coursewebs is content that I want to share with anyone.

Another common sharing scenario is when we get students expressing interest in our business analytics courses. I can direct them to my course websites and tell them they can see exactly what is covered and how it's done. This is quite helpful for them when making decisions about courses and programs of study.

Students (and their friends and co-workers) can use the sites long after they've graduated. In this way, the coursewebs act not only as a resource but as a marketing / advertising tool for our courses.

Other faculty can easily use content or ideas from my coursewebs. They are licensed under an `MIT License <https://opensource.org/licenses/MIT>`_.

The only real "cost" is that students have to deal with two different websites:

* the LMS for quizzes, assignments, forums and other stuff that needs to be behind the LMS wall
* the public courseweb with almost all of the course content

I've been using this approach for about five years and have had no complaints. Both sites are well structured and I teach analytics - students can handle two websites.



