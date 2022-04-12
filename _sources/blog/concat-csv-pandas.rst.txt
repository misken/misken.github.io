.. post:: Mar 09, 2016
   :tags: python, pandas, text
   :author: misken
   :exclude:
   
   Concatenating csv files using pandas

Concatenating csv files using pandas
======================================

As part of a research project on hospital capacity planning, I ended up
running many computer simulations. For example, there were 150 different
scenarios, each requiring 25 runs (replications) of the simulation model. Each
run generated a log file that was subsequently processed by a Python script. Much
of this post-processing took place in parallel threads with a subset of the
scenarios allocated to each thread. After all that, I ended up with a
subdirectory containing a number of csv files with identical structure that
needed to be combined into one big csv file. Here's a little bit of one of
the files.

::

  scenario,rep,timestamp,num_days,num_visits_obs,num_visits_ldr,num_visits_pp, ...
  30,1,2016-03-04 12:44:29.610563,105553,42150.0,42154.0,42159.0,8409.0, ...
  30,10,2016-03-04 12:48:00.519651,105553,42288.0,42296.0,42305.0,8500.0, ...
  30,11,2016-03-04 12:51:30.571655,105553,42210.0,42209.0,42227.0,8387.0, ...
  30,12,2016-03-04 12:55:08.550450,105553,42420.0,42433.0,42457.0,8341.0, ...
  30,13,2016-03-04 12:58:48.635709,105553,42277.0,42289.0,42301.0,8429.0, ...
  30,14,2016-03-04 13:02:21.325709,105553,42127.0,42135.0,42150.0,8581.0, ...
  ... many more rows and columns


I also wanted to make sure that the final combined file was sorted in
ascending order by scenario by replication. Even though I only had a handful
of files, manually doing the concatenation using Excel and copying and pasting
got old quickly. Also, I often face this same problem but have hundreds of csv
files to concatenate. Seemed like a good excuse to put together a Python script
to address this problem.

Example
-------

Here is a directory listing of the files to be concatenated.

::

  ~/exp9/results_csvs$ ls
  results_Exp9_Tandem05_nodischadj_100.csv  results_Exp9_Tandem05_nodischadj_3_5.csv
  results_Exp9_Tandem05_nodischadj_1_2.csv  results_Exp9_Tandem05_nodischadj_6_9.csv

The only tricky thing about creating the following Python script was making
sure that it worked both on Windows and Linux systems. The backslash vs
forward slash issue in file paths can cause grief.

.. code-block:: python

  import pandas as pd
  import glob
  import os

  # Inputs
  path = './results_csvs/'
  stub = 'results_Exp9_Tandem05_nodischadj'
  fnpattern = stub + '_*.csv'
  sortkeys = ['scenario','rep']

  # Create filename pattern to glob that includes the path
  # Try to make sure path works in both Windows and Linux

  fnpattern_wpath = os.path.normpath(os.path.join(path, fnpattern))

  # Create empty dict to hold the DataFrames created as we read each csv file
  dfs = {}

  # Loop over all the csv files matching our pattern
  for csv_fn in glob.glob(fnpattern_wpath):
      # Split the filename off from csv extension. We'll use the filename
      # (without the extension) as the key in the dfs dict.
      fnstub, ext = csv_fn.split('.')

      # Read the next csv file into a pandas DataFrame and add it to
      # the dfs dict.
      df = pd.read_csv(csv_fn)
      dfs[fnstub] = df

  # Use pandas concat method to combine the file specific DataFrames into
  # one big DataFrame.
  bigdf = pd.concat(dfs)

  # Since we didn't try to control the order in which the files were read,
  # we'll sort the final DataFrame in place by the specified sort keys.
  bigdf.sort_values(sortkeys, inplace=True)

  # Export the final DataFrame to a csv file. Suppress the pandas index.
  bigdf.to_csv(stub + '.csv', index=False)
