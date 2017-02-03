# installing and setting up chocolatey on win 10

## Pin Powershell to taskbar:

* type `Window+r`
* in the prompt type `powershell` and hit enter
* right click on the icon for powershell(seen below) and select "Pin to Taskbar"
 * add photo of icon

## Opening Powershell as admin:

* close the powershell you just opened using the command `exit`
 * type exit into powershell, hit enter, and it will close that application
 * this is handy to remember
* now right click on the icon you pinned to your task bar, and select "Run as Administrato"
 * this is necessary, as we'll be performing administrative tasks to get your computer ready for developing with ruby
 * you'll be prompted about whether you want to do this, select yes

## Setting execution policy for Powershell

* in powershell, type the following command (or copy and paste): `Set-ExecutionPolicy RemoteSigned`
  * Note: pasting in powershell is as simple as right clicking in the blue space of Powershell.
* press enter, and you may be asked to confirm the change you're making to execution policies. type `y` and press enter
* what we're doing, is allowing for the execution of signed powershell scripts to be performed on the system by us

## Chocolatey

Chocolatey is a powershell based package manager for windows, focused on making windows developers lives more simpler.
We'll be using it to install ruby, and the ruby DevKit.

If you'd like to read up on it more, this is the website for it https://chocolatey.org

## Installing Chocolatey:

* in the same powershell window we'll run: `iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex`
* this will prompt you for confirmation, at which you type `y`, and press enter
* once the command has finished, chocolatey will have been installed, and you can test it by running the following command:
 * `choco -v`
 * this should output `0.10.3`

## installing ruby and ruby-devkit:
* in the same powershell window, we'll run: `choco install git ruby ruby2.webkit`
* this will prompt you multiple times for confirmation, at each of them, type `y` and press enter
 * Note: you will see a separate window pop up during the installation of ruby2.webkit, this is normal, just let it run it's course
* once everything finishes installing, exit powershell, and we'll open another powershell as administrator
 * this is necessary, because there are some settings added during the install which only take effect once a new powershell is opened

## fixing ruby webkit:

* This step is only needed for windows 10
* we're going to type `cd C:\tools\DevKit2`, and hit enter
* then we'll type the command `ruby dk.rb init`, and hit enter
* then we're going you type `notepad.exe config.yml`
* in the notepad window which opens, paste the following content in, so that it's the only content in the file:
``` yaml
---
 - C:/tools/ruby23
```
* save the file and close it
* finally, we'll type the command `ruby dk.rb install`
* you'll need to close and reopen your powershell like before, because this is also modifying your some things to set up your computer to support ruby development.

## updating the existing gem installation

* Please follow along in the instructions provided at:
 * http://guides.rubygems.org/ssl-certificate-update/#installing-using-update-packages
 * Note: when they refer to your Command Prompt, please use your powershell as admin

