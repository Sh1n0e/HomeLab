# Pihole

The first thing I will be setting up on my homelab is a pihole image as a way to block ads for anyone as long as I have the addresses set up for it.

## How does it work?

Pihole works by acting as a middle man that stands between any given host device that is configured to have pihole with it, to the rest of the internet.

It acts as a DNS sinkhole which intercepts DNS requests and then compares them to a known list of ad and tracking domains. If there are any matches, then the requests are either blocked or allows the requests to come through.

This works especially with ads because nowadays, rather than hardcoding ads into apps or websites, DNS servers are set up that host a variety of ads that will eventually be picked to be tailored for any given person. Best example I can think of is how Amazon knows what products to try advertise to you.


## Steps to complete

Our first step is to clear port 53 using the following command as root to run a script to automate this process:

```bash -c "$(wget -qLO - https://raw.githubusercontent.com/bigbeartechworld/big-bear-scripts/master/disable-dns-service/disable_dns_service.sh)"```

verify with the following: ```lsof -i :53``` OR ```netstat -tulpn | grep ":53:"```

After we have confirmed the port is open, we can use the following docker compose file to set up a container for pihole so we can edit whatever we need on it.

To do that we can take the quickstart docker compose from this github repository: https://github.com/pi-hole/docker-pi-hole/#running-pi-hole-docker.

from this script there are some changes that need to be made to ensure that we are able to get connected ourselves.

## After Set up

Once I completed everything I was able to get into the admin page by entering the address of my raspberry pi through port 8080/admin: ```x.x.x.x:xx/admin```

Entering that into my searchbar now gives me access to the pihole UI so I can organize groups, what I would want blocked, temporarily stop pihole from operating to allow all traffic in and etc.

## Blocking ads

Now that I have access to the UI, I want to try and set it up so that I can have it block ads for myself.

The steps I had to do was very simple:

1. Go into ncpa.cpl and disable ipv6
2. Afterwards go into the properties for ipv4
3. Change the dns server from being collected automatically to enter the address that pihole is being hosted on.

If all is done correctly then this means that now no ads will show up as pihole blocks any dns responses that are being sent out by websites that you are visiting.