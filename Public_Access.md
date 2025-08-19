# Accessing services via Cloudflare

Initially I used a VPN that allows me to access my services via the VPN assigned IP addresses, I kept getting annoyed with the fact that there would be no SSL certificates available so I would always be annoyed with that.


Initially my solution involved using DuckDns to create SSL certificates that my services can use in conjunction with nginx proxy manager to make it so that within the network I can use a proxy name in stead of having to enter a regular address or use the name of my raspberry pi in order to access any given service.
- This still works for the record, I just now have the extra option when I am home to use either the public address or the private proxy.


Now what I have done is utilize cloudflare's tunneling service to essentially create a secure way for me to be able to access my internal services that I choose to make publicly available without having to go out of my way to change my home router, or firewall setting to expose Setting up the tunnel 

## What did I need to start 

1. A domain name
  - You can get this from anywhere, I chose to get my domain right from squarespace.
2. Cloudflare account
  - This is where the majority of anything involving binding my services to my new domain will happen.

## Setting up the tunnel 


