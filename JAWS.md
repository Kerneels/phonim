# Background #

This solution enables the GVIM (GUI version of Vim with OLE support compiled in) on Windows to speak and produce Braille via the JAWS screen reader. I originally developed it to work on Windows XP with JAWS 8 but have tested it without modification and found that it works with the latest JAWS demo version I could find (14 beta) on Windows 7.

The solution consists of a _vimrc vim config file and a JAWS script file and some settings. The_vimrc vim config file sets gvim up so that JAWS can track the cursor that gvim draws. The JAWS script and config settings is where the real work happens.

The JAWS script does the following:
  * Initiate and maintain an OLE connection with gvim. The OLE interface to gvim is used to invoke vim script functions inside gvim and then receive the results back (i.e. ask gvim for the current line of text, ask gvim for the current cursor position).
  * Keep track of cursor position, vim editing mode (normal, visual, insert, command).
  * Interpret user keystrokes like vim would interpret them (i.e. Esc would always change to normal mode, inside normal mode pressing 'i' would enter insert mode etc.).


Although this solution is very primitive and lacking in many ways, you can use this to edit files in gvim quite nicely. There is the odd occasion where the OLE linkup goes wrong and you have to restart JAWS, but overall I found this solution stable and workable.


# Quick Start #

  1. Download and setup JAWS and GVIM. Make sure you get the gvim version with OLE support compiled in. At the time of this writing, the following link would give you the right download: [gvim73\_46.exe [ftp://ftp.vim.org/pub/vim/pc/gvim73_46.exe](ftp://ftp.vim.org/pub/vim/pc/gvim73_46.exe)] or visit http://www.vim.org/download.php and download the latest Windows version, and for JAWS go to: http://www.freedomscientific.com/downloads/jaws/jaws-downloads.asp and download the latest version. # Download and extract phonim-jaws.zip from the downloads area of the phonim project.
  1. Copy all the gvim. files from the unpacked zip file into where your JAWS scripts would reside normally. On my system this is at C:\Users\All Users\Freedom Scientific\JAWS\14.0\SETTINGS\enu, or if you just want to install it for your user find the similar directory structure in your user home directory.
  1. Copy the _vimrc vim config file to where your gvim is installed. On my system this is atC:\Program Files (x86)\Vim.
  1. Run JAWS and then start GVIM or open a familiar code file with GVIM._

# Usage #

  * While in normal mode (nothing is displayed bottom left corner) you can press the 'j' and 'k' keys to move one line down and up respectively. Notice how JAWS reads the whole line when the cursor changes to a new line.
  * While on a line of text and in normal mode, use the 'w' key to move forward by one word. Notice how JAWS reads the current word when moving by word ('w'), and reads each character when moving by character ('h', 'l').
  * Whenever the cursor moves, be it from the arrow keys or the movement commands or even a search forward or backward, JAWS will read something.

## Known Issues ##

This is a list of known issues with this solution. When it becomes too big I'll put it into a separate page.

### Only One GVIM Instance Allowed ###

Since I make use of the gvim OLE interface inside the JAWS script I can't open
more than one gvim instance. Well you can open many gvim instances but
the JAWS script will look at the first one you opened since that's where
the OLE linkup happened.

The way around this is simply opening multiple files in one gvim
instance, which is what you want to do 90% of the time anyways.

It would be great if the script could be altered so that multiple OLE linkups could be accomodated in order to have as many gvim instances open as you like.

### No, or limited Reading of the Command Line Area ###

> When you issue the ':' character while inside normal mode in vim you enter command mode. The cursor is now placed at the bottom of the screen and you can type longer commands with their arguments. Once you press enter the command will be executed.

Since the shape of the cursor changes when entering command mode and because I do not know how to query the contents of the command line via vim script (via the GVIM OLE interface) I was not able to make this area read properly. One can of course use flat review mode with the JAWS cursor to read what has been typed or printed here.

It would be great to have JAWS also read this area properly.

### JAWS 40 Minute Demo Mode ... Yeah Right! ###

If you don't own JAWS then you will have to run it in the 40 minute demo mode. Yes, you heard right, 40 minutes only and then you have to reboot. Good luck with trying to do anything meaningful in 40 minutes!

However, if you want to assist with this project I will gladly approach Freedom Scientific, the makers of JAWS and ask them for some sort of developer license for you that will be active for the duration of your involvement with the project.