# red5pro-installer
Installer for Red5 Pro Server


## INTRODUCTION
---

The Red5pro install is a shell script, designed to make Red5pro installation simple and more efficient by automating most of the tasks related to getting a new Red5pro installation running.

The script presents a collection menu driven options to help achieve various red5pro setup tasks. Additionally it also takes care of installing the software depencencies required to get Red5pro working. The script in intended to work on supported linux flavors and mac.



## REQUIREMENTS
---

This script is 'currently' designed to work with linux systems. You need to have a linux distribution supported by 'Red5Pro' (ex: ubuntu, centos).

The script requires super user privileges to execute and carry out subtasks. Hence you must execute the script as a super user on your linux system (sudo...).


## USAGE
---

**To execute the script :** 
>> Script is located at : `Linux/rpro-utils.sh`
* Copy the script and conf.ini (script configuration file) to a location from where it can be executed such as : `/home/{username}/`.
* Navigate to directory location in the linux terminal (shell)
* Assign executable permissions to the script by issuing the following command in terminal : `sudo chmod +x ./rpro-utils.sh`

---

##### UBUNTU

* Execute the script by issuing the following command : `sudo ./rpro-utils.sh`

##### CENTOS

* Execute the script by issuing the following command : `sudo  bash./rpro-utils.sh`

>> Use the menu driven interface sequentially and follow instructiosn carefully for best results.

---

## PROGRAM OPTIONS
===

### INITIALIZTION

As the script runs in the terminal, it detects the operating system details such as Distribution (OS name), Version (OS version), Kernel type (64/32 bit), User's hoem directory, Red5pro default backup directory (located inside the home directory) and the default install location (the current directory).

The detected information is printed on screen an d then the menu which allows you to select a operation mode is rendered. The program supports two modes of operation : 

* Basic Mode: Provides most of the options for new installations.
* Advance Mode: Provides advance options for managing a existing red5pro installation.


![Main Menu](Linux/images/main_menu.png?raw=true "Main Menu")


__You can select a menu option by typing the number that represents that option and pressing [ ENTER ]__


===


### BASIC MODE


The basic mode provides all the options, commonly required to setup a new red5pro installation and other operatison such as starting / stopping red5.  Thew basic menu option allows you to:


![Basic Mode](Linux/images/basic_mode.png?raw=true "Basic Mode")



#### 1. INSTALL LATEST RED5PRO


Allows you to install Red5pro from red5pro.com website. You must have an existing account on red5pro.com to use this option. Before proceesding, the script checks for a few basic requirements : 

* Java : Java (JRE / JDK 1.8 or greater is required to install Red5pro)
* unzip : Unzip utility is required to unpack zip archives.

Depending on whether the softwares are found in the os distribution, the script helps you install them using the platform specific installation method. (ie: Ubuntu uses apt-get, where as CentOS uses yum to install softwares. )

Once the requirements are met the script proceeds to 'obtaining the latest Red5pro from Red5pro.com'. At this point, it prompts you for site credentials (email  & password). This information is posted to the website to help authenticate your download. If authentication succeeds, it begins downloading the latest red5pro archive file from red5pro.com. 


__* If an existing script is found, the script tried to stop red5 in case it was running before it can continue.__

__* If there is an existing red5pro installation found at the location, the files wil be backed up to the default backup location__


Once the download completes, the program extracts the archive file's content and copies the red5pro files into the install location. It prompts for a confirmation before starting the install.

The script prompts to determine if a autostart service is required for the red5pro installation. If user selects 'yes', The program creates a linux startup script for the current OS platform. Thsi script helsp red5pro start automatically with operating system startup.


#### 2. INSTALL RED5PRO FROM ZIP

This option lets you install Red5pro from a pre downlaoded zip. In case you have a older Red5pro that you wish to install or if you do not want to have the program download the latest red5pro for you.

The script checks the basic red5pro requirements as with the first option (INSTALL LATEST RED5PRO). Once requiremenst are met, it prommpts you for the full absolute path of the red5pro zip file. 

__The archive should have been downloaded from red5pro.com. Using a archive from a different source will not work__

The program extracts the archive file's content and copies the red5pro files into the install location. The rest of the process is exactly the same as for the first option (INSTALL LATEST RED5PRO).



#### 3. REMOVE RED5PRO INSTALLATION

This option lets you remove an existing red5pro installation. Removal deletes all the files and removes red5pro startup script if it exists.

On selection of this option, the program loosk for existing red5pro installation in the install location. If an installation is found, the user will be prompted to confirm the removal action. If user confirms it (by pressing Y + [ ENTER ] ), the script deletes the red5pro installation as well as any red5pro service installed on the OS.




#### 4. ADD / UPDATE RED5PRO LICENSE

This option navigates to a sub-menu which allows us to view, install and update a red5pro license.

![License Menu](Linux/images/license_menu.png?raw=true "License Menu")


__1. ADD / UPDATE LICENSE :__  Provides option to add a new license or update one if it already exists. The program looks for an existing red5pro installation and then the LICENSE.KEY file at expected location. If a file is found it allows you to enter a red5pro license code from the terminal interface.

__2. VIEW LICENSE :__  Provides option to view an existing red5pro license via the LICENSE.KEY file. The program looks for an existing red5pro installation and then the LICENSE.KEY file at expected location. If a file is found it displays the content of the file on terminal.



#### 5. START RED5PRO

This option allows you to start Red5pro. On selecting this option, the program first checks to see if a Red5pro service is installed on the system or not. If a red5pro service is found, it attempts to start red5 usign the service. If no service is found it attempts to start red5 using 'red5.sh' script located at the red5 install location.

__The program doe snot check the running state of red5pro. If it is started, starting it again will have no effect._

__NOTE: This does not check to see if you have installed red5pro or not. It is assumed that you have a valid red5pro instalaltion before attempting to start it.


#### 6. STOP RED5PRO

This option allows you to stop Red5pro. On selecting this option, the program first checks to see if a Red5pro service is installed on the system or not. If a red5pro service is found, it attempts to stop red5 usign the service. If no service is found it attempts to stop red5 using 'red5.sh' script located at the red5 install location.

__The program doe snot check the running state of red5pro. If it is stopped, stopping it again will have no effect._

__NOTE: This does not check to see if you have installed red5pro or not. It is assumed that you have a valid red5pro instalaltion before attempting to stop it.



===


### ADVANCE MODE


TO DO


![Advance Mode](Linux/images/advance_mode.png?raw=true "Advance Mode")



#### 1. WHICH JAVA AM I USING ?

Selecting this option lets you see the current java version on your system. If java is not found, the program will print a message to notify the same.


#### 2. INSTALL RED5PRO SERVICE

This option lets you install red5 service. On selecting this option, the program first checks to see if red5pro in installed. If red5pro is not installed the operation exits. If red5pro installation is found the program attempts to register it as a service. If red5pro service is already installed on the OS, it prompts the user to overwrite it. If user selects to overwrite (By selecting 'y' + ENTER), the service will be re-installed else the operation exists.


#### 3. UNINSTALL RED5PRO SERVICE

This option lets you uninstall red5 service. On selecting this option, the program first checks to see if red5pro in installed. Next it shecks to see if service is installed. If red5pro is not installed the operation exits. If red5pro installation is found the program attempts to unregister it as a service. If red5pro service does not exist on the OS, the operation exits. If service is found it is removed.


#### 4. UPGRADE RED5PRO FROM LATEST

The upgrade option allows you to install the latest red5pro over an existing installation. Although this is fairly a complex process, the program simplifies it for the user by providing step by step onscreen instructions.


Selecting this option, the program checks for an existing red5pro installation. If an existing installation is not found the operation exits.If an installation is found at install location, the program will create a backup of the existing red5pro instalaltion into the default red5pro backup location automatically before installing the new copy. 

The program prompts the user for confirmation to follow through. On confirmation, it creates a backup of existing red5pro instalaltion and displays the path of the backup location.

The program then follows through the new red5pro instalaltion by downloading the latets red5pro from red5pro.com. (__Similar to Basic Mode -> Install Latest Red5pro__) .  

After the installation is complete the program prompts the user for optional restoration help. If the user accepts, the program switches to restore wizard. If user does not accept the operation exists.

The restore wizard helps the user restore some of the common items that can be restored such as :

* License - RED5_HOME/LICENSE.KEY
* Cluster configuration - RED5_HOME/webapps/root/red5-default.xml
* Web applications - RED5_HOME/webapps/*

The restore wizard prompts the user for each restoreable item. If user accepts the item is automatically restored from the backup into the new installation. If the user rejects the wizard skosp that item. Restoration can be re-done anytime manually as well. At the end of the wizard the operation exits automatically.
