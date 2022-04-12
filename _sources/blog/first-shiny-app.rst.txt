.. post:: Nov 30, 2014
   :tags: R, shiny, teaching, statistics
   :author: misken
   :exclude:
   
   Plotting rejection regions for hypothesis tests using R Shiny

First R Shiny app: Rejection region plots for hypothesis tests
===============================================================

This is my first RStudio Shiny application. I wanted to learn `Shiny, a way to make R based interactive web based apps <http://www.rstudio.com/shiny/>`__, and at the same time produce something at least a little useful. While creating a solution guide for a hypothesis testing assignment I had assigned in my statistics class, I realized it was a pain to create little plots showing rejection regions for two sample tests on the mean (based either on Z or t distribution). Hmm, seemed like a good candidate for a Shiny app. The user can specify the distribution, the significance level, which tails to show, and (eventually) some style related things like colors. The resulting plot can be downloaded to a PNG file. I then inserted the file into my homework solution guide. While there isn't a whole lot of code needed for this app, there were numerous "gotchas" and much trial and error. I am super grateful to the folks at the `Scenarios Network for Alaska & Arctic Planning <http://www.snap.uaf.edu/>`__ who have created numerous `Shiny applications and tutorials and have shared them via their blog <http://blog.snap.uaf.edu/>`__. I learned much from their examples and "borrowed" many ideas from their series of `introductory tutorials on plotting random variable distributions <http://blog.snap.uaf.edu/2013/05/20/introducing-r-shiny-web-apps/>`__ . Hopefully this is the first of many Shiny apps for me. This post is not a Shiny tutorial. If you have no experience with Shiny, start at http://shiny.rstudio.com/tutorial/.

I deployed the app on `ShinyApps.io by RStudio <http://www.shinyapps.io/>`__, a site for hosting Shiny Apps (free and paid plans). You can check it out
at `http://hselab.shinyapps.io/critvalues <http://hselab.shinyapps.io/critvalues>`__.

You can get the source code at my `github repo for R Shiny apps <https://github.com/misken/hselab-shiny-apps/tree/master/critvalues>`__.
The source code is pretty heavily commented and includes the various trials and tribulations I had in getting this to work.

Here's what the app looks like.

    .. figure:: images/hselab-shiny-apps-critvalues.png
       :target: http://hselab.shinyapps.io/critvalues

       Screenshot from my Shiny app. Check out the real thing at `http://hselab.shinyapps.io/critvalues <http://hselab.shinyapps.io/critvalues>`__
