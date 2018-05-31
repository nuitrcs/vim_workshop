# VIM Workshop

Materials for VIM workshops taught by Northwestern IT Research Computing
Services.

# Setup

## Setting up VIM

### Mac and Linux
On Mac and Linux a small version of Vim is pre-installed and can be
accessed via Mac Terminal and Linux Shell. You can verify the
installation by issuing "vim --version" command on the terminal or shell.

### Windows
For this workshop we recommend Windows users to download Git Bash as
it provides a basic Unix Shell equipped with Vim. Git Bash is included in
Git for Windows. If you do not already have Git installed for Windows,
you can download an installer at [http://git-scm.com/](http://git-scm.com/).

During installation, you can use the default options presented except
for **_Adjusting your PATH environment_** step. For this step, select "**_Use
Git from Git Bash only_**" option so environment variables are not
be modified.


## Setting up Python (Optional)

### Mac and Linux
The workshop also includes an example where we will run a python script.
For most Mac and Linux machines the operating systems have native python
versions. Python version can be verified by issuing "python --version"
command on the terminal or shell.

### Windows
We recommend Anaconda Python 3.6 which can be downloaded from
https://www.anaconda.com/download/ if you do not already have it in the
Windows device. Do the installation just for your user and UNCHECK any
of the options presented in the **_Advanced Installation Options_** step
so that environmental variables are not modified.

To use Anaconda Python from Git Bash, issue the following commands in the
bash shell:
```bash
export PATH=$PATH:~/Anaconda3/
```
```bash
alias python='winpty python.exe'
```

