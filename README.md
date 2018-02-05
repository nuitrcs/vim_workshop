# Git Workshop

Materials for git workshops taught by Northwestern IT Research Computing
Services.

# Setup

## Setting up VIM

### Mac and Linux
On Mac and Linux a small version of Vim is pre-installed and can be
accessed via Mac Terminal and Linux Shell.

### Windows
For this workshop we recommend Windows users to download Git Bash as
it provides a basic we use Vim from Unix Shell. Git Bash is included in
Git for Windows. If you do not already have Git installed for your Windows,
you can download an installer at [http://git-scm.com/](http://git-scm.com/).

During installation, you can use the default options presented except
for **_Adjusting your PATH environment_** step. For this step, select "**_Use
Git from Git Bash only_**" option so your environment variables are not
be modified.


## Setting up Python (Optional)

### Mac and Linux
The workshop also includes an example where you will run a python script.
For most Mac and Linux machines the operating systems have native python
versions.

### Windows
We recommend Anaconda Python 3.6 which
can be downloaded from https://www.anaconda.com/download/ if you
don not already have it in you Windows device. Do the installation just
for your user and UNCHECK any of the options presented in the
**_Advanced Installation Options_** step so that your environmental
variables are not modified.

To use Anaconda Python from Git Bash, issue the following commands in the
bash shell:
```bash
export PATH=$PATH:~/Anaconda3/
```
```bash
alias python='winpty python.exe'
```

