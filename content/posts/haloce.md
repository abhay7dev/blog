+++
title = "How to install Halo Custom Edition on Windows"
date = "2022-12-20"
author = "Abhay"
cover = ""
tags = []
keywords = ["game", "halo", "windows", "haloce", "modern"]
description = "A modern guide describing how to install Halo Custom Edition on Windows"
showFullContent = false
readingTime = true
hideComments = false
+++
# How to install Halo: Custom Edition (Windows)

This blog post is a guide on how to install Halo: Custom Edition. The steps have been tested on Windows 10 but it should however, work for Windows 11.

Note: This is **Custom Edition**, **NOT** *Combat Evolved*. This means that by default, you will be *unable to play any of the original campain* by default. Custom maps as well as regular multiplayer are both available on Custom Edition.

## Part 1 - Base Game

### 1 - Acquire a CD Key

Halo: Combat Evolved PC was originally distributed through CDs. The box for the CD would have an alphanumeric 16 character long string split into 4 groups with a `-`. After the CD was inserted and the installer was started, it prompted for a CD Key to install. Luckily for us, these **CD keys are reusable**.

I will not post CD Keys here, however, they are really easy to find. Just **search up "Halo PC CD Key" and look around** a bit (The images tab is your friend).

### 2 - Install the Game

For this step, you will need to download some executables and install the game.

* [Halo Custom Edition Game [English]](https://www.halomaps.org/hce/detail.cfm?fid=410)
* [Halo Custom Edition Patch V1.0.10](https://www.halomaps.org/hce/detail.cfm?fid=6798)

After download, simply unzip both these zip files.
First, you should run the game installer. At this step, you will be prompted to enter the CD Key which you found in step 1. Eventually, you will reach a spot where it has 3 check marks with various install options. Importantly however, you **must uncheck "Install GameSpy Arcade"**. These are the old servers for combat evolved and are unusable.
After finishing the install, now double click the 1.0.10 executable to update Halo: Custom Edition to the latest version which allows for online play.

### 3 - Install the Dependencies

Various libraries and dependencies are required to run Halo: Custom Edition. They are listed below.

**All these dependencies are available in the *`redist`* folder in your Halo: CE download location**. These are available at your convinience and all required dependencies can be installed from this location. However, be aware that these are more than likely **outdated** with security vulnerabilities. It is highly recommended you follow the guide below. Additionally, the Visual C++ Redistributable **is not included** and most be installed from the below link if not already installed

* DirectX - Microsoft's graphics library
	- If you already play games, you more than likely have this installed already.
	- In the Windows Start menu, run `dxdiag` to see if you have DirectX installed and its version. Halo requires version 9, but the latest version is 12, which I recommend upgrading to if you have not already
	- According to Microsoft, DirectX Updates should be distributed through Windows updates. However, you can attempt to directly install libraries at [Microsoft's  DirectX End-User Runtime Web Installer](https://www.microsoft.com/en-us/download/details.aspx?id=35).
	- The **latest and recommended version is *12***
* MSXML - Microsoft XML Services
	- This library is used for the chat in game
	- The version used is *MSXML 4.0 Service Pack 3*
	- Microsoft has removed their download, but it is still available on the internet archive. [MSXML 4.0 Service Pack 3 on the Internet Archive (taken in 2020)](https://web.archive.org/web/20200803220857/https://www.microsoft.com/en-US/Download/confirmation.aspx?id=15697)

* Microsoft Visual C++ Redistributable - Various Components
	- This can be installed directly from Microsoft's page: https://learn.microsoft.com/en-US/cpp/windows/latest-supported-vc-redist?view=msvc-170.
	- Specifically, we want the **Visual Studio 2010 (VC++ 10.0) SP1**
	- Make sure to get the **32 Bit Version** as Halo is a 32 Bit application
	- You can get it directly [at this microsoft download link](https://download.microsoft.com/download/1/6/5/165255E7-1014-4D0A-B094-B6A430A6BFFC/vcredist_x86.exe).
	
### 4 - Finishing Up and Run!
At this point, Halo: Custom Edition should be installed as normal and should be playable.
Be aware that Halo: CE must be run **with admin permissions**. This permission must be given every time. I am not sure why it requests these permissions, but in my time playing, nothing bad has ever happened to my computer as a result of it.
Simply click Halo: Custom Edition in the Windows State Menu to begin.
I **HIGHLY RECOMMEND** immediately tweaking settings for the game in the Settings menu. You will want to set a frame rate and resolution for the game. There are various other settings to be changed, so make sure to look through all of them.
## Part 2 - Additions and Addons
The following section provides guides for highly recommended addons for the game. These help with graphics, Quality-of-Life improvements, and other overall management.
### Installing Mercury - The Halo Custom Edition Package Manager 
Mercury provides an easy way to manage and install various Halo: CE addons. It is a command line application that will run and install various packages. It is [open source](https://github.com/Sledmine/mercury) and developed by [Sledmine](https://github.com/Sledmine) and the [ShadowMods team](https://shadowmods.net/).
It is important to note that this application must **always be run with admin permissions**.
1. Simply navigate to the [project's releases page](https://github.com/Sledmine/mercury/releases) and download and install the latest version. This application is completely seperate from Halo: CE, so you may install either the 64 bit or 32 bit version. Both will operate the same.
2. Simply double click the installer to install Mercury
3. Using Mercury can be done in one of two ways. Either use the desktop shortcut automatically created at install time OR open a command prompt as an administrator and run Mercury from there
4. To explore Mercury more, simply navigate to [it's official website](https://mercury.shadowmods.net/).

Reference: https://mercury.shadowmods.net/docs/getting-started

### Installing Chimera
Chimera describes itself as "the update to Halo: Combat Evolved for the PC that we should have had but never got". Chimera provides a multitude of passive and togglable features meant for the modern era of computers.
It is open source and available at [SnowyMouse's Github](https://github.com/SnowyMouse/chimera).
1. Installing is very simple. Simply open an admin command prompt and run `mercury install chimera` and let mercury do all the work for you!

### Installing the Universal UI
Halo Custom Edition was created for custom maps. Maps are loaded through the `map_name` command while in game. The Universal UI was created in order to provide an easy visual catalog of all the popular custom maps that were in rotation. It is still a viable option today and my recommended User Interface Changer.
1. Simply open an admin command prompt and run `mercury install uui` and the Universal UI will automatically be added

### Installing the original Halo: Combat Evolved Campaign
As stated at the beginning, the original Halo PC Campain is not installed by default in Halo: Custom Edition. These can however be installed manually.
1. Return to http://hce.halomaps.org in order to download the campaign files. Links to all levels will be found at the bottom of this section
2. Unzip each and every downloaded file. The should have names like `a10` or `c40`. These files are the original maps for the campaign patched to run on Halo: Custom Edition
3. Copy all the map files to the `maps` folder in your Halo: Custom Edition install location. By default, this would be `C:\Program Files (x86)\Microsoft Games\Halo Custom Edition\maps`. If you properly installed Halo: Custom Edition earlier, you should already see multiplayer maps. Copy all the downloaded campaign map files into this maps subfolder in the main directory.
4. After copying all these files, simply open up the game, and navigate through the Campaign section of the universal ui to reach the section for Bungie's original campaign and play as Masterchief and discover the secrets of the ring.

Links:
* All files    - http://hce.halomaps.org/index.cfm?search=renamon
	- Level 1  - [Pillar of Autumn](https://www.halomaps.org/hce/detail.cfm?fid=1681) (a10)
	- Level 2  - [Halo](https://www.halomaps.org/hce/detail.cfm?fid=1678) (a30)
	- Level 3  - [Truth and Reconciliation](https://www.halomaps.org/hce/detail.cfm?fid=1682) (a50)
	- Level 4  - [The Silent Cartographer](https://www.halomaps.org/hce/detail.cfm?fid=1701) (b30)
	- Level 5  - [Assault on the Control Room](https://www.halomaps.org/hce/detail.cfm?fid=1702) (b40)
	- Level 6  - [343 Guilty Spark](https://www.halomaps.org/hce/detail.cfm?fid=1718) (c10)
	- Level 7  - [The Library](https://www.halomaps.org/hce/detail.cfm?fid=1719) (c20)
	- Level 8  - [Two Betrayals](https://www.halomaps.org/hce/detail.cfm?fid=1711) (c40)
	- Level 9  - [Keyes](https://www.halomaps.org/hce/detail.cfm?fid=1712) (d20)
	- Level 10 - [The Maw](https://www.halomaps.org/hce/detail.cfm?fid=1720) (d40)

### Installing CEnshine
In the PC Port of Halo: Combat Evolved frmo the xbox, the shaders and graphics were altered and a worsening way. Sledmine's CEnshine aims to replicate the Xbox's original textures as much as possible
1. Installing it is simply `mercury install censhine` in an admin command prompt.

### Installing optic medals
Another project from the ShadowMods team, optic introduces the medals which are found in later Halo Titles for kills in game.
1. Optic required the installation of [harmony](https://github.com/MangoFizz/harmony), an extension of Chimera's builtin scripting API to include more features. Simply install with `mercury install harmony`
2. Now we can run `mercury install optic` and we should now get kill medals in our multiplayer games!

## Part 3 - Fun Stuff and Things to watch
The following is various projects and other Halo: Custom Edition related things to look into if you are interested

* [SPV3](https://www.moddb.com/mods/spv3-for-halo-ce) - Arguably the most well-known mod in the Halo Franchise. A complete overhaul of the original campaign with new weapons, enemies, mechanics, and more! Installing this is a seperate hurdle so if you are interested, do your own research!
* Literally any of the ShadowMods' and Sledmine's other projects. Notable ones include
	- [Coop Evolved](https://github.com/Sledmine/coop-evolved) - This project allows for the campaign to be played cooperatively
	- [Insurrection](https://insurrectionce.com/) - A modern and complete overhaul of Halo: Custom Edition's User Interface while most notably, adding an easy way for friends to play multiplayer together easily and for Free
* [Project Lumoria Campaign](https://www.halomaps.org/hce/detail.cfm?fid=6507) - A complete custom campaign. Various new encounters and more. Maps have been made from the ground up. A very fun and new experience
* [www.halomaps.org](https://www.halomaps.org) - This site is what we have been using for a good part of this tutorial. It is the largest catalog of custom Halo maps on the internet and has been around for a very long time.
* [CE3](https://haloce3.com) - CE3 is another catalog for various maps
* [OpenSauce](https://www.nexusmods.com/halo/mods/7/) - OpenSauce allows for the usage of `.yelo` maps which are essentially `.map` files with greater functionality. This has been used by various custom maps.
* [HAC2](http://devieth.halonet.net/) - Halo Anticheat 2 is an addon similar to OpenSauce and Chimera, adding various new features to the game. - Original Site is down, I am not sure if this works: http://hac2.halopc.com/index.html
* [OpenCarnage](https://opencarnage.net/) - OpenCarnage is a forum for Halo CE.
* [HaloSpawns](https://www.halospawns.com/) - HaloSpawns allows you to learn the spawns of each multiplayer map in Halo CE. This website includes a WebGL based map explorer letting you view each map in your web browser!

## Conclusion

This guide has served as very useful documentation for me and hopefully for you to. If you found this helpful, feel free to share this post.
:)
