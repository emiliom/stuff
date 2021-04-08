## Install conda

Here are the instructions for installing Python on Windows. I tested them on my wife's Windows 10 laptop.

We'll install Python (3.8) via the *conda* "open source package management system and environment management system" (https://conda.io). The advantages of conda include:

- Doesn't require administrative privileges (though I believe you do have admin rights)
- Can be installed side by side with other Python installations w/o interfering with them
- Allows you to easily create "virtual environments" with custom Python installations

conda can be installed in one of two ways, either with "Anaconda" or "Miniconda". We'll use Miniconda, which is much lighter weight than Anaconda, for your own personal use, you may find Anaconda more user friendly. Go to https://docs.conda.io/en/latest/miniconda.html
Download the Windows Python 3.8 installer; I don't know whether you'd use the 32bit or 64 bit one. I did my Windows testing on the 64bit version. If your computer is not too old, I suspect it'll be 64bit; but pick the one that's right for your computer.

Installation instructions for Windows are here:
https://conda.io/projects/conda/en/latest/user-guide/install/index.html

Assuming you're on Windows 10:

- After downloading the miniconda .exe file, double-click on it
- Select the option to install for the local user only
- Accept the default installation path. I assume it'll be something like C:\Users\<USERNAME>\miniconda3
- On the Advanced Installation Options window, uncheck both boxes ("Add Miniconda3 ..." and "Register Miniconda3 ...")
- On the "Completing Miniconda3" window, you can do whatever you want (check or uncheck the boxes). If you have no preference, uncheck both boxes.

When installation is finished, from the Start menu, open the Anaconda Prompt or Anaconda Powershell Prompt; the latter will probably be nicer. Test it by running the command "conda list"

I will be putting together a text file called a conda environment file that lists the specific packages and versions that will be used. I'll send you that file and instructions to use it to create a conda environment.


## Create conda environment and install JupyterLab

You'll need to create a conda "environment" (a Python virtual environment). See [this link for complete documentation](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html), though it's not needed here.

1. Open the command shell (Anaconda Prompt or Anaconda Powershell Prompt, in my previous instructions).
2. cd (change directory) to where the conda environment `fhloo_environment.yml` file is located. For example: `cd C:\Users\user1\fhloo`
3. Create "fhloo" conda environment:  `conda env create -f fhloo_environment.yml`
4. "Activate" the environment to start using it:  `conda activate fhloo`

Until I send you the scripst, there's nothing further to do with this.

Separately, for your own exploratory work using Jupyter notebooks, I recommend you install JupyterLab (see the User Guide section at https://jupyterlab.readthedocs.io). To install it, open the command shell again (see #1 above) then create a new "jupyterlab3" conda environment as follows:
```bash
conda create -n jupyterlab3 -c conda-forge jupyterlab=3 nb_conda_kernels
```
