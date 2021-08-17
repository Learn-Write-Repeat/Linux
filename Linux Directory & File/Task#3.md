# Linux Users & Groups
Linux/Unix operating systems offer the provision to support multiple users, where the same computer resources- hard disk, memory, etc.-are accessible to the various accounts associated with the device. 

However, in order to allow multiple users to co-exist on a device, protection of individual data and files against unauthorized access must be ensured. 
Here, a term called *'permissions'* comes to our aid.

## The Read, Write and Execute Permissions
*Permissions* serve to define the privileges or rights that a user, or a set/collection of users (called a *group*) enjoys in terms of three categories of actions *viz.,* *Read, Write,* & *Execute*, usually executed on files, which are simply collections of alike data, and/or directories (collections of files). 

**1. Read** 
A *read (abbr. as 'r')* permission is restricted to allow the user to be able to only view the contents of the files, and list the compositions of a directory. No modifications can be performed by the user(s) with the *read* privilege. 

**2. Write**
A *write (abbr. as 'w')* permission on a file allows the user(s) to modify the contents of that file and, for a directory, the write permission grants the right to edit the contents of a directory (e.g. add/delete files).

**3. Execute**
For a file, the *executable (abbr. as 'x')* permission grants the user(s) the ability to run the file and execute the program or script contained in it. For a directory, it allows user(s) to change to a different directory and make it their current working directory.

To view the permissions on an existing file/directory, run the command, **`ls -l <directory/file>`**, replacing *<directory/file>* with the actual name, accompanied by the extension of the file.

> **`-rwxrwxrwx 1 eccentric_undergrad eccentric_undergrad 55 Aug  8 17:08 Test.txt`**

The output contains the following elements:
1. The first ten characters show the *access permissions*:
			i. The `-` indicates the nature of the file (where, `d` for directory, `s` for special file, and `-` for a regular file.
			ii. The next three characters (`rwx`) denote the permissions of user pertaining to the said file/directory. 
			In the above example, the user has the privilege to read, write as well as execute the file *'Test.txt'*.
			iii. The following three characters (`rwx`) represent the permissions assigned to the members of the group the user belongs to, pertaining to this file/directory.
			iv. The last three characters (`rwx`) denote the permissions all the other users on the system can enjoy, pertaining to the said file/directory.
			
2. After the permissions, comes the *number of links* associated with the said file.
3. For a file, the *date & time* that the file was last modified while for a directory, it is the time that the directory was created.  

### Changing File & Directory Permissions
To change file & directory permissions in Linux by the owner, initiate the following commands according to the context of use:  

>   **chmod +rwx < filename>**:  to add permissions.
>   **chmod -rwx < directoryname>**:  to remove the existing permissions.
>  **chmod +x < filename>** : to allow executable permissions for the given.
>   **chmod -wx < filename>**:  to remove write and executable permissions.


### Changing File & Directory Permissions in Linux for the Group Owners 
Much like the owner-specific permissions, for changing the file & directory permissions of group and other miscellaneous users (i.e., other than the owner), the following commands must be executed:

>   **chmod g+w < filename>**: to add write permissions for group users.
>   **chmod g-wx < filename>**: to remove write and executable permissions for group users.
>   **chmod o+w < filename>**: to add write permissions for *other* users.
>   **chmod o-rwx < foldername>**: to remove write and executable permissions for *other* users.

In order to change directory permissions for everyone, use, `ugo` (where, `u` stands for users, `g` for group, and `o` for others) or `a` (for all).

>   **chmod ugo+rwx < foldername>**:  to set read, write, and execute permissions for everyone.
>   **chmod a=r < foldername>**:  to grant only read permission to all users.


## User Shell

A *shell* is an environment in which the users can use interact with the operating system and avail to its utilities such as execute commands, programs, and shell scripts, manage & open files, perform system administrative tasks, etc. It provides the users with an interface to the Linux/Unix system and functions to gather input from the users and execute the programs based on that input and finally display that program's output.

There are different flavors of a shell, just as there are different flavors of the Linux operating systems, and each flavor of shell has its own set of recognized commands and functions. 

In Linux/Unix, there are two major types of shells −

**1. Bourne shell**
The original UNIX shell (command execution program, often called a command interpreter), developed at AT&T. 
The Bourne Shell has the following subcategories:
-- Bourne shell (sh)
-- Korn shell (ksh)
-- Bourne Again shell (bash) 
-- POSIX shell (sh)

**2. C shell** 
A command shell for Unix-like systems that was originally created as part of the Berkeley Software Distribution (BSD) in 1978.
The different C-type shell include: 
-- C shell (csh) 
-- TENEX/TOPS C shell (tcsh)

### Determing User Shell

The information pertaining to the shell(s) existing in your Linux system are stored in the **`/etc/shells`** file, and its contents can be easily be listed (even by a normal user *(see definition below)*) by executing the command,
>**`cat /etc/shells`** 

Moreover, if need arises, any user can switch from the existing shell assigned to the them to only the shells present in the **`/etc/shells`** file. Only a root user *(see definition below)* can run a shell which is not present in the **`/etc/shells`** file.

### Changing User Shell
Firstly, if you are unsure about your currently assigned shell, issue the command,
>**`grep <username> /etc/passwd`**

by replacing < username> with your account's username.

Now, run one of the following commands on your terminal to change your currently assigned shell:

>**`chsh --shell /bin/sh <username>`**
> 
>**`usermod --shell /bin/bash tecmint`**
>
Run the **`grep`** command once again to verify if your shell has been changed.


## User Management 

In Linux, users are categorised into two different types: 
1. Root/System User/Administrator
System users are created by default with the system, and enjoy the privilege of universal access to all the files existing on the device.
2. Normal Users
Regular users are created by system administrators and can log into the system and use it. They usually possess a limited access to the system resources of files and directories.

Users in the Linux system are distinguished by a string of characters unique to a particular user, known as the *user identification number* or *UID*.

### The `/etc/passwd` file

All the information associated with a user account is stored in a file identified as **`/etc/passwd`**. 

The essential user information, used at time of login and for system user management is stored in the **`/etc/passwd`** in plain text format, with general read permissions granted to normal users, while the write and modify permissions are usually restricted to the root user only.

Inorder to list the content of the **`/etc/passwd`** file, type the command,
> **`cat /etc/passwd`**

on your shell and execute it.

The contents of the file, stored as *colon-separated* entries, are described below:


>**`eccentric_undergrad:x:1000:1000:,,,:/home/eccentric_undergrad:/bin/bash`**
>
>`[username]:[password]:[UID]:[GID]:[GECOS]:[home_dir]:[shell_path]`

1.  **Username**
 It should be between 1 and 32 characters in length, and is used when user logs in.
2.  **Password**
The *'x'* character following the username indicates that password, which is encrypted, is stored in /etc/shadow file. 

3.  **User ID (UID)**
Each user is assigned a unique user ID (UID). 

4.  **Group ID (GID)**

5.  **User ID Info (GECOS)**
Referring to the *comment field*, it allows the system adiministartor/root user to add extra information about the users etc. 

6.  **Home directory**
It is the absolute path to the directory the user will be in when they log in. If this directory does not exist in the system, the user's directory becomes `/`.

7.  **Command/shell**
This part denotes the absolute path of the user command shell *(/bin/bash)*. 
*Please note that it does not necessarily have to be a shell. For example, *sysadmin* can use the *nologin shell*, which acts as a replacement shell for the user accounts. 

### Creating New User Accounts
When a new user is created, the system is configured to take following actions, by default:

--   Assign a unique indentification id or *UID* to the user.
--   Create a home directory  `/home/`.
--   Set the default shell of the user to   `/bin/sh`.
--   Create a private group, named after the username of the new user and assign the user to the said group.
--   The contents of  `/etc/skel`  are copied to the home directory of the new user.
--   _.bashrc_,  _.bash_profile_  and  _.bash_logout_  are copied to the home directory of new user.
These files provide environment variables for this user’s session.

To create a new standard user, issue the command,
> **`useradd <name>`**

and replace `<name>` with the username of the user to be created.
Next, set the password for the newly created user using the command,
> **`passwd <name>`** 

Another method for creating users can be acheived by first installing a new package call **`adduser`**. 
The **`adduser`** command automatically creates a home directory and sets the default group, shell, etc.

For Debian/Ubuntu systems, execute the command,
> **`apt-get install adduser`**

to install the said package.

 Once the installation is complete, execute the command,
> **`adduser <name>`**

Upon issuing the above command, a series of prompts arise for feeding additional information pertaining to the newly created user, most of which is optional, except the password. 


### Deleting Existing User Accounts
In order to remove an existing user account from your Linux system, execute the commmand,
> **`userdel <name>`**

However, the above command only erases the existance of the said user from the system, without eliminating the associated files and directories.

To remove the user account, as well as the associated files and directories, run the command,
> **`userdel -r <name>`**



## Group Management in Linux

In Linux, a *group* is simply a collection/set of users. The main objective of having a utility like *groups* is to enable the users to define a set of privileges like read, write, or execute permission for a given resource that can be shared among the users within the group.

Primarily, groups are classified into two categories in Linux, *viz.,* *Primary Groups* & *Secondary Groups*.

### Primary Groups
When a new user is created, the system is configured to add it into a group by default, known as a *primary group*. This group is shares the same name as the said user and uniquely exists for every other user present in the system. 

The ID of the primary group of a particular user can be determined by running the command,
> **`cat /etc/passwd`**

From the output, the entry corresponding to the user in question, the fourth column represents the ID of the primary can be found.

Another method of attaining a user's primary group information is to issue the command,
> **`id <name>`**

By replacing the < name> with the user's username.

### Secondary Groups 
Once a user has been successfully created, they can be added into a group with other set of users. These types of groups are known as *secondary groups*. In Linux, the information associated with the existing *secondary groups* is stored in the **`/etc/group`** file.
 
 Issue the following commands to add a user(s) to a group(s):

>**`sudo usermod -a -G <groupName> <username>`** : To add a user with username as < username> to a singular group with the name of the group as < groupName>.
>
>**`sudo usermod -a -G <groupName_2>,<groupName_3>,<groupName_4> <username>`** : To add a user with username as < username> to multiple groups with the name of the groups as < groupName_2>, < groupName_3>, and < groupName_4>.

*Note that, in Linex, the system users are allowed to have 15 groups, at most and 0 groups, at least.* 

In order to list the groups an existing user is a part of, execute the command,
> **`groups <username>`**
