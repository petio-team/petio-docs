---
description: >-
  If you notice any mistakes that need to be corrected, please reach out on
  Discord!
---

# Caddy

## Caddy For Windows

* Download the newest release from [here](https://caddyserver.com/v2).
* Create a folder named `Caddy` on root of the `C:\` drive or where you got Windows installed.
* Extract the Caddy zip in the folder you just created.
* In the new Caddy folder make another folder called `logs`.

### Make a Caddy File

* Create a new text file, rename it to `Caddyfile` and make sure it doesn't have an extension.
* In the `Caddyfile` paste:

```text
example.ddns.net {
    encode gzip
        log {
            output file C:\Caddy\logs\petio.log
            {
            roll true               # Rotate logs, enabled by default
            roll_size_mb 5          # Set max size 5 MB
            roll_gzip true          # Whether to compress rolled files
            roll_local_time true    # Use localhost time
            roll_keep 2             # Keep at most 2 log files
            roll_keep_days 7        # Keep log files for 7 days
            }
        }
    reverse_proxy localhost:7777
}
```

* Remember to change `localhost` and `port` accordingly.

### Start Caddy

* You have two ways to run Caddy.

  * You can do it manually by creating a bat file:

  ```text
  cd C:\Caddy
  Caddy run'
  ```

  * You can run it as a service. Just follow the [NSSM](../install-guides/windows.md#nssm) or [Shawl](../install-guides/windows.md#shawl) guides.

### Port Forwarding

* Open port `80` and `443`.  If you don't know how to port forward you should check out [Portforward.com](https://portforward.com/router/) and find your router.

### Firewall

* Open port `80` and `443` in your firewall. To open Windows Firewall, go to the Start menu, select Run, type `WF.msc` and then select OK.
* Now click on Inbound Rules, then on the right side you want to click new rule.
* Select Port click next.
* Select TCP and type inn `80, 443` then next.
* Allow the connection and hit Next. Then just choose a name like "Caddy".

### DNS

* Now you need to get DNS redirect set up.  Some examples of services you can use are [noip](https://www.noip.com/) or [DuckDNS](https://www.duckdns.org/). Just make sure you set the record type as “DNS Host \(A\)”.

## 

