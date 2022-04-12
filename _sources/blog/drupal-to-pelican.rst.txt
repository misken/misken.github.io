.. post:: Nov 28, 2014
   :tags: python, blogging
   :author: misken
   :exclude:
   
   Static blogging with Pelican

Goodbye Drupal: static-blogging with Pelican
============================================

I gave Drupal the old college try for a few years with this blog. Ultimately,
I found myself spending too much time tinkering with the beast that is
Drupal than creating content. At the same time, working with Python and R
reminded me of the beauty of the simple text file and lightweight markdown
languages like Markdown and reStructuredText. So, when I started to hear
about static blogs and tools like `Jekyll <http://jekyllrb.com/>`__ and `Pelican <http://docs.getpelican.com/en/3.5.0/>`__, I was intrigued.



One of my `favorite computational science blogs <http://ivory.idyll.org/blog/>`__ has
the following footer:

    Proudly powered by pelican, which uses python.

Hmm, let's take a look at this Pelican. Lots of Googling led to a
bunch of `useful links about static-blogging with Pelican <https://delicious.com/isken/pelican>`__. 

Why Pelican
-----------

In this post, I'm not going to try to duplicate other "how to blog with Pelican"
posts. Instead I'm just going to highlight the reasons for moving this blog to 
Pelican and describe a few challenges and solutions to my specific problem
of porting Drupal content containing a mish mash of text, images, R Markdown
generated HTML and IPython notebooks. Some of the information on porting from
Drupal to Pelican won't make much sense until you understand how Pelican works.

The main reasons I decided to move from Drupal to Pelican:

- My blog would consist essentially of a bunch of text files and images.
 
  - No database
  - easy to version, backup and move around
  - easy to edit
- I could author posts in `reStructuredText <http://docutils.sourceforge.net/rst.html>`__ or `Markdown <http://daringfireball.net/projects/markdown/syntax?>`__.
- Pelican made it easy to edit and test locally with a simple webserver
- Publishing is just pushing the changed files up to my web host
- Pelican is Python powered and I like Python and want to support it. Jekyll is Ruby based.
- No more Drupal core updates and module updates
- No more messing around with text filters and related modules and how they play with CKEditor.
- Less security concerns since my site is just static content

Porting content from Drupal to Pelican
--------------------------------------

All content in Drupal is stored in a MySQL database. There are various modules designed for getting
`content out of Drupal for migration to other versions of Drupal <https://www.drupal.org/project/backup_migrate>`__.
It's also possible to write SQL to pull things directly out of the database - given that you can `figure out which of the hundred or so tables contains what you want <http://drupal.stackexchange.com/questions/6787/where-does-drupal-store-the-content-of-a-nodes-body>`__.
For example, by default, the body of a post is in the `body_value` field of the `field_data_body` table. Images live somewhere else.
I ended up trying one of Pelican's built in utilities for importing blog content from places like Wordpress. In fact, I had another
site that was a Wordpress site and porting it was as simple as using Wordpress' export to XML feature and Pelican's utility for
importing XML files from Wordpress. A little manual cleanup and that site was ported. Not so easy for Drupal sites. 

I ended up
using `Pelicans ability to import content from an RSS or Atom feed <http://pelican.readthedocs.org/en/3.5.0/importer.html>`__. The result
was one `.rst` file per post. Some of these just required minor cleanup in a text editor and they were ready to go. Here's what one
such post looks like - it's a reSt file ready for Pelican.

  ::
  
	    xkcd on the Monty Hall problem
	    ##############################
	    :date: 2013-10-30 01:38
	    :author: mark
	    :tags: probability, teaching, xkcd
	    :slug: xkcd-on-the-monty-hall-problem

	    Every year we do the Monty Hall problem in my classes in some form or
	    another. Leave it to `xkcd to give the definitive answer to this
	    paradox <http://xkcd.com/1282/>`__.


Others were hideous messes of raw html living in reSt `raw` blocks.
For some of these files, I decided to use the original HTML file and create a reSt file that was simply a wrapper for it. For example, here's the
directory structure for the content in my Pelican site. Note the `literalhtml` folder.

  ::
  
	  .
	├── create-sequence-ggplots-topdf.rst
	├── ... BLAH BLAH more rst files
	├── learning-python-suggestions-and-resources-for-business-analytics-students-and-professionals.rst
	├── literalhtml
	│   ├── hillpy_bydate_demo.html
	│   ├── hillpy_occstats_demo.html
	│   ├── ORSchedLeadTime_Python.html
	│   └── ORSchedLeadTime_R.html
	├── pages
	│   ├── about.rst
	│   ├── ... BLAH BLAH more rst files
	│   └── projects.rst


and here's the entire contents of the reSt file for one of the posts that uses one of the HTML files:

   ::
   
	    Occupancy analysis with Python + pandas - Part 1: Create "by date" data frame
	    #############################################################################
	    :date: 2013-03-25 21:38:33
	    :author: mark
	    :tags: python, occupancy-analysis, pandas
	    :slug: occupancy-analysis-with-python-pandas-part-1-create-by-date-data-frame


	    .. raw:: html
	       :file: literalhtml/hillpy_bydate_demo.html

For the above approach to work, you also have to tell Pelican to treat the file in the `literalhtml` folder
as literal content that should not be processed. To do this, I added the following two lines to my
`pelicanconf.py` configuration file.

    ::
    
        ARTICLE_EXCLUDES = ['literalhtml']
        PAGE_EXCLUDES = ['literalhtml']



Several of my posts were creating using R Studio and consisted of HTML generated from R Markdown source files
using `knitr <http://yihui.name/knitr/>`__. Several of these posts contained images (e.g. ggplot2 graphs). For these,
I decided to go back to the original R Markdown files, regenerate the HTML using `knitr` and then publish them to
`RPubs <https://rpubs.com/>`__, a free hosting service provided by `RStudio <http://www.rstudio.com/>`__. Then I just reworked the post to contain
the first few paragraphs and then a link to the RPubs hosted content. This is similar to some of the Python related posts
in which the IPython notebook content is displayed on the `nbviewer <http://nbviewer.ipython.org/>`__ site. Here's one of the
posts which makes use of RPubs:

    :: 
    
	    Create sequence of ggplots and send to pdf
	    #########################################################
	    :date: 03/22/2013 - 09:17
	    :author: mark
	    :tags: R, ggplot2
	    :slug: sequence-ggplot-to-pdf


	    See my previously posted tutorial `Getting started with R (with plyr and ggplot2) 
	    for group by analysis <http://hselab.org/getting-started-R-group-by.html>`__. 
	    At the end of that tutorial we did some facet plots to show a bunch of histograms. 
	    What if we wanted to do a sequence of plots instead and save each of them to separate PDFs?

	    Check out my approach at `http://rpubs.com/misken/sequence-ggplots-topdf <http://rpubs.com/misken/sequence-ggplots-topdf>`__.

Themes
------

One thing about Drupal, there are a jillion themes available. Obviously, there are far fewer available for Pelican (or similar
static blogging tools). Nevertheless, there are `plenty of good themes <https://github.com/getpelican/pelican-themes>`__
and it's not difficult to create your own. I quickly settled on `Bootstrap 3 for Pelican <https://github.com/DandyDev/pelican-bootstrap3>`__ 
since my Drupal site was using Bootstrap and Bootstrap 3 for Pelican had all kinds of goodies for customizing your site (including
all the free themes from `http://bootswatch.com/ <http://bootswatch.com/>`__). 

So, hopefully I'll blog more now and spend less time fighting with my blogging platform.
