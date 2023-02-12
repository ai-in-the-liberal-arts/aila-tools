+++
title = "High-Performance Computing using Clojure on the Amherst Cluster"
description="The Amherst College cluster helps you perform high-performance computing by completing independent tasks parallel to each other."
date = 2022-05-12
[extra]
author = "Lovemore Nyaumwe"
+++

The Amherst College cluster helps you perform high-performance computing by completing independent tasks parallel to each other. Users can find further information about that [here](https://www.amherst.edu/offices/it/knowledge_base/academic-resources/unix_servers/using-the-college-computer-cluster). In this article, I intend to provide a tutorial on using Clojure on the Amherst Cluster.

**Instructions for running Clojure jobs on the Amherst cluster** :

In your Terminal:

> ssh YourAmherstUsername@cluster.amherst.edu

Answer “yes” to **"Are you sure you want to continue connecting (yes/no)?"**

When asked, enter your Amherst password. Look at what’s here (your prompt will look different):

> **[lspector@csc3-desktop ~]$** ls
> **cluster-archive cluster-scratch**

Change directories into cluster-scratch:

> **[lspector@csc3-desktop ~]$** cd cluster-scratch

Run leiningen with no arguments:

> **[lspector@csc3-desktop cluster-scratch]$** lein

It should download some files and then display the leiningen documentation, leaving you back in the shell. This gets leiningen set up in your directory and shows that it is working. As with many of the other steps below, the downloading part will happen only the first time you do this.

Launch a REPL, independent of any project:

> **[lspector@csc3-desktop cluster-scratch]$** lein repl

It will download more files and then give you a REPL. Do some REPL interaction and then (quit) to get back to the shell prompt.

For your actual work, you may want to use scp or “git clone” to get your project to the cluster but to try things out; we’ll just make a new one that is set up to run from the command line.

Create a new project:

> **[lspector@csc3-desktop cluster-scratch]$** lein new app foo

This creates a new project called foo using the app template, which means that its project.clj and core.clj are set up so that “lein run” will run the -main function in core.clj.

Change directories into the project:

> **[lspector@csc3-desktop cluster-scratch]$** cd foo

Run the project:

> **[lspector@csc3-desktop foo]$** lein run

This will download more files and then print “Hello, World!”, which is all that the default new project does, and then it will leave you back in the shell.

Now we want to run a couple of instances of this program on different cluster nodes, dispatched through the “Condor” job-management software. You shouldn’t run intensive stuff on the “head” node, to which we’re currently logged in; you always want to dispatch those to the cluster nodes. You should get your project running first on your local machine, launching your runs with “lein run,” so that you know it will launch correctly, and then move it to the cluster in your cluster-scratch directory, and continue with the following steps that we’ll use here just to run a couple of instances of the default “Hello, World!” program.

To run instances of the program on cluster nodes, we first make a command file that describes the complete set of runs that we want to do. Again, you might want to compose this elsewhere or generate it from code for your actual work, but here we’ll just create a simple one right on the cluster, using a terminal-based text editor called nano.

Still, in the project directory, create and edit the new file:

> **[lspector@csc3-desktop cluster-scratch/foo]$** nano foo-runs.cmd

Then paste in the following (without the “------” lines at the beginning and end, with your Amherst username in place of YourAmherstUsername, and if you’re doing this for a different project, then your project name in place of foo:

*## Global job properties*
*universe = vanilla*
*notification = error*
*notify_user = YourAmherstUsername@amherst.edu*
*initialdir = /mnt/scratch/YourAmherstUsername/foo*
*getenv = True*
*executable = run*

*## Job properties*
*output = /home/YourAmherstUsername/cluster-scratch/foo/results/0/out*
*error = /home/YourAmherstUsername/cluster-scratch/foo/results/0/err*
*log = /home/YourAmherstUsername/cluster-scratch/foo/results/0/log*
*queue*

*## Job properties*
*output = /home/YourAmherstUsername/cluster-scratch/foo/results/1/out*
*error = /home/YourAmherstUsername/cluster-scratch/foo/results/1/err*
*log = /home/YourAmherstUsername/cluster-scratch/foo/results/1/log*
*queue*

Then hit ctrl-x to exit. It’ll ask you if you want to save it; press Y for yes. It’ll ask you what you want to name it; just hit return to accept the name you used when you started nano.

That command file just specifies two runs, which will both be the same in this case because we haven’t made foo do anything that isn’t completely deterministic. But if you use Clojure’s random functions, each one will start with a different seed and potentially do something different. Jobs (runs) can also be made to take arguments from the command line, which can vary from job to job, and there are many other options for things that can appear in Condor command files, but this will do for now.

You also need to create an executable file called “run” that launches a run.

Do this again with nano:

> **[lspector@csc3-desktop cluster-scratch/foo]$** nano run

In the run file, add just the following two lines (without the “------” lines):

> #! /bin/sh
> lein run

Then exit, saving it as you do so.

Then we have to make run executable, which we can do like this:

> **[lspector@csc3-desktop cluster-scratch/foo]$** chmod +x run

Finally, we must create the output directories that we specified in the command file. First, create the results directory:

> **[lspector@csc3-desktop cluster-scratch/foo]$** mkdir results

Then create both of the specific output directories:

> **[lspector@csc3-desktop cluster-scratch/foo]$** mkdir results/0

> **[lspector@csc3-desktop cluster-scratch/foo]$** mkdir results/1

Finally, we’re ready to submit the jobs to Condor:

> **[lspector@csc3-desktop cluster-scratch/foo]$** condor_submit foo-runs.cmd
> **Submitting job(s)…**
> **2 job(s) submitted to cluster 598.**

You can monitor your submitted jobs with:

> **[lspector@csc3-desktop cluster-scratch]$** condor_q YourAmherstUsername

If something went wrong, which you might know from seeing that your jobs are “held” for a long time, or there’s no output appearing, or if you want to kill them for some other reason, you can do that with condor_rm and the job number it printed when it launched:

> **[lspector@csc3-desktop cluster-scratch]$** condor_rm 598

On the other hand, if all goes well, then your results will appear in the results directories. Here I’ll use the Unix ls command to see all of the resulting files and the cat command to print all of the “out” files:

> **lspector@csc3-desktop foo]$** ls results/*
> **results/0/err results/0/log results/0/out results/1/err results/1/log results/1/out**
> **[lspector@csc3-desktop foo]$** cat results/*/out
> **Hello, World!**
> **Hello, World!**

Some more details, but written for use in a different context (for Python programs for physics), are available [here](https://www.ats.amherst.edu/software/scipy/index3.html#HighPyrformanceComputing).
