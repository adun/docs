# Raspberry Pi

## Post installation tweaks

### Update packages

```
sudo apt update && sudo apt upgrade -y
```

### Change hostname

```
hostnamectl set-hostname <NEW_HOSTNAME>
```
And add an entry to `/etc/hosts`
```
127.0.0.1    new-hostname
```

### Setup firewall

Set default rules and allow SSH connexion through the firewall
```
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw enable
```

## AdGuard Home

[AdGuard wiki](https://github.com/AdguardTeam/AdGuardHome/wiki/Getting-Started)

### Installation

Download and extract Linux ARM: 32-bit ARMv6 (recommended for Raspberry Pi)
```
wget https://static.adguard.com/adguardhome/release/AdGuardHome_linux_armv6.tar.gz
tar -xf AdGuardHome_linux_armv6.tar.gz
```

Enable firewall temporary rules to access AdGuard initial configuration wizard on port `3000`
```
sudo ufw allow 3000
```

Run AdGuard and configure until the last step shutdown the app using CTRL+C twice.
```
sudo ./AdGuardHome
```

Display ufw temporary firewall rules and remove rule by rule number
```
sudo ufw status numbered
sudo ufw delete {rule-number-here}
```

Install AdGuard service
```
sudo ./AdGuardHome -s install
```

Add rule to allow HTTP connections
```
sudo ufw allow http
```

Add rules to allow DNS connections
```
sudo ufw allow 53/tcp
sudo ufw allow 53/udp
```

### Configure Nginx as a reverse proxy server for AdGuard Home

Edit AdGuard configuration to bind the service to another port than HTTP/80.

Change configuration to another port: `bind_host: 127.0.0.1` and `bind_port: 81` and restart the service.
```
sudo nano AdGuardHome.yaml
sudo ./AdGuardHome -s restart
```

Install Nginx
```
sudo apt install nginx -y
```

Sample nginx reverse proxy configuration
```
location /agh/ {
    proxy_pass http://localhost:81/;
    proxy_redirect / /agh/;
    proxy_cookie_path / /agh/;
}
```

Add the reverse proxy to Nginx configuration and restart the service
```
sudo nano /etc/nginx/sites-available/default
sudo systemctl restart nginx
```

Access AdGuard Home dashboard
```
SERVER_IP/adg
```

### Custom DNS blocklists

- SebSauvage Hostfile
https://sebsauvage.net/hosts/hosts-adguard

- AdGuard Social Media filter
https://filters.adtidy.org/extension/chromium/filters/4.txt

- AdGuard Tracking Protection filter
https://filters.adtidy.org/extension/chromium/filters/3.txt

- AdGuard Base filter
https://filters.adtidy.org/extension/chromium/filters/2.txt

- AdGuard Annoyances filter
https://filters.adtidy.org/extension/chromium/filters/14.txt

- Filter unblocking search ads and self-promotion
https://filters.adtidy.org/extension/chromium/filters/10.txt

- AdGuard Russian filter
https://filters.adtidy.org/extension/chromium/filters/1.txt

- AdGuard German filter
https://filters.adtidy.org/extension/chromium/filters/6.txt

- AdGuard French filter
https://filters.adtidy.org/extension/chromium/filters/16.txt

- AdGuard Japanese filter
https://filters.adtidy.org/extension/chromium/filters/7.txt

- AdGuard Mobile Ads filter
https://filters.adtidy.org/extension/chromium/filters/11.txt

- AdGuard DNS filter
https://filters.adtidy.org/extension/chromium/filters/15.txt

- WaLLy3K's Blacklist
https://v.firebog.net/hosts/static/w3kbl.txt

- ZeroDot1 CoinBlockerLists
https://zerodot1.gitlab.io/CoinBlockerLists/hosts_browser

- Fademind's Risky Hosts
https://raw.githubusercontent.com/FadeMind/hosts.extras/master/add.Risk/hosts

- Spam404
https://raw.githubusercontent.com/Spam404/lists/master/main-blacklist.txt

- DigitalSide Threat-Intel
https://osint.digitalside.it/Threat-Intel/lists/latestdomains.txt

- Easy privacy
https://v.firebog.net/hosts/Easyprivacy.txt

- Quidsup Tracker
https://gitlab.com/quidsup/notrack-blocklists/raw/master/notrack-blocklist.txt

- Blocklist Scam
https://blocklist.site/app/dl/scam

- Blocklist Fraud
https://blocklist.site/app/dl/fraud

- Blocklist Phishing
https://blocklist.site/app/dl/phishing

- Blocklist Ads
https://blocklist.site/app/dl/ads
