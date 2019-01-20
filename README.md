![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2019-01-20)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
66.70.217.179|tor.cusse.org|10
89.234.157.254|marylou.nos-oignons.net|9
60.12.215.85|-|9
176.10.104.240|tor1e1.digitale-gesellschaft.ch|9
42.61.24.202|-|9
219.135.194.73|73.194.135.219.broad.gz.gd.dynamic.163data.com.cn|9
111.7.177.239|-|9
217.170.205.77|vps-77.205.170.217.stwvps.net|9
61.188.189.7|7.189.188.61.broad.nc.sc.dynamic.163data.com.cn|8
80.82.77.33|sky.census.shodan.io|8
51.15.53.83|83-53-15-51.rev.cloud.scaleway.com|8
87.118.116.12|tormachine.keymachine.de|8
199.19.225.161|mxolution.info|8
122.226.181.165|-|8
122.226.181.164|-|8
122.226.181.167|-|8
122.226.181.166|-|8
76.72.169.18|egh4.com|8
180.111.205.112|-|8
171.25.193.20|tor-exit0-readme.dfri.se|8
218.48.59.189|-|8
144.132.10.218|cpe-144-132-10-218.rjui-cr-101.win.vic.bigpond.net.au|8
178.73.215.171|178-73-215-171-static.glesys.net|8
45.119.212.105|-|8
197.231.221.211|exit1.ipredator.se|8
27.3.150.15|-|8
71.229.24.115|c-71-229-24-115.hsd1.fl.comcast.net|8
94.41.0.140|94.41.0.140.static.ufanet.ru|8
109.195.93.219|109x195x93x219.dynamic.spb.ertelecom.ru|8
80.82.70.118|host.group-ib.ru|8
23.129.64.101|yawnbox.emeraldonion.org|8
64.113.32.29|tor.t-3.net|8
176.31.208.193|tor-exit1.netnik.xyz|8
171.25.193.77|tor-exit1-readme.dfri.se|8
171.25.193.78|tor-exit4-readme.dfri.se|8
199.87.154.255|tor.les.net|8
51.15.43.205|tor4thepeople3.torexitnode.net|8
125.64.94.200|-|8
87.228.111.210|-|8
62.102.148.67|-|8
101.226.241.113|-|8
88.214.26.49|-|8
113.122.10.250|-|8
103.255.235.141|-|8
122.154.143.2|-|8
152.204.24.19|-|8
117.135.115.70||8
121.165.33.239|-|8
112.254.116.143|-|8
115.238.245.4|-|8
185.244.25.157|-|8
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|8
80.67.172.162|algrothendieck.nos-oignons.net|8
