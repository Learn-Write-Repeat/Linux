# Environment Variables

Lets see how to set and list the environment variables in linux

In Linux based systems environment variables are a set of dynamic named values, 
stored within the system that are used by applications launched in shells or subshells. 
In simple words, an environment variable is a variable with a name and an associated value.

Environment variables allow you to customize how the system works and the behavior of the applications on the system.

## Environmenr Variables and Shell Variables

**Variable should have the following format:**

```
KEY=value
KEY="Some other value"
KEY=value1:value2
```

Some important Points to be noted
- The names of the variables are `case-sensitive`. By convention, environment variables should have `UPPER CASE` names.
- When assigning multiple values to the variable they must be separated by the colon `:` character.
- There is no space around the equals `=` symbol.

**Variables can be classified into two main categories:**

- environment variables
- shell variables.

**_`Environment variables`_** are variables that are available system-wide and are inherited by all spawned child processes and shells.

**_`Shell variables`_** are variables that apply only to the current shell instance. Each shell such as zsh and bash, has its own set of internal shell variables.

## Commands to set and list environment variables

- **_`env`_** 
   - The command allows you to run another program in a custom environment without modifying the current one. 
   - When used without an argument it will print a list of the current environment variables.
   
- **_`printenv`_** 
   - The command prints all or the specified environment variables.
   
- **_`set`_** 
   - The command sets or unsets shell variables. 
   - When used without an argument it will print a list of all variables including environment and shell variables, and shell functions.
   
- **_`unset`_** 
   - The command deletes shell and environment variables.
   
- **_`export`_** 
   - The command sets environment variables.

## List Environment Variables

The most used command to displays the environment variables is printenv. 
If the name of the variable is passed as an argument to the command, only the value of that variable is displayed. 
If no argument is specified, printenv prints a list of all environment variables, one variable per line.

**For example**, to display the value of the HOME environment variable you would run:

```
printenv HOME
```

The output will print the path of the currently logged in user:

```
/home/DevIncept
```

You can also pass more than one arguments to the printenv command:

```
printenv LANG PWD
```

```
en_US
/home/DevIncept
```

To show list of all env variables

```
printenv
```

**_Output_**

```
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35;...
LESSCLOSE=/usr/bin/lesspipe %s %s
LANG=en_US
S_COLORS=auto
XDG_SESSION_ID=5
USER=linuxize
PWD=/home/DevIncept
HOME=/home/DevIncept
SSH_CLIENT=192.168.121.1 34422 22
XDG_DATA_DIRS=/usr/local/share:/usr/share:/var/lib/snapd/desktop
SSH_TTY=/dev/pts/0
MAIL=/var/mail/DevIncept
TERM=xterm-256color
SHELL=/bin/bash
SHLVL=1
LANGUAGE=en_US:
LOGNAME=DevIncept
XDG_RUNTIME_DIR=/run/user/1000
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
LESSOPEN=| /usr/bin/lesspipe %s
_=/usr/bin/printenv
```

Some of the most common environment variables:

- **_`USER`_** - The current logged in user.
- **_`HOME`_** - The home directory of the current user.
- **_`EDITOR`_** - The default file editor to be used. This is the editor that will be used when you type edit in your terminal.
- **_`SHELL`_** - The path of the current user’s shell, such as bash or zsh.
- **_`LOGNAME`_** - The name of the current user.
- **_`PATH`_** - A list of directories to be searched when executing commands. When you run a command the system will search those directories in this order and use the first found executable.
- **_`LANG`_** - The current locales settings.
- **_`TERM`_** - The current terminal emulation.
- **_`MAIL`_** - Location of where the current user’s mail is stored.


## Setting Environment Variables

To create a new shell variable with the name MY_VAR and value Linuxize simply type:

```
MY_VAR='DevIncept'
```

You can verify that the variable is set by using either echo $MY_VAR of filtering the output of the set command with grep set | grep MY_VAR:


```
echo $MY_VAR
```

**Output**

```
DevIncept
```

## Persistent Environment Variables

To make Environment variables persistent you need to define those variables in the bash configuration files. 
In most Linux distributions when you start a new session, environment variables are read from the following files:


/etc/environment - Use this file to set up system-wide environment variables. Variables in this file are set in the following format:

```
FOO=bar
VAR_TEST="Test Var"
```

/etc/profile - Variables set in this file are loaded whenever a bash login shell is entered. When declaring environment variables in this file you need to use the export command:

```
export JAVA_HOME="/path/to/java/home"
export PATH=$PATH:$JAVA_HOME/bin
```
Per-user shell specific configuration files. For example, if you are using Bash, you can declare the variables in the ~/.bashrc:

```
export PATH="$HOME/bin:$PATH"
```

To load the new environment variables into the current shell session use the source command:

```
source ~/.bashrc
```

Therefore in this file we have learnt to set and list the environment variables.
