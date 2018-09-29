## Buildng a Beowulf Cluster and Installing it on Ubuntu 16.04

The pages has the steps for:

A. Installation for Beowulf Cluster,

B. Internet resources for Cluster development

C. Software for accessing cluster

D. Accessing the cluster,

E. Problems faced during installation
 

A. Steps for Installation of Beowulf Cluster:
1. Hardware connections
2. Master PC installation
3. Worker PC installation
4. Worker PC Cloning
5. Installing Workload Manager (Optional. For giving access to multiple users)

1. Hardware Connections
* One of the PC is master node and others will be worker nodes.
* Master will require 2 LAN cards: one connects to the internet directly and the other to the network router for communicating with other worker PCs.
* Make hardware connections Ethernet cables: one from each PC should go to the network router.
* You might want a KVM (Keyboard-Video-Mouse) switch for cluster installation. This helps to access multiple PCs with one monitor, keyboard and mouse.


2. Master Node Installtion
* I hope you want to install Beowulf using Ubuntu. You can follow the steps given here:

* [https://www.linux.com/blog/building-beowulf-cluster-just-13-steps Building a Beowulf Cluster in just 13 steps] (Start with this)
* [https://help.ubuntu.com/community/MpichCluster MPICH Cluster Linux] (And This)

You will Installing MPI (Message Passing Interface) variant: MPICH, OpenMPI, etc. on the master PC
* Then install the softwares you need.
 

3. Worker Nodes
Install MPI and the software (according to the instructions given in the above 2 links) on one worker PC.
If the worker PCs are of the same configuration, you can clone the single worker (called the Golden Worker) to other workers. You do not to install even the Operating System. All the drivers, hard-disk configurations and softwares are cloned to the new PC. You will just need to rename the PC and assign a local IP address

4. Clone Golden Worker PC: See this page
https://en.wikibooks.org/wiki/Building_a_Beowulf_Cluster/Cloning_of_Slaves


5. Install a WorkLoad Manager
* Workload manager such as Slurm is a job scheduling software used when you have multiple users using the same resource.

 [https://en.wikipedia.org/wiki/Slurm_Workload_Manager Slurm Workload Manager]

It is an open-source job scheduling software used by more than 60% of Top500 supercomputers in the world. [https://slurm.schedmd.com/ Website]

* List of other Workload managers: [https://developer.nvidia.com/cluster-management List 1] [http://redbarnhpc.redbarncomputers.com/support/resources/ List 2]

* [http://etutorials.org/Linux+systems/cluster+computing+with+linux/Part+III+Managing+Clusters/Chapter+14+Cluster+Workload+Management/ Tutorial for setting -up Workload Manager on Beowulf Cluster]



B. Some internet resources
== Best Resources ==
* [https://www.linux.com/blog/building-beowulf-cluster-just-13-steps Building a Beowulf Cluster in just 13 steps] (Start with this)
* [https://help.ubuntu.com/community/MpichCluster MPICH Cluster Linux] (And This)
* [https://en.wikibooks.org/wiki/Building_a_Beowulf_Cluster WikiBooks] (Use Case. You could go through this)


Others:
* [http://byobu.info/articles/Building_a_simple_Beowulf_cluster_with_Ubuntu.html Building a simple Beowulf cluster with Ubuntu]
* [https://www-users.cs.york.ac.uk/~mjf/pi_cluster/src/Building_a_simple_Beowulf_cluster.html Building a simple Beowulf cluster with Ubuntu]
* [http://webhome.phy.duke.edu/~rgb/brahma/Resources/beowulf/ Beowulf Project at CESDIS (NASA)]
* [http://mpitutorial.com/tutorials/installing-mpich2/ MPI Tutorial]
* [https://www.youtube.com/watch?v=kcBMtMiTHHE How to build a beowulf]
* [http://svn.oscar.openclustergroup.org/trac/oscar/wiki/DistroSupport OSCAR]
* [http://oss.sgi.com/LDP/HOWTO/Beowulf-HOWTO.html#toc5 Beowulf HOWTO]
* [http://www.beowulf.org/overview/faq.html Beowulf.org]
* [http://www.beowulf-underground.org/ beowulf-underground]
* [http://www.zdnet.com/article/build-your-own-supercomputer-out-of-raspberry-pi-boards Raspberry Pi Supercomputer]
* [http://www.linux-magazine.com/Issues/2013/154/Getting-Started-with-HPC-Clusters Getting started with HPC]
* [http://mpi-forum.org/ MPI Forum]



C. Useful software for cluster

cssh (Cluster SSH) to log on to all worker PCs at once.

top or 'htop' to see the CPU and memory usage.

Meld: For file/folder comparison.

Text Editors: Both the text editors below have option for hoc and mod syntax highlighting

Microsoft Visual Studio Code (Another text editor)

Sublime Text editor



MATLAB: Parallel computing with MATLAB® on a cluster requires two products:
* MATLAB Distributed Computing Server™, which should be installed on each computer of the cluster that performs the computation.
* Parallel Computing Toolbox™, which should be installed on the computer where you write your applications.

*[https://in.mathworks.com/support/product/DM/installation/ver_current.html Install]


D. Using the Cluster

Ubuntu:

Use ssh. Open Terminal. ssh using user credentials: ssh username@IPADDRESS.

File transfer using FTP.

Windows:

The cluster could be accessed using

* Graphical User Interface (GUI via Remote Desktop Connection) or

* Command line (using secure shell protocol, ssh).


Graphical User Interface Based (Windows): There are two processes to be done here:

*File Transfer using Winscp or a Network folder.
*Running the Simulation using Remote Desktop Connection.


'''Softwares to Access Cluster from Windows'''
* [https://support.microsoft.com/en-us/help/17463/windows-7-connect-to-another-computer-remote-desktop-connection Windows Remote Desktop Connection]
* '''File Transfer''': [https://winscp.net/eng/docs/introduction 'Winscp']
    Its main function is file transfer between a local and a remote computer. Beyond this, WinSCP offers scripting and basic file manager functionality.
    [https://winscp.net/eng/docs/after_installation How top Use it]

   It also has several built-in functionalities e.g. ssh shell, script editor

   https://www.slant.co/versus/5954/5955/~filezilla_vs_winscp


Command Line Based (Windows)

a. Install Putty: http://www.putty.org/

b. Launch Putty from Windows menu

c. Type IP Address in the Host Name

d. Login using user credentials.

e. Copy file from your PC to cluster using the scp command.

Optional Xming server could be used to see gui along with command line. g. Download and install Xming Server: https://sourceforge.net/projects/xming/

h. Launch Xming Server before logging in through Putty.

i. Now, if you launch any GUI based program from Putty e.g. firefox, nrngui you will see their graphical window.


E. Some Problems faced during the development

In the 13 step guide to cluster development
** Needed to install a fortran compiler at step 9 before configure step. Compiler installed gfortran
*** sudo apt-get install gfortran
** used latest version of MPICH: mpich-3.2
** For step number 11: Use this (instead of what is mentioned in the step)

echo /home/mpiuser/mpich1/bin | sudo tee -a /etc/environment

or

sudo bash -c 'echo /home/mpiuser/mpich1/bin >> /etc/environment'



Cloning of Golden Slave

On the golden slave (or an identical clone) you run:

node1# dd if=/dev/hda conv=sync,noerror bs=64k | nc -l 5000

On the completely blank soon-to-be-slave you run:

node2# nc 192.168.1.6 5000 |  dd of=/dev/hda bs=64k

where 192.168.1.6 is the ip of the golden slave. This presupposes the disk of soon-to-be slave is at least as big as the disk in the golden slave.

This took several (~4) hours time, but it worked.

'''NB: Don't forget to go to superuser before using these commands i.e. use sudo su'''

or

Use these

node1# sudo dd if=/dev/hda conv=sync,noerror bs=64k | nc -l 5000

node2# nc 192.168.1.6 5000 | sudo dd of=/dev/hda bs=64k

dd is convert and copy and requires administrative priviledges.
[https://www.gnu.org/software/coreutils/manual/html_node/dd-invocation.html dd reference]



Password Less SSH

Procedure to create a password-less ssh access:

A password-less ssh access should be maintained from the master to the slaves for the proper working of the beowulf cluster. This was done using the following procedure in the terminal of the master node -

1. $ ssh-keygen

just press Enter key with empty strings, whenever prompted. You will be prompted three times (i) Enter file in which to save the key (ii) Enter the passphrase (ii) Enter the passphrase again.
2. $ ssh-copy-id <username>@<host_ip_address>

Here the username is mpiuser (which is the username currently set for all the nodes in this cluster - this may be changed later as per the imagination of lab sysad). The host_ip_address is the ip address for the slave node to which password-less access is to be established from the master node. For the current cluster, a local ip address of the format 192.168.1.X is set ( X = 5 for master node, 6, 7, 8 for slaves 1, 2, and 3).
   - After this command, you will be prompted to enter the password to the slave node. You have to enter the password once.

Thats it! After this you can ssh to the slave node from the master node using the command

$ ssh <username>@<host_ip_address>

without entering a password.

For detailed explanation, please visit [https://www.linuxbabe.com/linux-server/setup-passwordless-ssh-login this page].​


Problems with the shared folder :"/mirror"

The folder is the root directory. And is not allowing to add new files to the folder.

* Solution:
i) Try to change the ownership of the folder,
* Problem during shutting down of the PC. The PC remains at the splash screen for a lot of time and does not get shut down.​

ii) Write a script to copy data from master to all worker PCs after doing pasword-less ssh.


Display Driver Problems: GUI (Unity) won't resume after screen suspend. Try these options:
https://askubuntu.com/questions/760043/ubuntu-16-04-unity-desktop-environment-doesnt-load-after-fresh-install

	
