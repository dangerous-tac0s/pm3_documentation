# Windows Setup

> [!NOTE]
> This version of the setup guide is meant to get you up and going fast without overwhelming you with details. If you're the sort of person that wants to know in depth
> what's going on, [checkout this guide](https://forum.dangerousthings.com/t/getting-started-with-the-proxmark3-easy/9050).

This guide was created using Windows 11 but should work with any 64-bit version of Windows. It is intended to be alongside <a href="" target="_blank">this video</a>. Set aside at least 30-minutes for this process. Actual time will vary based on system resources and your comfort level with command line interfaces.

> [!IMPORTANT]
> Lost, stuck, or just generally not figuring it out? Head over to the [forum](https://dngr.us/forum). Search the [support section](https://forum.dangerousthings.com/search?q=%23support%20)--someone likely encountered the same issue. If you don't find a solution, create a post in the support section. Reference or link to the step you're stuck on and let us know what operating system and version you're running. Screenshots and photos make helping you out easier.


### Overview
1. Setup ProxSpace.
   - We need a special environment to build, install, and run the Proxmark software.
3. Build and install the Proxmark software.

### Steps
1. #### ProxSpace
   
	* ##### 1a.
      	Download and install <a href="https://www.win-rar.com/download.html?&L=0" target="_blank">WinRAR</a> [^1a_details]
	* ##### 1b.
      	Download [ProxSpace](https://github.com/Gator96100/ProxSpace/releases/latest/download/ProxSpace.7z) [^1b_details]
	* ##### 1c.
      	Extract the ProxSpace.7z file to: [^1c_details]
    	* **If there's only one user account on the computer**:  your home directory (eg: c:\users\johnsmith).
    	* **if there are many accounts on the computer:** c:\ (this will make it available to all users).
        	* **Suggested:** You can create a shortcut to your home directory.
            	```cmd
            	mklink /D ProxSpace c:\ProxSpace
            	```
            	It should be done for every user account that needs access to the Proxmark. Not necessary if you installed it to your home directory.
	* ##### 1d.
      	Press the windows key + r and type "cmd" in the "Open" field of the "Run" dialog and hit the "OK" button or the enter key to open the command prompt.


> [!IMPORTANT]
> The following assumes you either extracted to your home directory or linked the ProxSpace folder to it


2. #### Proxmark
	* ##### 2a.
      	Enter the following into the terminal to setup and start ProxSpace: [^2a_details]
    	```cmd
    	ProxSpace\runme64.bat
    	```
	* ##### 2b.
      	Download the latest version of the Iceman fork of the Proxmark 3 software: [^2b_details]
    	```bash
    	git clone https://github.com/RfidResearchGroup/proxmark3.git
    	```
	* ##### 2c.
      	After that finishes downloading: [^2c_details]
    	```bash
    	cd proxmark3 && cp Makefile.platform.sample Makefile.platform && notepad Makefile.platform
    	```
	* ##### 2d.
      	In the notepad window that opens, make the following changes: [^2d_details]
    	- PLATFORM=PM3RDV4 to #PLATFORM=PM3RDV4
    	- #PLATFORM=PM3GENERIC to PLATFORM=PM3GENERIC
	* ##### 2e.

       	Save the file and close Notepad.
	* ##### 2f.
    	In the terminal window enter the following to build the ProxMark software: [^2f_details]
    	```bash
    	make clean && make -j8 all
    	```
  	* ##### 2g.

     	Plugin the Proxmark.

	* ##### 2h.
 
      	Enter the following commands with your ProxMark connected to the computer: [^2h_details]
    	```bash
    	./pm3-flash-bootrom
    	```
 
    	```bash
    	./pm3-flash-fullimage
    	```
 
	* ##### 2 Optional
   	 
    	Run the following to automatically start the Proxmark 3 client when you start ProxSpace using "runme64.bat": [^2_optional_details]
    	```bash
    	echo proxmark3/pm3 >> ../.bashrc
    	```

## Congratulations!
You've finished setting up your Proxmark. If you did the last optional step, you should see this prompt:

<img src="../setup/images/proxmark_prompt.png" alt="isolated" width="750"/>

Which means you're ready to use your Proxmark.

If you see this:

<img src="../setup/images/proxspace_prompt.png" alt="isolated" width="750"/>

Enter this to connect to the Proxmark:
```bash
proxmark3/pm3
```

Which you'll need to do to use your Proxmark after entering Proxspace. If you want to avoid this step, [do this](WINDOWS.md#2-optional).

Want to get familiar with using the Proxmark? [Click here](../basics/PROXMARK_BASICS.md).

---

### [Back to Home](../README.md)

[^1a_details]: Windows can't uncompress 7z archives. WinRAR can.
[^1b_details]: This link points to the latest version of ProxSpace. If you're interested in learning more about ProxSpace, you can check [it's repository on GitHub](https://github.com/Gator96100/ProxSpace).
[^1c_details]: When you open the command prompt, it will start you in your home directory. If you extract ProxSpace there or link to it, it'll make your life easier because you won't have to change directories or reference a long path to use your Proxmark.

[^2a_details]: This will take a while. It will also be how you start ProxSpace to use your Proxmark after you've completed the setup. When we're using ProxSpace, we're using Bash which is the terminal (aka command prompt) commonly used in Linux. If you want to learn more about using Bash, [go here](https://www.freecodecamp.org/news/linux-command-line-bash-tutorial/).
[^2b_details]: Git is a version control system used primarily in software development. We're using it to get the latest version of the Proxmark software. The "clone" command is used when you haven't gotten something for the first time. When we update, we'll use "pull" to pull down the latest version. We'll still need to update the makefile, build, and flash again after that to finish the update.
[^2c_details]: This puts us in the correct directory and selects the appropriate "makefile” for building the Proxmark software and then opens Notepad so we can make a change.
[^2d_details]: The "#" symbol is used to signify "comments." These are statements that are ignored--typically used for human readable notes but also for configuration changes like we are doing here. The default setting is to build software for the [Proxmark 3 RDV4](https://proxmark.com/proxmark-3-hardware/proxmark-3-rdv4) which is a much more expensive but higher performing device.
[^2f_details]: This compiles the software to the specifications we've specified.
[^2h_details]: These command names are a bit misleading... The "bootrom" is the bootloader and the "fullimage" is the firmware. You need to run both of these.
[^2_optional_details]: This adds "proxmark3/pm3" to the end of the .bashrc file. That file controls some of Bash's behavior.
