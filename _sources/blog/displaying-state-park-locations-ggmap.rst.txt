.. post:: Jul 01, 2014
   :tags: R, ggmap, gis, xml
   :author: misken
   :exclude:
   
   Getting started with ggmap and XML

Displaying Michigan state park locations: A "getting started with ggmap (and XML)" project
===========================================================================================

For quite a while I've been wanting to explore the mapping and spatial analysis capabilities of R.
Maps are cool and R is cool, so maps + R should be awesome. I've dabbled here and there but thought
I'd try to do a few simple projects to start to build some familiarity with this topic.

In this first "Hello World" level project, I decided to show the location and approximate size of all of state parks in the Michigan State Park system. The Michigan DNR hosts data about the state parks in Michigan at [http://www.michigandnr.com/parksandtrails/](http://www.michigandnr.com/parksandtrails/). Detailed data is available for download as a series of "simple" XML files. So, as a byproduct, I'll also show how I dealt with getting
data from an XML file into an R data frame.

Check out my approach at `http://rpubs.com/misken/state-parks-ggmap-xml <http://rpubs.com/misken/state-parks-ggmap-xml>`__.
