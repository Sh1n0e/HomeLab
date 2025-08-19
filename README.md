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

08/07/25:
- Using Tailscale as a VPN, I can now access my home server services from anywhere so long as I am connected to it.

08/12/25:
- Created Nginx-proxy manager with DuckDNS to create SSL certificates as well as creating proxy hosts so that now within the internal network, or when connected to a VPN, I can enter a domain name rather than the IP address or hostname of my Raspberry Pi.

08/19/25:
- Using a cloudflare tunnel to be able to have my services accessible by the public
- Added 2 factor authentication so that even though the link is publicly accessible, you will still need an email that is within the accepted list of emails to get a code for access to my filebrowser service.