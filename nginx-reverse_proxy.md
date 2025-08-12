# NGINX-Proxy-Manager

The following below is the startup script I will be using when creating the image:
```docker
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '443:443'
      - '81:81'
      
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```
in my own setup, I did change the host port numbers as I already have them occupied by other services I am currently running.

Now that I have that set up, you can enter the ip address or hostname of the machine that is hosting these services and then add port 81 (:81) to reach the admin page with a prompt to log in.

The default settings for nginx proxy manager is:
- username: admin@example.com
- passowrd: changeme

Once done you will log in and be prompted to change the default username and password.

**NOTE**: It is very important that (at least in my case) to keep the ports the same, I originally launched an image of this with ports 80 and 443 changed and my proxy wouldn't work until I changed it back.

## Post installation

### Creating SSL certificate
Now that I have completed the installation, I will be playing around with DNS domains. For my case, I will be using Duck DNS as it is free and easy to use, but feel free to use whatever you want to use.

In duck DNS, you will be prompted to add your first domain, so do that and name it whatever you want it to be then add it. Unless you are hosting the reverse proxy on a personal device or have it bridged to a VM that is hosting the service, you will need to copy and paste the address being used as the ip of the domain.

From there, you can go back to your proxy manager, and create new SSL certificate. This is where we will be using the domain that we have created earlier so that we can get the following benefits:
1. No need to memorize address and port numbers for services
2. Removes the annoying "http is not secure" error message that I get whenever using any of the services I am running.

When creating this SSL certificate, we need:
- Domain name from wherever you had yours created (I used duckdns)
- Press the SSL certificate tab on the proxy manager
- Press the add button and choose the "Let's Encrypt" option
- From here you will be prompted to add domain names so we need to add the following:
  - your.domainname.xxxx AND a wildcard domain which consists of: *.your.domainname.xxx
  - The * represents the wildcard in which I will show how that is relevant when adding my proxy for my filebrowser service.
- From there you need to enable "Use a DNS Challenge"
  - Select your provider
  - Enter the token that is given to you
  - Set propagation seconds to 120 just to give time.

Sometimes when creating the SSL certificate, you may need to try the process again and then it will work perfectly.

### Creating first host

I will use my filebrowser service to be the tester for both when im connected internally to my server and beyond when im using the tailscale VPN I have set up.

To being the setup we can go to the Host tab and click the option that will direct us to the proxy host tab then add a new host.

From here we will be prompted with the domain name we would like to use as our proxy. Afterwards, we are prompted on if we want it to use the http or https protocol. Then we add the direct address we are using (in my case, the ip address assigned to my raspberry pi) and then the next box with the port number.

Once this is done there will be some options with the following labels:
- Cache Assets
- Block Common Exploits
- Websockets Support

For our use case, we really only need option 2 and potentially option 3 if you want.

Then we go on to the SSL tab where we use the dropdown box that is present and select the SSL certificate that we created earlier. Then we will get similar options in this tab for additional options in regards to the SSL:
- Force SSL
- HTTP/2 Support
- HSTS Enabled
- HSTS Subdomains

As I am writing this I don't have an idea on what the last two options are about, all I am concerned about is the Force SSL option as well as the HTTP/2 support to ensure that each of my domains are now secured so web browsers won't constantly give warnings that the website is not safe, as well as ensuring that features present with HTML 5 will work in future.



