# Proxmox 

After doing some experimentation on my raspberry pi in terms of self hosting my own services and exposing one (Filebrowser) to the public, I am feeling confident enough to now use a spare laptop I have to create another HomeLab (with possible integration with my Raspberry Pi) using Proxmox as a Type 1 Hypervisor.

## What I'm planning to host 

1. Jellyfin Media Server 
2. Minecraft Server that friends can access 
3. SMB file sharing 
4. TrueNAS scale to act as mass cloud storage 

### Updates:

August 26: Successfully created new proxmox environment and used ansible to automate the installation of docker and deployment of Portainer to host docker containers.

August 28: 
- I have created a virtual machine that hosts my Jellyfin Media server and other future services using portainer
- Created a VM with open media vault to act as SMB file sharing and cloud storage rather than TrueNAS scale as I had an issue where the os got corrupted and I lost everything I set up initially
- Still working on the minecraft server (modded is too heavy of a load for my system so I will try a vanilla server and see how that goes)