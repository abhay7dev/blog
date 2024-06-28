+++
title = "Running Uptime Kuma on my old phone"
date = "2022-11-21"
author = "Abhay"
cover = ""
tags = []
keywords = ["uptime-kuma", "selfhosting", "termux", "cloudflare", "nodejs", "cloudflare-tunnels"]
description = "The process by which I set up uptime-kuma on termux in my old android phone along with cloudflare tunnels"
showFullContent = false
readingTime = true
hideComments = false
+++
# How I ran uptime-kuma on termux with cloudflare tunnels

The project [uptime-kuma](github.com/louislam/uptime-kuma) is the first ever piece of software I have self hosted. Previously, I was scared  of self hosting because...
1. I was not aware of what hardware requirements would be sufficient for my needs
2. What I even wanted to self host
3. Domain names and IP Addresses (I don't want to expose my home IP Address)

Through research, I found my answers
1. Literally any piece of hardware that can connect to the interne and has a reasonable cpu/memory and storage for my needs. I don't plan on doing anything crazy, so small devices would work just fine (such as the old android phones lying around and unused).
2. If I wanted to selfhost nextcloud, I would want to have a sufficient amount of storage space to do so. Hosting websites was stopped by problem number 3. However, when I made my website (https://abhay7.dev) using https://replit.com, which periodically switches off vm instances, I needed an http pinger to keep it up. As a result, I decided on uptime kuma, which was very simple to self host and served my purpose
3. I moved my website over to cloudflare and their service of tunnels helped solved all my issues, as all I needed was to install `cloudflared`, login, configure, and I would have my server running on localhost exposed to the web with its own seperate IP address.

## The setup

1. The first thing I did was delete everything off the device I was using to self host. Using `adb` allowed me to quickly debloat everything excluding the system apps and termux. Speaking of termux, that is what I am using as my terminal emulator for android. I did not need to root my phone. (Termux is available at https://github.com/termux/termux-app).
2. `pkg upgrade && pkg install openssh` No one wants to type a bunch of commands on a puny screen with an onscreen keyboard. I upgraded packages and installed openssh for a quick ssh server.`sshd`on termux to start the server. Can be killed with `pkill sshd`
3. From my laptop, `ssh my_termux_user@192.168.0.XXX -p 8022` Lands my straight into my terminal emulator. From here, my guide was [this github issue on uptime-kuma](https://github.com/louislam/uptime-kuma/issues/423) on how to host it on an android device.
4. `pkg install clang make python nodejs-lts binutils git` is all I need.
5. `git clone https://github.com/louislam/uptime-kuma.git && cd uptime-kuma` so that we actually get the software
6. `npm run setup` - This takes a while, as it compiles a customized version of sqlite, but it will work. After this is complete, you can test out the server by `node server/server.js`. The app by default runs on port `3001`, so navigating to `192.168.0.XXX:3001` yields the admin dashboard!
7. The next step was to install [`pm2`](https://pm2.io/). Simple as `npm i -g pm2`. `pm2 start server/server.js --name uptime-kuma` was all I needed to start the server. 
8. Now I needed to connect to cloudflare. I connected my domain to cloudflare by making an account, setting nameservers, etc. But now I needed to make a tunnel to my subdomain. For this, I followed [the command line tutoral](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/tunnel-guide/local/) on how to setup cloudflare tunnels.
9. 
	```bash
	pkg install cloudflared
	cloudflared tunnel login # Outputs a link to authorize cloudflared
	cloudflared tunnel uptime-kuma-tunnel
	cd ~/.cloudflared
	
	ls # look for the json file, copy the file name
	
	nano config.yml # add the following
	```
	
	```yaml
	url: http://localhost:3001
	tunnel: <Tunnel-UUID-From-Json-File>
	credentials-file: /root/.cloudflared/<Tunnel-UUID>.json
	```
	
	```
	# Finish with the following
	cloudflared tunnel route dns uptime-kuma-tunnel status.example.com
	
	cloudflared tunnel run # Run the tunnel
	```
	
	We can add this to pm2 by running
	`pm2 start "cloudflared tunnel run"`
	
The end result is uptime kuma running on our own device but available on the internet! Check out https://status.abhay7.dev for a working example :)
