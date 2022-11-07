---
template: main.html
title: Getting started
---

## **Introduction**
Centre for Computational Modelling and Simulation (CCMS) aims to promote and support computational modelling as a mainstream research activity amongst the faculty and researchers of NIT Calicut. A High Performance Computing (HPC) Cluster and NVIDIA DGX Station purchased under HEFA are the major computing facility under this centre. The facility consists of 31 CPU nodes and 2 GPU nodes. The NVIDIA DGX Station has four V100 GPU accelerators. The facility is mainly for developing and running parallel codes for research purposes. The HPC system installed has been ranked as the 38th in the list of top 100 computing machines in India, in January 2021, a list maintained by **_CDAC, Bangalore_** [click here](https://topsc.cdacb.in/topsc.php/filterdetails?slug=January2021). 


## **System Configuration**
Wanted to know about system configuration 😀? Check the it [here](system_configuration.md)

## **Get an Account for You**
Centre for computational Modelling and Simulation (CCMS) comprises of a High Performance Computing cluster and a DGX Station that are available to both faculty and students. Inorder to get an account you may [download the application](http://www.nitc.ac.in/app/webroot/img/upload/Uersform-ccms.pdf) and submit filled application to the mail id : **ccmsadmin@nitc.ac.in** or through hardcopy

You will be notified once your account is approved. For NITC students, recommendation from the guide/ faculty is mandatory. A short proposal describing the computing to be carried out, justification for the use of HPC facility and expected outcome (1 page only) is to be attached with the submitted form. 



## **System Access**

The cluster can be accessed through Master node, which allows users to login, to submit jobs, transfer data and to compile source code. (If your compilation takes more than a few minutes, you should submit the compilation job into the queue to be run on the cluster.)

By default, a user will have access to home directory (/gpfs-home/) This directory is available on the login node as well as the other nodes on the cluster. And the /gpfs-scratch/ directory may be used for temporary data storage, generally used to store data required for running jobs. Any data stored in /gpfs-scratch will be deleted after 30 days.


### **Remote Access**

####`Using ssh in Windows`

:   Windows systems do not have any built-in support for using SSH, so you will have to download a software package to use SSH. PuTTY is the most popular open source (ie free) SSH client for Windows. To install it, visit the download site, and download the Installer package. Once installed, find the PuTTy application shortcut in your Start Menu, desktop. On clicking the PuTTy icon The PuTTy Configuration dialog should appear: Locate the Host Name input box in the PuTTy Configuration screen. Enter the server name you wish to connect to (e.g. [username]@[hpcipaddress]), and click Open. Enter your password when prompted, and press Enter. You are now connected!

####`Using ssh in Mac or Linux`

:   Both Mac and Linux systems provide a built-in SSH client, so there is no need to install an additional package. Simply locate and run the Terminal app. Once in the terminal, you can connect to an SSH server by typing the following command:




 <div class="termy">

            ```console
            // to access from your pc 
            user@my-pc:~$ ssh username@hostid

            // if a remote GUI section is required
            user@my-pc:~$ ssh username@hostid -X
            ```
                
  </div>

           




!!! info "Note"	

	Your user name and the hostid will be recieved through mail. Please check that. and replace username & hostid with appropriate value

!!! Note "How to change the user password?"	

	Use the "passwd" command to change the password for the user from the login node. 



## **Usage Policy and Guidelines**

* Application software available in the system / installed by user is to be used for academic purpose only and cannot be used for the monetary benefit of an individual or a company.
* To protect the security of the system, the user should neither provide his/her password nor allow other individuals to use his/her account. The system administrators may verify the above fact at any point of time. If found guilty, the user id will be cancelled without further reference to the user.
* Individuals who attempt to use accounts, files, system resources or other facilities without authorization or those who aid other individuals doing so, may be committing a criminal act and may be subjected to criminal prosecution.
* It is the responsibility of each individual user to know what effects the use of certain programs and/or facilities can have on other users and/or facilities, whether it may damage system resources or severely inconvenience other users currently using the system.
* System files and other application software installed by users and provided under license are not to be copied or tampered with.
* A Project Report is to be submitted at the end of the project.(1 page max.)
* Acknowledgement of the use of the center’s facilities should be made in journal publications, dissertations, theses, conference publications and reports published by the users.
* Any outcomes of the project, in terms of publications (journal / conference proceedings etc.) should be communicated to the center.
* Student Accounts will be deleted and the user files removed on graduation. 

## **Best Practices of HPC**

*    Do not go over your storage quota. Exceeding your storage quota can lead to many problems including batch jobs failing, confusing error messages and the inability to use X11 forwarding. Be sure to routinely run the "du -sh ~/ " command to check your usage. If more space is needed then remove files.
*    Do not run jobs on the Master node. When you connect to a cluster via SSH you land on the Master node which is shared by all users. The login node is reserved for submitting jobs, compiling codes, installing software and running short tests that use only a few CPU-cores and finish within a few minutes. Anything more intensive must be submitted to the Slurm job scheduler as either a batch or interactive job. Failure to comply with this rule may result in your account being suspended.
*    Do not try to access the Internet from batch or interactive jobs. All jobs submitted to the Slurm job scheduler run on the compute nodes which do not have Internet access. Because of this, a running job cannot download files, install packages or connect to GitHub. You will need to perform these operations on the login node before submitting the job.
*    Do not allocate more than one CPU-core for serial jobs. Serial codes cannot run in parallel so using more than one CPU-core will not cause the job to run faster. Instead, doing so will waste resources. See the Slurm page for tips on figuring out if your code can run in parallel and for information about Job Arrays which allow one to run many jobs simultaneously.
*    Do not run jobs with a parallel code without first conducting a scaling analysis. If your code runs in parallel then you need to determine the optimal number of nodes and CPU-cores to use. The same is true if it can use multiple GPUs. To do this, perform a scaling analysis as described in Choosing the Number of Nodes, CPU-cores and GPUs.
*    Do not request a GPU for a code that can only use CPUs. Only codes that have been explicitly written to use GPUs can take advantage of GPUs. Allocating a GPU for a CPU-only code will not speed-up the execution time but it will increase your queue time, waste resources. Furthermore, some codes are written to use only a single GPU. For more see GPU Computing and Choosing the Number of Nodes, CPU-cores and GPUs.
*    Do not load environment modules using only the partial name. You should always specify the full name of the environment module (e.g., module load compilers/intel/parallel_studio_xe_2020.4.912) and on some clusters failing to do so will result in an error. Also, you should avoid loading environment modules in your ~/.bashrc file. Instead, do this in Slurm scripts and on the command line when needed.
*    Please do not use spaces while creating the directories and files.







## **Transferring files between local machine and HPC cluster**

Users need to have the data and application related to their project/research work on Madhava HPC Cluster

To store the data special directories have been made available to the users with name “scratch and home” the path to this directory is “/gpfs-scratch” and “/gpfs-home”. Whereas these directories are common to all the users, a user will get his own directory with their username in /gpfs-scratch/ as well as /home-home/ directories where they can store their data. However, there is limit to the storage provided to the users, the limits have been defined according to quota over these directories, all users will be allotted same quota by default. When a user wishes to transfer data from their local system (laptop/desktop) to HPC system, they can use various methods and tools

A user using the ‘Windows’ operating system will get methods and tools that are native to Microsoft Windows and tools that could be installed on your Microsoft Windows machine.Linux operating system users do not require any tool. They can just use “scp” command on their terminal, as mentioned below.

Users are advised to keep a copy of their data with themselves, once the project/research work is completed by transferring the data in from Madhava HPC Cluster to their local system (laptop/desktop). The command shown below can be used for effecting file transfers (In all the tools):

		scp –r [path to the local data directory] [your username]@[IP of Madhava HPC:[path to directory on HPC where to save the data]

		

for example:

		scp –r /dir/dir/file sajil@:/gpfs-home/sajil

		

Same Command could be used to transfer data from HPC system to your local system (laptop/desktop).

		scp –r 	 [your username]@[IP of Madhava HPC:[path todirectory on HPC where to save the data] [path to the local data directory]

				

for example:

		scp –r 	sajil@[cluster IP/Name]:/gpfs-home/sajil/file /dir/dir/file

				

## **Running Interactive Jobs**

In general, the jobs can be run in an interactive manner or in batch mode. You can run an interactive job as follows:

The following command asks for a single core in testq for one hour with a default amount of memory.


			
		srun --nodes=1 --ntasks-per-node=1 --time=01:00:00 –partition=testq –job-name= job-name --pty /usr/bin/bash
	

The command prompt will appear as soon as the job starts. This is how it looks once the interactive job starts:

image

Exit the bash shell to end the job. If you exceed the time or memory limits the job will also abort. Please note that Madhava HPC Cluster is NOT meant for executing interactive jobs. However, for the purpose of quickly ascertaining successful run of a job before submitting a large job in batch (with large iteration counts), this can be used. This can even be used for running small jobs. The point to be kept in mind is that, since others too would be using this node, it is prudent not to inconvenience them by running large jobs.

## **Managing Jobs**

Madhava HPC Cluster extensively uses modules. The purpose of the module is to provide the production environment for a given application, outside of the application itself. This also specifies which version of the application is available for a given session. All applications and libraries are made available through module files. A User has to load the appropriate module from the available modules.

			
		module avail # This command lists all the available modules
		module load compilers/intel/parallel_studio_xe_2020.4.912 # This will load the intel compilers into your environment
		module unload compilers/intel/parallel_studio_xe_2020.4.912 # This will remove all environment setting related to intel compiler loaded previously
		module list #This will list currently loaded modules.
		

image

`A simple Slurm job script`


			
		#!/bin/sh
		#SBATCH --nodes 1 // specifies number of nodes
		#SBATCH --ntasks-per-node=40 // specifies core per node
		#SBATCH --time=06:50:20 // specifies maximum duration of run
		#SBATCH --job-name=lammps // specifies job name
		#SBATCH --output=job_output.txt //specifies output file name
		#SBATCH --partition=shortq // specifies queue name



		
		#SBATCH --ntasks=10 //specifies total no of cores required 
		##########################################################
		echo “Job Submitted”
		#load required modules
		module load ...
		#------------- run your commands here—-----------------#
		mpirun -n $SLURM_NTASKS ...
		echo “Job finished successfully”
		

###**List Partition**

sinfo displays information about nodes and partitions(queues).

		sinfo


###**Submit the Job**

To Submitting a simple standalone job , This is a simple submit script which is to be submitted

		sbatch job-script-name


###**List jobs**

Monitoring jobs on SLURM can be done using the command squeue. squeue is used to view job and job step information for jobs managed by SLURM
		squeue


###**Get job details**

scontrol can be used to report more detailed information about nodes, partitions, jobs, job steps, and configuration.

		scontrol show node - shows detailed information about compute nodes.
		scontrol show partition - shows detailed information about a specific partition
		scontrol show job - shows detailed information about a specific job or all jobs if no job id isgiven.
		scontrol update job - change attributes of submitted job.

###**Suspend a job (root only):**


			
		# scontrol suspend 135
		# squeue
		JOBID PARTITION NAME     USER  ST TIME NODES NODELIST(REASON)
		135   shortq    simple.s user1 S  0:13  1     compute01
		

###**Resume a job (root only):**


		# scontrol resume 135
		# squeue
		JOBID PARTITION NAME     USER  ST TIME NODES NODELIST(REASON)
		135   shortq    simple.s user1 R  0:13 1     compute01
		

**Kill a job.**

Users can kill their own jobs, root can kill any job.


		$ scancel 135
		$ squeue
		JOBID PARTITION NAME USER ST TIME NODES NODELIST(REASON)
		

###**Hold a job:**


		$ scontrol hold 139
		Release a job:
		$ scontrol release 139
		

## **More about Batch Jobs (SLURM)**

SLURM (Simple Linux Utility for Resource Management) is a workload manager that provides a framework for job queues, allocation of compute nodes, and the start and execution of jobs.

It is important to note:

* Compilations are done on the login node. Only the execution is scheduled via SLURM on the compute/GPU nodes
* Upon Submission of a Job script, each job gets a unique Job Id. This can be obtained from the ‘squeue’ command.
* The Job Id is also appended to the output and error filenames.

###**Parameters used in SLURM job Script**

The job flags are used with SBATCH command. The syntax for the SLURM directive in a script is "#SBATCH ". Some of the flags are used with the srun and salloc commands.

|Resource Flag 		|	Syntax 		       |	Description				     |
|-----------------------|------------------------------|-----------------------------------------------------|
|partition 		| --partition=partition-name   |Partition is a queue for jobs.			     |
|time 			| --time=01:00:00 	       |Time limit for the job.				     |
|nodes 			| --nodes=2 		       |Number of compute nodes for for the job		     |
|cpus/cores 		| --ntasks-per-node=8 	       |Corresponds to number of cores on the compute node   |
|job name 		| --job-name="job-1" 	       |Name of job					     |
|output file 		| --output=job-1.out 	       |Name of file for stdout.                             |
|access 		| --exclusive 		       |Exclusive access to computenodes                     |
|resource 		| --gres=gpu:2 		       |Request use of GPUs on compute node                  |




###**Some useful SLURM commands.**


|Sl No 	|Purpose 					|Command                                                 |
|-------|-----------------------------------------------|--------------------------------------------------------|
|1 	|To check the queue status 			|squeue                                                  |
|2 	|To check the status/ availability of nodes 	|sinfo                                                   |
|3 	|To cancel a job running 			|scancel  note: job id can be obtained by command squeue |
|4 	|To check the jobs of a particular user 	|squeue -u                                               |
|5 	|To list all running jobs of a user 		|squeue -u -t RUNNING                                    |
|6 	|To list all pending jobs of a user 		|squeue -u -t PENDING                                    |
|7 	|To cancel all the pending jobs for a user 	|scancel -t PENDING -u username                          |

## **Addressing Basic Security Concerns**

Your account on Madhava HPC Cluster is ‘private to you’. You are responsible for any actions emanating from your account. It is suggested that you should never share the password to anyone.

Please note that, by default, a new account created on Madhava HPC Cluster is readable by everyone on the system. The following simple commands will make your account adequately safe.


|Command   	  	    |Discription																				  |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|chmod 700 [directory name] |will ensure that only yourself can read, write and execute files in your directory                                                                                         |
|chmod 750 [directory name] |will enable yourself and the members of your group to read and execute files in your directory										   |
|chmod 775 [directory name] |will enable yourself, your group members and everyone else to read and execute files in your directory									   |
|chmod 777 [directory name] |will enable EVERY ONE on the system to read, write and execute files in your directory. This is a sort of ‘free for all’ situation. This should be used very judiciously   |



