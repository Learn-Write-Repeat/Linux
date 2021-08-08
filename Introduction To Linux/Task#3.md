# Editors in Linux
A Linux system is capable of supporting multiple text editors, with each distro being shipped with multiple text editors pre-installed. They can be used for editing text files, writing codes, updating user instruction files, and more. 
The broad categorisation of the variety of text editors compatible on Linux OS is as follows: 
1. **Command-Line based** text editors such as Vi/Vim, Nano, Pico (traditional text editors) 
2. **GUI based** text editors such as gedit (for GNOME), KWrite (for KDE)

## Vim Editor
The Vim editor is a highly-configurable and powerful command-line based text editor that is capable of supporting most of the file types and can accomodate multiple plugins in accordance with the programmer's needs.
Vim's interface is not based on menus or icons but on commands given in a text user interface and can also serve as a standalone application in a graphical user interface.

One of the most distinctive features of Vim is its modularity. Before getting our hands dirty with Vim, we shall first dive into the various modes that the command-line based editor offers to the users.
While most text-editors offer a single mode of operation, Vim offers 7 different modes viz,
1. Normal Mode
By default, Vim starts in the normal mode and is characteristically used for single-character editing and content reviewing through navigation.
2. Visual Mode
Similar to the Normal Mode, but is mainly used for text-highlighting.
3. Select Mode

4. Insert Mode
Similar to the normally encountered editing mode in most modern editors, in the insert mode, buffers can be modified with the text inserted.
5. Command-line or Cmdline Mode
It supports a single line input at the bottom of the Vim window. Normal commands (beginning with :), and some other specific letters corresponding to different actions (including pattern search and the filter command) activate this mode.
7. Ex Mode
8. Terminal-Job Mode (New introduction in Vim8)

###  Installation
Most of the Linux distributions come pre-installed with Vi Editor (The OG Command-line editor of Unix based systems) and can be accessed by typing the `vi <filename>` command. On some POSIX disbutions, however, the `vi` command is a pointer to Vim.
To verify whether you have Vim already installed on your system, use the command: 
> **`which vi`**

If Vim is pre-installed on your system, it would return the **Vim binary** as the output:
> `/usr/bin/vim`

If the output is empty, follow along to install Vim Editor on your systems: 
- To install Vim on Debian based distros like Ubuntu, use the command:
> **`sudo apt-get install vim`**
- To install vim on an arch-based distro run the following command:
> **`sudo pacman -S vim`**

Finally run the `which vim` command to verify correct installation of Vim on your system.

### Getting Started With Vim
 
#### Creating your first file
To kickstart your experience with Vim, run the command `vim` followed by the file and extension of your choice: 
> **`vim testFile.txt`**

The editor would open in Normal Mode, by default.

#### Begin Editing Your File
Upon creating your file and opening it in the Vim Editor, press **`i`** key followed by **`ENTER`** key to switch to insert mode and start editing!

#### Navigating Your Way 
Instinctively, you may be driven to use the navigtion keys on your keyboard to move through the document while editing, but Vim offers keys with dedicated functions to help you in navigation more efficiently:
>   **`h`**  - move cursor left
>  **`j`**  - move cursor down
>   **`k`**  - move cursor up
>   **`I`**  - move cursor right
>   **`H`**  - move to top of screen
>  **`M`** - move to middle of screen
>  **`L`** - move to the bottom of the screen
>
> **`0`** - jump to the start of the line
> **`$`** - jump to the end of line
> **`gg`** - move to the first line of the document
> **`G`** - go to the last line of the document
> 
> **`fx`** - jump to the next occurence of the character 'x'
> **`Fx`** - jump to the previous occurence of the character 'x' 

#### Undo & Redo
Making mistakes is a part of the process. Undo and Redo accessibilities always come to our rescue to save us from blunderous mishaps!
Vim Editor too provides there functionalities:
> **`u`** - Undo (use while in Normal Mode)
> **`CTRL+R`** - Redo the latest action

#### Pattern Searching & Replacing
Vim offers various commands and functionalities to ease your process of creating textual pieces of art; directly searching for a pattern and being able to replace it instantly is one of them:
> **`/pattern`** - Search for the 'pattern' of text/code in your file
> **`?pattern`** - Search backward for your 'pattern'
>
>  **`:%s/old/new/g`**  - Replace all patterns denoted by 'old' with 'new' throughout file
>**`:%s/old/new/gc`** - Replace all patterns denoted by 'old' with 'new' throughout file with user confirmation

#### Saving & Exiting your file
The following set of commands can be used to save and/or exit your file in the Vim Editor, once done editing:
> **`:w`** - Save your file without exiting the editor
> **`:wq`** or **`:x`** or **`ZZ`** - Save your file and quit the editor
> **`:q`** - Directly quit the editor (fails to work if there are unsaved changes)
> **`:q!`** - Quit without saing the the recent changes
> **`:wqa`** - Exit all open windows **after** saving the recent changes 

#### Finding The Right Assistance
Not sure about what a command or specific keystroke is meant for? While in the Normal mode, just type the command **`:h[elp] keyword`** to open help for the entered keyword. 

---
*While we have offered an indepth overview of the various commonly employed commands and accessibilities that the Vim Editor has to offer, you can type the* **`:help`** *command while in Cmdline Mode to discover more about the fascinating tool of Vim Editor.*
