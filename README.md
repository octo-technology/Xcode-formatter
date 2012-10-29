XCODE FORMATTER
================

![Why a code formatter](https://raw.github.com/octo-online/Xcode-formatter/master/images/why.png)

Xcode Formatter use [uncrustify](http://uncrustify.sourceforge.net/) to easily format your source code as your team want it to be!

Add a simple directory in your Xcode project to provide: 

* Xcode __shortcut-based code formatting__: use a shortcut to format modified sources in the current workspace
* __automatic code formatting__: add a build phase to your project to format current sources when application builds
* __all sources formatting__: format all your code with one command line
* __shared formatting rules by project__: edit and use a same configuration file with your project dev team


*****



1) How to setup the code formatter for your project
-----------------------------------------------------

### Install uncrustify

	$ brew install uncrustify

To install brew:
 
	$ ruby -e "$(curl -fsSkL raw.github.com/mxcl/homebrew/go)"


### Check that uncrustify is located in /usr/local/bin/ 

	$ which uncrustify


### Add CodeFormatter directory beside your .xcodeproj file

![CodeFormatter directory location](https://raw.github.com/octo-online/Xcode-formatter/master/images/directory_location.png)


### Check that your Xcode application is named "Xcode" (default name)

You can see this name in the Applications/ directory (or your custom Xcode installation directory). Be carefull if you have multiple instances of Xcode on your mac: ensure that project's one is actually named "Xcode"!

(Why this ? This name is used to find currently opened Xcode files. See CodeFormatter/Uncrustify\_opened\_Xcode\_sources.workflow appleScript).


### Install the automator service Uncrustify\_opened\_Xcode\_sources.workflow

Copy this file to your ~/Library/Services/ folder (create this folder if needed).

Be careful : by double-clicking this file, you will install it but the file will be removed ! Be sure to leave a copy of it for other users.




2) How to format opened files when building the project
---------------------------------------------------------

### Add a build phase "run script" containing the following line:

	sh CodeFormatter/scripts/formatOpenedSources.sh

![Add build phase](https://raw.github.com/octo-online/Xcode-formatter/master/images/add_build_phase.png)




3) How to format opened files with a shortcut
-----------------------------------------------

### Add a shortcut to the Uncrustify_opened_Xcode_sources service

Go to Xcode > Services > Services preferences :

![Create service shortcut](https://raw.github.com/octo-online/Xcode-formatter/master/images/add_service_shortcut.png)

And set your shortcut :

![Choose service shortcut](https://raw.github.com/octo-online/Xcode-formatter/master/images/choose_service_shortcut.png)




4) How to format files in command line
----------------------------------------

### To format currently opened files, use formatOpenedSources.sh: 

	$ sh CodeFormatter/scripts/formatOpenedSources.sh


### To format all files, use formatAllSources.sh:

	$ sh CodeFormatter/scripts/formatAllSources.sh PATH

PATH must be replaced by your sources path.



5) How to change formatter’s rules
------------------------------------

### Edit CodeFormatter/uncrustify\_objective\_c.cfg

You can use UniversalIndentGUI (http://universalindent.sourceforge.net/) to simplify edition.
