# Minecraft Server Setup

This will be a short guide on how I've set up Minecraft Servers on many different Linux machines. My current server box is running Debian 11 so all the commands here will be using apt and geared towards Debian-based systems, however replacing apt with the distro-specific package manager would be the only change needed to transport this to Arch or other systems.  
</br>

## Prerequisites

Before anything, ensure your databases are up to date and the most current version of JRE (Java Runtime Environment) is installed.

```
sudo apt update && sudo apt upgrade
sudo apt install openjdk-17-jre
```
</br>

## Server User and Directory

I always create a separate user to run each of my games from, especially on systems running multiple servers at once 
```
sudo useradd minecraft
```

Create a directory to store all of the server files. I prefer to make it in `/opt`, however this directory could be anywhere you like. The `/opt` directory does require root privilleges to operate in, so if operating here make sure your game user has `sudo` privilleges.   
```
sudo mkdir /opt/minecraft
``` 
</br>

## Instal and Create Server Files

Go and grab the latest server binary from the Minecraft website. The link below is the most up to date file as of writing, however this will inevitably change in the future as future updates are released.
```
wget https://launcher.mojang.com/v1/objects/125e5adf40c659fd3bce3e66e67a16bb49ecc1b9/server.jar
```
Create a `run.sh` file to make starting the server easier. I've also attached my version of this file in this repo.
``` 
#!/bin/sh

java -Xms1024M -Xmx4096M -jar server.jar
```
Note the `-Xms####` and `-Xmx####` flags. This is the minimum and maximum amount of RAM the server will be allowed to use respectively. My server has 16gb of RAM and runs a couple different games at once, so here I allow Minecraft up to 4gb.