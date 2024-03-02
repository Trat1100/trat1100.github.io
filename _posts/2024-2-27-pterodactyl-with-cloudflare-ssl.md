---
title: Pterodactyl Panel with Cloudfalre Proxy SSL
date: 2024-2-27 12:00:00 +0800
categories: [pterodactyl, cloudflare]
tags: [pterodactyl,cloudflare]     # TAG names should always be lowercase
---

## Generating a Cloudflare SSlL Certificate

Login to your [Cloudflare Dashboard](https://dash.cloudflare.com). Select your domain and go to: <br> `SSL/TLS --> Origin Server --> Create Certificate`
![Cloudflare](/assets/22-5-22/img001.png)

Hit **Create Certificate** and on the next screen, first make sure to select the Private key type to `RSA(2048)` then type your Pterodactyl Panel Domain in the *Hostnames* section `e.g. panel.trat.tech` and select your certificate duration.

![Cloudfalre](/assets/22-5-22/img002.png)

Now you have successfully generated a Cloudflare SSL Certificate. Select the **Key Format** to `PEM` and note both Origin Certificate and the Private Key in a notepad file as we will use them later.

## Adding Cloudflare Certificate to your Pterodactyl VPS

Login to your VPS and go to the directory `/home/<username>` and follow the commands given below:

```shell
cd /home/trat1100
mkdir certs && cd certs
```

Now add the Origin Certificate and Private Key in that directory by using a text editor called [nano](https://help.ubuntu.com/community/Nano). Use the command given below:

```shell
nano fullchain.pem 
# Paste the Origin Certificate by pressing Ctrl+Shift+V
# To Save and exit the Text editor Press Ctrl+X then Y and hit Enter key.
nano privkey.pem
# Paste the Private Key by pressing Ctrl+Shift+V
# To Save and exit the Text editor Press Ctrl+X then Y and hit Enter key.
```

## Configuring Reverse Proxy for Cloudflare SSL:

