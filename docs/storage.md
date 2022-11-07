---
template: main.html
title: Storage
---

# Storage

## About Madhava HPC Storage
Since there are many users and large computations used to run, much more space is  needed to store all user data compared to a personal computer. In `Madhava HPC Cluster` different types of storages are there.

Like a desktop or laptop computer, individual cluster nodes often have local disk drives. Since this storage is local to a node, it is usually faster to access by the processes running on the node. On Madhava HPC Cluster these local drives are used for system softwares.

Most of the data on a cluster is kept in separate storage units that have multiple hard drives. These units are called file servers. A file server is a computer with the primary purpose of providing a location to store data. Regular users do not login to file servers. On HPC clusters these file servers are connected to the same Infiniband switch that connects all nodes, providing relatively fast access to data from all cluster nodes.

Every user on a cluster has a home directory. If you type "pwd" right after ssh-ing to a cluster, you should see /gpfs-home/<username>, where <username> is your Login Id & home directories are  accessed on any cluster node.

Since there are multiple users on a cluster, to minimize one user's actions affecting other users, home directories have quotas. On HPC clusters listed on this site, one can not keep more than 500GB of data in their home directory. Users keep important data in the home directories. For optimal performance we recommend to keep file system less than 70% full. 

And finally cluster have separate scratch space named /gpfs-scratch/<username> that is mounted on all nodes. This storage is not backed up and is purged regularly. Users are requested to use this space as their SCRATCH directory instead of /tmp for smooth running of the program. Since many high computational jobs create scratch files of large size, using scratch to /tmp will lead to inapprpriate halting of the code and functioning of the cluster. If users couldn't find their directory in /gpfs-scratch, please contact CCMS Admin. 


## Storage Policies
* Use /gpfs-home/<username> and /gpfs-scratch/<usernae> as your home and scratch directory.
* regularly backup your important files from /gpfs-scratch
* The quota for home and scratch is shown in table below.

| Directory              | Quota                  |
|:----------------------:|------------------------|
|      Home directory    | 204TB                  | 
|    Scratch Directoty   | 70 TB                  | 
|       User Home        | 500 Gb                 | 


