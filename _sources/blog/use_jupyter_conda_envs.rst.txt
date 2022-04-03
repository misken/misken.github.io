.. post:: Apr 3, 2022
   :tags: jupyter, conda
   :author: misken
   
   Run Jupyter lab from base and toggle between conda envs


Using different conda environments with Jupyter Lab
====================================================

This has been a source of confusion for me over the years. Previously, 
I had been installing ``jupyter`` and ``jupyter-lab`` into each of my 
conda virtual envs. However, there is really no need to do this and 
after digging through many blog and StackOverflow posts (links at 
bottom), I've settled on the following procedure. The tl;dr version
is:

* create conda env that includes ``ipykernel`` but does not include ``jupyter`` and/or ``jupyter-lab``,
* conda install ``nb_conda_kernels`` into base conda environment,
* always launch Jupyter Lab from base conda environment,
* switch kernel to desired conda virtual env from inside of Jupyter.

Create conda virtual env for analytics
----------------------------------------

Here's my YAML file. **IMPORTANT** - notice that we are NOT installing
``jupyter`` and/or ``jupyter-lab`` in our new conda virtual env. Instead,
we are installing ``ipykernel`` which will then allow 
Jupyter (run from base env) to automatically "see" this kernel 
associated with the analytics virtual env
and allow us to switch our notebook to this kernel.

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
      - sphinx
      - cookiecutter
      - pyyaml
      - pytest
      - pip
      
Create the virtual env with:

.. code-block:: console

    conda env create -f analytics.yml
    
Install ``nb_conda_kernels`` in base environment
-------------------------------------------------

In order for Jupyter to see any kernels associated with conda environments,
we need to install ``nb_conda_kernels`` in our base environment. As 
described `here in the conda docs <https://docs.anaconda.com/anaconda/user-guide/tasks/use-jupyter-notebook-extensions/>`_, by installing ``nb_conda_kernels``
a few other Jupyter extensions also get installed, including ``nb_conda``.
The ``nb_conda`` extension is NOT the same as ``nb_conda_kernels`` and
appears to provide a conda navigator like tab in Jupyter.

.. code-block:: console

   conda install nb_conda_kernels
   
Run Jupyter Lab from base environment
--------------------------------------

Always run Jupyter Lab from base environment. We don't even have
Jupyter Lab installed in the analytics virtual environment. Once 
Jupyter is running, the kernel can be set to any one of the kernels
associated with your conda virtual envs. You can do this from the
Kernel menu or from the upper right corner of the window.

Resources
----------

I settled on this procedure after reading numerous blog posts and
SO posts. Some of the most helpful are:

* `Get Your Conda Environment to Show in Jupyter Notebooks — the “Easy Way” <https://towardsdatascience.com/get-your-conda-environment-to-show-in-jupyter-notebooks-the-easy-way-17010b76e874>`_
* `How to use Jupyter notebooks in a conda environment? <https://stackoverflow.com/questions/58068818/how-to-use-jupyter-notebooks-in-a-conda-environment>`_
* `Using Jupyter Notebook Extensions <https://docs.anaconda.com/anaconda/user-guide/tasks/use-jupyter-notebook-extensions/>`_
* `How to Setup Anaconda and Jupyter Notebook the Right Way <https://towardsdatascience.com/how-to-set-up-anaconda-and-jupyter-notebook-the-right-way-de3b7623ea4a>`_
