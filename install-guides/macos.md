---
description: >-
  If you notice any mistakes that need to be corrected, please reach out on
  Discord!
---

# MacOS

## MongoDB

Petio supports two ways of connecting to a Mongo Database instance, locally or remote. We recommend the locally hosted MongoDB option.

{% hint style="warning" %}
Macs with the new M1 chip \(arm64 arch\) do not yet support Mongo locally installed. Please use either Remote MongoDB Hosting or any of the [Docker ](docker.md)options.
{% endhint %}

### MongoDB Locally

{% hint style="info" %}
We assume you've installed [homebrew](https://brew.sh/#install) in order to follow this guide.
{% endhint %}

* Add the Official MongoDB Repo to homebrew:

```bash
brew tap mongodb/brew
```

* Install MongoDB:

```bash
brew install mongodb-community@4.4
```

* Start MongoDB as a service:

```bash
brew services start mongodb-community
```

### 

### MongoDB Remotely

* Register for Atlas [here](https://www.mongodb.com/cloud/atlas/register).
* Create a free cluster.

![](../.gitbook/assets/remote_mongodb_cluster.jpg)

* Change the provider or region if you need to. It may take some time to create the cluster.

![](../.gitbook/assets/remote_mongodb_server_region.jpg)

* After the cluster is made, click on connect and select MongoDB Compass and follow the instructions on screen.

![](../.gitbook/assets/remote_mongodb_compass.jpg)

* Move on to the next section to start [installing Petio](macos.md#petio-as-a-service).

## Petio as a Service

* First make a directory for Petio:

```bash
sudo mkdir /opt/Petio
```

* Download the latest version of Petio:

```bash
sudo curl -L https://petio.tv/releases/latest --output petio-latest.zip
```

* Extract Petio to the directory we just made:

```bash
sudo unzip petio-latest.zip -d /opt/Petio
```

* To have Petio running in the background without user input, we will use `launchctl.`
  * To more-or-less control `launchd`define a service for Petio like shown below and save it as `tv.petio.plist` in the `~/Library/LaunchAgents/` folder.

```markup
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
    <dict>
        <key>Label</key>
        <string>tv.petio</string>
        <key>ProgramArguments</key>
        <array>
            <string>/opt/Petio/bin/petio-macos</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
    </dict>
</plist>
```

* Load the service using:

```bash
launchctl load ~/Library/LaunchAgents/tv.petio.plist
```

* Start the service using:

```bash
launchctl start tv.petio
```

* Verify that Petio is indeed running:

```bash
launchctl list | grep tv.petio
```

* To stop Petio, run:

```bash
launchctl stop tv.petio
```

Once you've completed theses steps, you can navigate to `http://<hostname>:7777` to start [configuring Petio](../configuration/first-time-setup.md).

