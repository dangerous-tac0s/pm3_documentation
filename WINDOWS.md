# Windows Setup
This guide was created using Windows 11 but should work with any 64-bit version of Windows. It is intended to be alongside [this video](). Set aside at least 30-minutes for this process. Actual time will vary based on system resources and your comfort level with command line interfaces.

Have a suggestion? Contact [me](operations@dangerousthings.com) or open a PR.


> [!NOTE]
> Lost, stuck, or just generally not figuring it out? Head over to the [forum](dngr.us/forum). Search the [support section](https://forum.dangerousthings.com/search?q=%23support%20)--someone likely encountered the same issue. If you don't find a solution, create a post in the support section. Reference or link to the step you're stuck on and let us know what operating system and version you're running. Screenshots and photos make helping you out easier.


### Overview
1. Setup ProxSpace. 
2. Build and install the Proxmark software.

### Steps
1. #### ProxSpace
   
	* ##### 1a. 
  		Download and install [WinRar](https://www.win-rar.com/download.html?&L=0) [^1a_details]
	* ##### 1b.
  		Download [ProxSpace](https://github.com/Gator96100/ProxSpace/releases/latest/download/ProxSpace.7z) [^1b_details]
	* ##### 1c.
  		Extract the ProxSpace.7z file to: [^1c_details]
		* **If there's only one user account on the computer**:  your home directory (eg: c:\users\johnsmith).
		* **if there are many accounts on the computer:** c:\ (this will make it available to all users).
			* **Suggested:** You can create a shortcuts to your home directory: [^1_suggested_details]
				```cmd
				mklink /D ProxSpace c:\ProxSpace
				```
				This will allow easy access to the ProxSpace directory. It should be done for every user account that needs access to the Proxmark. Not necessary if you installed to your home directory.
	* ##### 1d.
  		Press the windows key + r and type "cmd" in the "Open" field of the run dialog and hit the "OK" button or the enter key. [^1d_details]


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
	* 2e.

   		Save the file and close Notepad.
	* ##### 2f.
		In the terminal window enter the following to build the ProxMark software: [^2f_details]
		```bash
		make clean && make -j8 all
		```
	* ##### 2g.
 
  		Enter the following commands with your ProxMark connected to the computer: [^2g_details]
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

TODO: add image

if you see this:

TODO: add image

Enter "pm3" to connect to the Proxmark.

Want to get familiar with using the Proxmark? [Click here](PROXMARK_BASICS.md).

---

### Details

[^1a_details]: 1a: TODO
[^1b_details]: 1b: TODO
[^1c_details]: 1c: TODO
[^1_suggested_details]: 1 Suggested: TODO
[^1d_details]: 1d: TODO

[^2a_details]: 2a: TODO
[^2b_details]: 2b: TODO
[^2c_details]: 2c: TODO
[^2d_details]: 2d: TODO
[^2f_details]: 2f: TODO
[^2g_details]: 2g: TODO
[^2_optional_details]: 2 Optional: TODO
