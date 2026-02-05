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

### 2. Create a New Folder and open it in VSCode

1. 