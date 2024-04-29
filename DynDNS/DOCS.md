# Home Assistant Add-on: DynDNS

## Installation

Follow these steps to get the add-on installed on your system:

1. [Add my Home Assisant add-ons repository][repository] to your HassOS instance. 
2. Navigate in your Home Assistant frontend to **Settings** -> **Add-ons** -> **Add-on store**. 
3. Find the "DynDNS" add-on and click it. 
4. Click on the "INSTALL" button.

## How to use

1. Set up the dynamic DNS service, as described in the dynamic DNS service provider documentation.
2. In the configuration of the DynDNS add-on, you only need to set the updateUrl as described by your provider in its documentation.  
Then replace the variables for the IPv4 and IPv6 in this url.  
Some providers require you to log in with the request. You can use the `dnsServiceUsername` and `dnsServicePassword` options for this.

## Configuration 

Add-on configuration:

### Option: `updateUrl` (required)

The DNS update url which is provided by your Dynamic DNS services.
In addition, there are various variables for replacing dynamic parts of the update url.

> **For Example:** https://dyndns.inwx.com/nic/update?myip=${ipv4}&myipv6=${ipv6}  
or  
> https://www.duckdns.org/update?domains=example.duckdns.org&token=abcd1234-1234-abcd-1234-abcdef123456&ip=${ipv4}&ipv6=${ipv6}

#### Available variables:
- `${ipv4}`  
  The IPv4 provided by the settings of the `ipv4` option
- `${ipv6}`  
  The IPv6 provided by the settings of the `ipv6` option
- `${DNS_SERVICE_USERNAME}`  
  The value of the `dnsServiceUsername` option
- `${DNS_SERVICE_PASSWORD}`  
  The value of the `dnsServicePassword` option

### Option: `secondUpdateUrl` (optional)

In some cases, you may need to update IPv4 and IPv6 in two separate requests, so you can enter the second DNS update url here.
In addition, there are various variables for replacing dynamic parts of the update url.

> **For Example:** https://dyndns.inwx.com/nic/update?myip=${ipv4}&myipv6=${ipv6}  
or  
> https://www.duckdns.org/update?domains=example.duckdns.org&token=abcd1234-1234-abcd-1234-abcdef123456&ip=${ipv4}&ipv6=${ipv6}

### Option: `dnsServiceUsername` (optional)

For some dynDNS services you have to authenticate yourself during the request.
To do this, you have to enter the corresponding username here.

### Option: `dnsServicePassword` (optional)

For some dynDNS services you have to authenticate yourself during the request.
To do this, you have to enter the corresponding password here

### Option: `ipv4` (required)

This option allows to specify either 'default' or an interface name to use an IPv4 
address of the host, alternatively you can input an address manually.

If you specify a URL here, contents of the resource it points to will be
fetched and used as the address. This enables getting the address using
a service like https://api.ipify.org/ or https://ipv4.text.wtfismyip.com

> If you are not sure, set it to “default”

### Option: `ipv6` (required)

This option allows to specify either 'default' or an interface name to use an IPv6 
address of the host, alternatively you can input an address manually.

If you specify a URL here, contents of the resource it points to will be
fetched and used as the address. This enables getting the address using
a service like https://api6.ipify.org/ or https://ipv6.text.wtfismyip.com

> If you are not sure, set it to “default”

### Option: `seconds`

The number of seconds to wait before updating subdomains.

### Examples

#### INWX
```yaml
updateUrl: https://dyndns.inwx.com/nic/update?myip=${ipv4}&myipv6=${ipv6}
seconds: 300
ipv4: default
ipv6: default
dnsServiceUsername: example-username
dnsServicePassword: secret
```

#### Strato
```yaml
updateUrl: https://dyndns.strato.com/nic/update?hostname=${DNS_SERVICE_USERNAME}&myip=${ipv4},${ipv6}
seconds: 300
ipv4: default
ipv6: default
dnsServiceUsername: sub.domain.de (In this case the subdomain) 
dnsServicePassword: secret
```

#### DuckDNS
Note that in the updateUrl the domain and the token must be replaced with yours.
```yaml
updateUrl: https://www.duckdns.org/update?domains=example.duckdns.org&token=abcd1234-1234-abcd-1234-abcdef123456&ip=${ipv4}&ipv6=${ipv6}
seconds: 300
ipv4: default
ipv6: default
```

## Known issues

- `/run.sh: line 28: SOMEVARIABLE: unbound variable`  
  This error means that you have a hint error in the `updateUrl` for the variables or that they do not exist

## Support

Got questions?

You have several options to get them answered:

- The [Home Assistant Discord Chat Server][discord].
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

In case you've found a bug, please [open an issue on our GitHub][issue].