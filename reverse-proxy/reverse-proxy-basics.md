---
description: >-
  If you notice any mistakes that need to be corrected, please reach out on
  Discord!
---

# Reverse Proxy Basics

A good ELI5 explanation for a reverse proxy server is to think of it as a single point of entrance for your network as opposed to multiple points of entrance. It checks requests coming in through  ports 80/443 - or whatever port you might specify differently - and directs those requests to the correct server such as Petio, Radarr or Sonarr. The reason why this is more secure is because rather than randomly punching holes in your firewall for _each_ service, you are only forced to open up 1 or 2 ports that handle all the traffic.

We recommend you read [LinuxServer.io's guide ](https://docs.linuxserver.io/general/swag)on how to set up their SWAG container which contains all the necessary tools for a reverse proxy at home.
