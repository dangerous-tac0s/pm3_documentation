# Mac OS X Setup

This guide was created using Mac OS X Big Sur. It is intended to be alongside <a href="" target="_blank">this video</a>. Set aside at least 30-minutes for this process. Actual time will vary based on system resources and your comfort level with command line interfaces.

> [!IMPORTANT]
> Lost, stuck, or just generally not figuring it out? Head over to the [forum](https://dngr.us/forum). Search the [support section](https://forum.dangerousthings.com/search?q=%23support%20)--someone likely encountered the same issue. If you don't find a solution, create a post in the support section. Reference or link to the step you're stuck on and let us know what operating system and version you're running. Screenshots and photos make helping you out easier.

### Overview
1. Prepare Development Environment
    * The Proxmark software is downloaded as source and compiled for specific platforms
2. Build and Install the Proxmark Software

### Steps
1. #### Development Environment
   * ##### 1a.
     
     Download and Install [Homebrew](https://brew.sh/) [^homebrew]
     
     ```bash
      /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```
    * ##### 1b.
      
      Use the following command to install the necessary packages:
      
      ```bash
       brew Install Git && brew install readline qt5 gd pkgconfig coreutils && brew install recode && brew install astyle
      ```

2. #### Proxmark
   * ##### 2a.
     
     Download the latest version of the Iceman fork of the Proxmark 3 software: [^git]
     
     ```bash
      git clone https://github.com/RfidResearchGroup/proxmark3.git
     ```

   * ##### 2b.
       
     After that finishes downloading: [^makefile]
     
     ```bash
      cd proxmark3 && cp Makefile.platform.sample Makefile.platform && nano Makefile.platform
     ```

   * ##### 2d.
      	In the notepad window that opens, make the following changes: [^makefile_edit]
    	- PLATFORM=PM3RDV4 to #PLATFORM=PM3RDV4
    	- #PLATFORM=PM3GENERIC to PLATFORM=PM3GENERIC
    
   * ##### 2e.

     Save the file and close nano.

   * ##### 2f.
  
     ```bash
      make clean && make -j8 all
     ```

   * ##### 2g. Plugin your Proxmark and Flash it

> [!IMPORTANT]
> With your Proxmark unplugged from your machine, press and hold the button on the Proxmark as you plug it into a USB port. You can release the button after plugging it in. Two of the four LEDs should stay on meaning it's in bootloader mode, ready for the next step. In case the two LEDs don’t stay on when you’re releasing the button, you’ve got an old bootloader, start over and keep the button pressed during the whole flashing procedure.
> 

   Enter the following commands with your ProxMark connected to the computer: [^flash]
      
```bash
  ./pm3-flash-bootrom
```

```bash
  ./pm3-flash-fullimage
```
       
[^homebrew]: Homebrew is a tool for downloading and installing software packages. If you want to know more about what the script you're downloading and executing to install it does, [read this](https://docs.brew.sh/Installation).
[^git]: Git is a version control system used primarily in software development. We're using it to get the latest version of the Proxmark software. The "clone" command is used when you haven't gotten something for the first time. When we update, we'll use "pull" to pull down the latest version. We'll still need to update the makefile, build, and flash again after that to finish the update.
[^makefile]: This puts us in the correct directory and selects the appropriate "makefile” for building the Proxmark software and then opens the text editor "nano" so we can make a change.
[^makefile_edit]: The "#" symbol is used to signify "comments." These are statements that are ignored--typically used for human readable notes but also for configuration changes like we are doing here. The default setting is to build software for the [Proxmark 3 RDV4](https://proxmark.com/proxmark-3-hardware/proxmark-3-rdv4) which is a much more expensive but higher performing device.
[^flash]: These command names are a bit misleading... The "bootrom" is the bootloader and the "fullimage" is the firmware. You need to run both of these.
