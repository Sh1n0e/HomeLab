# HomeLab
Created by: Shawn Rae

Purpose: Passion project of mine as well as a learning experience to gain a deeper understanding of how to work with docker and linux.

I will update this as it goes with what has recently been added, removed or updated.

08/03/25:
- Created Pihole image and have it operating when manually assigning a device with the address of the raspberry pi being used.

08/04/25:
- Made Filebrowser container with a manually mounted external hard drive

08/05/25:
- Attempted to auto mount the external hard drive on startup but its not working.
  - I tried fixing this by putting the drive intto the etc/fstab file but so far it is not working
  - Temporary solution: manually mount hard drive on start and refresh the container and I will have access to my data.