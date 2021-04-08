# Getting started with Jupyter, conda, Python (relevant scientific packages) and Git/GitHub

We'll point to tutorials and documentation created for [OceanHackWeek (OHW) 2020](https://oceanhackweek.github.io) at the [OHW Resources site](https://oceanhackweek.github.io/ohw-resources/). When reading these materials, ignore references to JupyterHub or "the Hub". That's a cloud-based deployment of Jupyter. For now, we'll be working only on Jupyter in your own computer ("locally").


## Git/GitHub, Jupyter and relevant Python packages

- Git and GitHub: See the OHW [Git](https://oceanhackweek.github.io/ohw-resources/prep/git/) pages, and the OHW [Git and GitHub pre-hackweek tutorial](https://oceanhackweek.github.io/ohw-resources/schedule/#thursday-august-6) (slides and video recording are available).
- Jupyter: See the WaterHackWeek section on [Jupyter notebooks and the Jupyter ecosystem](https://waterhackweek.github.io/learning-resources/prep/jupyterhub/#jupyter-notebooks-and-the-jupyter-ecosystem) and recommended [References and Resources](https://waterhackweek.github.io/learning-resources/prep/jupyterhub/#references-and-resources) at the end of that page. See also the OHW 20 [Jupyter and Scientific Python basics pre-hackweek tutorial materials](https://oceanhackweek.github.io/ohw-resources/schedule/#friday-august-7)
- [Setup Your Earth Analytics Python (conda), Git, Bash Environment On Your Computer Setup earth analytics environment Workshop | Earth Data Science - Earth Lab](https://www.earthdatascience.org/workshops/setup-earth-analytics-python/)
- Scientific Python: See the OHW [Jupyter and Scientific Python basics pre-hackweek tutorial materials](https://oceanhackweek.github.io/ohw-resources/schedule/#friday-august-7). Then see the OHW [Xarray tutorial](https://oceanhackweek.github.io/ohw-resources/schedule/#monday-august-10).
- See  [Introduction to Jupyter For Python | Earth Data Science - Earth Lab](https://www.earthdatascience.org/courses/intro-to-earth-data-science/open-reproducible-science/jupyter-python/). More broadly, you can check out the [Introduction to Earth Data Science | Earth Data Science - Earth Lab](https://www.earthdatascience.org/courses/intro-to-earth-data-science/)

## conda

Go through these instructions. You may also find these materials very helpful: [Set Up Your Conda Earth Analytics Python Environment Setup earth analytics environment | Earth Data Science - Earth Lab](https://www.earthdatascience.org/workshops/setup-earth-analytics-python/setup-python-conda-earth-analytics-environment/)

### Installation (installing Python on Windows through conda)

We'll install Python (3.8) via the [conda](https://conda.io) "open source package management system and environment management system". The advantages of conda include:

- Doesn't require administrative privileges (though I believe you do have admin rights)
- Can be installed side by side with other Python installations w/o interfering with them
- Allows you to easily create "virtual environments" with custom Python installations

conda can be installed in one of two ways, either with "Anaconda" or "Miniconda". We'll use Miniconda, which is much lighter weight than Anaconda, for your own personal use, you may find Anaconda more user friendly. Go to https://docs.conda.io/en/latest/miniconda.html
Download the Windows Python 3.8 installer; I don't know whether you'd use the 32bit or 64 bit one. I did my Windows testing on the 64bit version. If your computer is not too old, I suspect it'll be 64bit; but pick the one that's right for your computer.

Installation instructions for Windows are [here](https://conda.io/projects/conda/en/latest/user-guide/install/index.html). You can find MacOS instructions [here](https://conda.io/projects/conda/en/latest/user-guide/install/index.html), but the process should be pretty similar as on Windows (except that you can do it via the command line, I think).

Assuming you're on Windows 10:

- After downloading the miniconda .exe file, double-click on it
- Select the option to install for the local user only
- Accept the default installation path. I assume it'll be something like C:\Users\<USERNAME>\miniconda3
- On the Advanced Installation Options window, uncheck both boxes ("Add Miniconda3 ..." and "Register Miniconda3 ...")
- On the "Completing Miniconda3" window, you can do whatever you want (check or uncheck the boxes). If you have no preference, uncheck both boxes.

When installation is finished, from the Start menu, open the Anaconda Prompt or Anaconda Powershell Prompt; the latter will probably be nicer. Test it by running the command "conda list"

### Create conda environment and install JupyterLab

You'll need to create a conda "environment" (a Python virtual environment) as needed, customized to the specific need. See [this link for complete documentation](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html), though it's not needed here.

Install JupyterLab through a dedicated conda environment; see the User Guide section at https://jupyterlab.readthedocs.io. To install it, open the command shell (see #1 below) then create a new "jupyterlab3" conda environment as follows:
```bash
conda create -n jupyterlab3 -c conda-forge jupyterlab=3 nb_conda_kernels
```

conda environments can be specified and created using a text file called a conda environment file that lists the specific packages and versions that will be used. The environment file is constructed using the yaml format. To create the environment with such a file:

1. Open the command shell (Anaconda Prompt or Anaconda Powershell Prompt, in my previous instructions).
2. cd (change directory) to where the conda environment `environment.yml` file is located. For example: `cd C:\Users\user1\fhloo`
3. Create conda environment, assigned the name specified in the file (assume it's MYENV):  `conda env create -f environment.yml`
4. "Activate" the environment to start using it:  `conda activate MYENV`
