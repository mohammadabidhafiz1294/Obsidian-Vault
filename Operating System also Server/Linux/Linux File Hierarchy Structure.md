## Introduction

The Linux File Hierarchy Structure or the Filesystem Hierarchy Standard (FHS) defines the directory structure and directory contents in Unix-like operating systems. It is maintained by the Linux Foundation.It’ll be using the term Linux hereafter instead of UNIX though

-   In the FHS, all files and directories appear under the root directory /, even if they are stored on different physical or virtual devices.
-   Some of these directories only exist on a particular system if certain subsystems, such as the X Window System, are installed.
-   Most of these directories exist in all UNIX operating systems and are generally used in much the same way; however, the descriptions here are those used specifically for the FHS and are not considered authoritative for platforms other than Linux.

	**Is Only a hierarchy structure??**
	
	The Linux Filesystem Hierarchy Standard (FHS) is not just a structure, it is a set of guidelines that aim to ensure that all Linux distributions use a consistent and predictable file system structure. The FHS specifies the location and purpose of important system files and directories, and helps ensure that software applications can find the resources they need in a predictable way.
	
	The FHS is important because it makes it easier for users and developers to navigate the file system and understand where things are located. It also helps ensure that software applications and system utilities work correctly across different Linux distributions.
	
	While the FHS is not a requirement, most Linux distributions follow it closely to ensure consistency and compatibility
	

## Explaintion 

![[linux system structure.jpg| 500]] 

![[linux system structure 2.png| 500]]

