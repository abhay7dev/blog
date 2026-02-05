+++
title = "How to Build a Discord Bot in Node.js [WIP]"
date = "2026-02-05"
author = "Abhay"
cover = ""
tags = []
keywords = ["bots", "discord", "nodejs"]
description = ""
showFullContent = false
readingTime = false
hideComments = false
+++

# How to Build and Run a Simple Discord Bot in Node.js [WIP]

## Introduction
This blog post will describe, in proper detail, how to make a Discord Bot in 2026. 

### What is a Discord Bot?
A Discord Bot is an automated program which can be accessed via messages on the Discord platform. They can be thought of as special accounts within the platform that are controlled via code, not humans, and their functions and features are at the discretion of the developer.

### What will be taught?
Over the course of this blog post, the reader will learn about how to configure settings on discord and how to set up Node.js and VSCode in order to write code and run a Discord bot. This post does NOT cover deployment of bots, how to code in JavaScript (although there will be explanations of the code written), or how to further extend functionality.

### What are the prerequisites?
Readers are expected to:
* Have a working electronic device with the necessary permissions to install software.
* Have a Discord Account already made and logged into in their preferred Web Browser.
* Have an understanding of various technical terms.
* Have a mind that is excited to learn!
    * Take advantage of the giscus comment section under this blog post to ask questions!

This guide is targeted specifically towards those with MacOS, although links and/or commands will be provided for those on other operating systems (Windows, Linux).

## Instructions
### 1. Install Node.js and Visual Studio Code (VSCode)
1. Navigate to https://nodejs.org/en/download in your Web Browser
2. Follow the prompts and the instructions to install the latest LTS (Long-Term-Support) version of Node.js on your operating system(24.13.0 at the time of writing)
    * MacOS users with homebrew installed: `brew install node` installs node
3. Navigate to https://code.visualstudio.com/download in your Web Browser
4. Click the button to install the latest stable version of VSCode based on your Operating System and preferences
    * MacOS users with homebrew installed: `brew install --cask visual-studio-code` installs VSCode

### 2. Create a New Folder and Open it in VSCode

Create a new folder in your operating system file explorer or command line utility.
Click open in vscode

### 3. Create a JavaScript file and Install Required Dependencies

Now that you have gotten to this interface, right click the blank file explorer area and create a new file called index.js
Press control and backtick in order to open up the terminal in vscode (or go to file -> term ... (todo)). 
Run npm init -y to set up npm
then run npm install discord.js, dotenv

create a new file called .env

### 4. Configure Discord Developer Settings and Retrieve your Discord Bot Token

1. Navigate to https://discord.com/developers/applications in your Web Browser
    * If prompted to sign in, do so.
2. Click the "New Application" button, type in a name, accept Discord's policies, and then finally, click create.
![New Application Modal](/discordbot/create_app.png)
3. Grab the tokens and place it in the dot env

### 5. Write Code and Run the Discord Bot

Add the following code in index.js
go back to the terminal and run node index.js

### 6. Test the Discord Bot 

invite the bot to a discord server, i have cereated a test server. given that i assumed you knew about discord beforehand, i assumed you can create a server on your own
now navigate to a text channel, then do the /ping command.

## Conclusion
This blog post guided you readeres on how to make a very siimple discord bot. with further research, idea generation, and more, you can further expand utility and better suit bots for your needs, improving your QoL on the discord platform

## References
nodejs
vscode
discordjs