---
title: How to access and work on Einstein's HPC cluster
author: Daniel Piqué
date: '2017-11-29'
slug: introduction-to-einstein-s-hpc-cluster
categories: []
tags: []
output:
  html_document:
    highlight: pygments
---


1. Request access to the cluster. This can be done by emailing [Brent Solly](https://www.einstein.yu.edu/search/?q=brent%20solly&searchType=directories) or [Shailesh Shenoy](https://www.einstein.yu.edu/search/?q=Shailesh+Shenoy&searchButton.x=0&searchButton.y=0&searchType=directories) and asking to be added as a user. An account and userid will be created for you.

2. Open up a terminal (Mac/Linux) or command prompt (Windows)

3. In the prompt, type `ssh user_id@ip_address`, where `user_id` is your montefiore ID/username, and `ip_address` is the IP address shared with you by the IT team (should start with the number 10 and be in the following format: 10.xx.x.xx)

4. Type the password associated with your montefiore id.

5. You now should be on the login node. The command prompt may have your montefiore id followed by an @ symbol, followed by the word "loginnode". This is how you know you're on the login node. 

- Note: The login node is where all users are directed after they log in. Computations should not be performed on this node, however. This is because there is a limited amount of memory on this node, and computations performed on this node will affect the ability of other users to log in and navigate through the cluster. 

6. Next, we should log in to a compute node. This is where all of the computations will be performed. To do this, type `qrsh -l h_vmem=20G`. You can adjust `20G` to the amount of memory that you want (for reference, many modern laptop computers have 8 or 16 GB of memory). You can also use `qsub` to submit a job to the cluster. `qsub` and `qrsh` are the 2 ways to interact with the cluster's compute nodes, with the latter being an 'interactive' approach.

7. Now, we can load R. To do this, we first have to load the module. Type `module load R` and then tab, which will display the available versions of R. To see all available modules type `module avail`.

8. You'll need to upload your data to the cluster to perform computations. To do so, use the [`scp` command](https://www.garron.me/en/articles/scp.html). The following command will transfer `file1.txt` onto the home directory on the cluster: `scp file1.txt user_id@ip_address:~/` There are also other file transfer methods, and you can even drag and drop once you have the network drive mapped on your computer (see below).

9. You can also mount the cluster to your computer, so that you can use the Finder or Explorer windows to navigate through the cluster's file system.  [Here](http://osxdaily.com/2010/09/20/map-a-network-drive-on-a-mac/) are instructions for doing so on a mac, and [here](https://www.laptopmag.com/articles/map-network-drive-windows-10) are the instructions for doing so on a PC. If you have R or RStudio on your computer, you can set the working directory to the cluster and read files directly from the cluster. 

### Additional Resources

- There are many types of HPC clusters. Einstein's cluster runs on the Sun Grid Engine (SGE), so even though there is no Einstein-specific documentation on how to use the cluster, we can reference the [documentation](http://gridscheduler.sourceforge.net/htmlman/manuals.html) and publicly available [tutorials](http://star.mit.edu/cluster/docs/0.93.3/guides/sge.html) from other institutions that also use the SGE to learn about how to use our cluster.

- Email support@penguincomputing.com if you need to install an R package. If the cluster is not working, submit at ticket with through the [IT support portal](https://itsupport.einstein.yu.edu/) (note: you have to be on Einstein's campus or using VPN to access this site)
