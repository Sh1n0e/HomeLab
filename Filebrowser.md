# Filebrowser

The main reason I wanted to start up a homelab in the first place. Filebrowser is a very simple UI that allows me to store my files and as I get better and learn more on setting up my home server to expose it to the WAN, I am hoping that I can access these files stored in this image remotely.

----

## Deploying image

Before I begin anything, I have my raspberry pi connected to a 1TB external HDD which I can confirm is in place by using the ```lsblk``` command.

Then from there I need to mount the drive so I will execute the following commands:

```
0. Only applicable if this was a drive used in windows: Reformat the drive to be an appropriate drive type for linux. (I am using ext4 in my case)

sudo mkfs.ext4 /dev/(sdb/sdc/sda) 

1. Create a directory for the drive in the mnt directory (We will be referencing this when creating the container)

sudo mkdir /mnt/<drive name>

2. Mount disk into the recently created directory

sudo mount /dev/sda /mnt/<drive name>
```

Now that the hard drive has been mounted, I will execute the following docker compose command:

```
docker run \
    -v /path/to/drive:/srv \
    -v filebrowser_database:/database \
    -v filebrowser_config:/config \
    -p xxxx:80 \
    filebrowser/filebrowser

Where xxx is an arbritrary port number I assign And /path/to/drive is the hard drive you want to mount for storage.
```

**NOTE** --> When executing this command, it is very important to KEEP AN EYE on the terminal because you will be assigned a password when running this command and if you forget, you are gonna have to recreate the whole image.

----

## Issues experienced:

1. So after creating the image successfully, I am now trying to access filebrowser by entering the IP that has been assigned to that image in portainer with the port I set it to earlier, however it is not working. **Solution** - Just like Portainer, I can enter the hostname of my raspberry pi that is running the system and enter the port number I assigned.

2. Even when logged in as admin I cannot add/delete files and folders. **Solution** - Temporarily, I have changed the permissions of the file using ```chown o+rw /path/to/drive``` and that seems to have fixed the problem. I can work out a more secure solution down the line before I allow access from beyond my home network.

3. Recently discovered that if the raspberry pi im hosting is unplugged, the image won't relaunch to the hard drive that I had mounted earlier. **Solution** - I used the following command: ```sudo -H vim etc/fstab``` and add in the UID of the hard drive, where it is located and its default permissions. This should make it so that when it starts up, my hard drive should be found and not cause this issue again.

----

## Post installation:

Now that I have succesfully installed FileBrowser and confirmed that I am able to upload, download and create files and folders: I can say that this has come out very nicely.

I definitely learnt a lot more through this installation in comparison to pihole because I went ahead and used docker rather than the portainer UI which honestly was a lot more fun experimenting with everything.

Main things I learnt:
- Mounting a hard drive that I plugged in externally
- Executing docker compose command while editing parameters to fit what I need
- Adjusting read and write permission of directories present.
- Troubleshooting issues that come about when it comes to composing the container to ensure everything works properly.