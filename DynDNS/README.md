# Home Assistant Add-on: DynDNS

Automatically update your Dynamic DNS IP address with support of various Dynamic DNS (DynDNS or DDNS) services.

![Supports aarch64 Architecture][aarch64-shield] ![Supports amd64 Architecture][amd64-shield] ![Supports armhf Architecture][armhf-shield] ![Supports armv7 Architecture][armv7-shield] ![Supports i386 Architecture][i386-shield]

## About

The following Dynamic DNS services were tested:
- INWX: https://dyndns.inwx.com/nic/update?myip=${ipv4}&myipv6=${ipv6}
- Strato: https://dyndns.strato.com/nic/update?hostname=${DNS_SERVICE_USERNAME}&myip=${ipv4},${ipv6}
- DuckDNS: https://www.duckdns.org/update?domains=example.duckdns.org&token=abcd1234-1234-abcd-1234-abcdef123456&ip=${ipv4}&ipv6=${ipv6}
> Even if your Dynamic DNS services are not listed here, it is quite possible that it will still work with this add-on.

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg

**Based on the [Home Assistant DuckDns Add-On](https://github.com/home-assistant/addons/tree/master/duckdns)**
**Logo created with  [logo.com](https://logo.com/)**