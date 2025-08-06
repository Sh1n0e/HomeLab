# Welcome

This is the beginning of my homelab journey. To start I will be using a Raspberry Pi Zero 2 W and I initally plan to use this to host the following:

- pihole server
- Host a file server
- create a self-hosted website with the use of nginx
  - use nginx-reverse-proxy to enable my homelab to be accessible via WAN


This whole project stemmed from the idea that I use github as a means to store my notes that I take from my classes, but I figured I should be able to host it in my own way beacuse it would look a lot cooler. It would also make for a nice way to develop my own learning.

-----

## Initial set up 

Using the raspberry pi imager, I was able to get a full set up of a baseline operating system.
- I should note that I plan to make this a headless system, so I will be running majority of things within the raspberry pi purely off of command line as an extra added level of self-challenge.

With the full set up came with ssh pre included so I just ssh myself in via the windows terminal.

From there I install docker with the following command: ``` sudo apt install docker.io ```. I found this did take 2 tries (once initially then again after running ```sudo apt-get update```).

From here I will now try to host virtual containers on portainer.

```
1. Create a volume to store databases:

sudo docker volume create portainter_data

2. Downloading and installing the portainer server container:

sudo docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ee:lts

3. Verify installation is done correctly

sudo docker ps
```

If all is good then we can go to the web server by typing the following into your search bar:

``` https:localhost.local:<portNumber>```
- Where the local host is what you would name your raspberry pi (at least for me because while the server runs on the pi itself, I will manage everything remotely via my PC)

You will be prompted with a login screen where you will create your credentials so go on ahead and do that as well as entering your assigned license key. Everything else will be taken care of from there.
