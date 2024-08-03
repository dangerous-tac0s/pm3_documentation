# Windows Setup
This guide was created using Windows 11 but should work with any 64-bit version of Windows. Set aside at 30-minutes for this process. Actual time will vary based on system resources and your comfort level with command line interfaces.

### Overview
You'll need to install a special environment (ProxSpace) to run the Proxmark client in. It's compressed with a special format that isn't supported by default by Windows so you'll need to install WinRar.  After installing those, you can get the latest version of the Proxmark 3 software, build it from the source you download, flash it to the Proxmark device, and finally setup the client. 

### Steps
1. Download and install [WinRar](https://www.win-rar.com/download.html?&L=0)
2. Download [ProxSpace](https://github.com/Gator96100/ProxSpace/releases/latest/download/ProxSpace.7z)
	- This link will download the relevant, latest available file.
3. Extract the ProxSpace.7z file to:
	- Your home directory, ***if there's only one user account*** on the computer you're installing it on.
	- c:\ ***if there are many accounts*** (this will make it available to all users.
		- Suggested but Optional: You can create a shortcuts to your home directory:
			```cmd
			mklink /D ProxSpace c:\ProxSpace
			```
			This will allow easy access to the ProxSpace directory. Not necessary if you installed to your home directory.
4. Press the windows key + r and type "cmd" in the "Open" field of the run dialog and hit the "OK" button or the enter key.


> [!IMPORTANT]
> The following assumes you either extracted to your home directory or linked the ProxSpace folder to it


5. Enter the following into the terminal to setup and start ProxSpace:
	```cmd
	ProxSpace\runme64.bat
	```
6. Download the latest version of the Iceman fork of the Proxmark 3 software:
	```bash
	git clone https://github.com/RfidResearchGroup/proxmark3.git
	```
7. After that finishes downloading:
	```bash
	cd proxmark3 && cp Makefile.platform.sample Makefile.platform && notepad Makefile.platform
	```
8. In the notepad window that opens, make the following changes:
	- PLATFORM=PM3RDV4 to #PLATFORM=PM3RDV4
	- #PLATFORM=PM3GENERIC to PLATFORM=PM3GENERIC
9. Save the file and close Notepad.
10. In the terminal window enter the following to build the ProxMark software:
	```bash
	make clean && make -j8 all
	```
11. Enter the following commands with your ProxMark connected to the computer:
	```bash
	./pm3-flash-bootrom
	```
	```bash
	./pm3-flash-fullimage
	```
- Optional: Run the following to automatically start the Proxmark 3 client when you start ProxSpace using "runme64.bat":
  ```bash
  echo proxmark3/pm3 >> ../.bashrc
  ```

## Congratulations!
You've finished setting up your Proxmark. If you did the last optional step, you should see this prompt:

TODO: add image

if you see this:

TODO: add image

Enter "pm3" to connect to the Proxmark.
