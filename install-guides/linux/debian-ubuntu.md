---
description: >-
  If you notice any mistakes that need to be corrected, please reach out on
  Discord!
---

# Debian 10/Ubuntu 20.04

## MongoDB

Petio supports two ways of connecting to a Mongo Database instance, locally or remote. We recommend the locally hosted MongoDB option.

### **MongoDB Locally**

{% hint style="info" %}
Make sure to add the correct repository to `apt` depending on whether you're using Debian or Ubuntu.
{% endhint %}

* Import the public key used by the package management system:

```bash
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
```

* Create the /etc/apt/sources.list.d/mongodb-org-4.4.list file:

{% tabs %}
{% tab title="Debian 10" %}
```bash
echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
```
{% endtab %}

{% tab title="Ubuntu 20.04" %}
```bash
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
```
{% endtab %}
{% endtabs %}

* Reload local package database:

```bash
sudo apt-get update
```

* Install the MongoDB packages:

```bash
sudo apt-get install -y mongodb-org
```

* Start MongoDB:

```bash
sudo systemctl start mongod
```

* Verify that MongoDB has started successfully:

```bash
sudo systemctl status mongod
```

* To make sure MongoDB starts after restart use:

```bash
sudo systemctl enable mongod
```

### MongoDB Remotely

We are looking for contributors!

## Installing Petio

* Create a user for Petio:

```bash
sudo useradd -M --shell=/bin/false petio
```

* Make a directory for Petio:

```bash
sudo mkdir /opt/Petio
```

* Change ownership of the directory for Petio:

```bash
sudo chown petio /opt/Petio
```

* Download the latest version of Petio:

```bash
sudo wget https://petio.tv/releases/latest -O petio-latest.zip
```

* Extract Petio to the directory we just made:

```bash
sudo unzip petio-latest.zip -d /opt/Petio
```

* Create the petio service with systemd:

{% code title="/etc/systemd/system/petio.service" %}
```bash
[Unit]
Description=Petio a content request system
After=network.target
StartLimitIntervalSec=0

[Service]
Type=simple
Restart=on-failure
RestartSec=1
ExecStart=/opt/Petio/bin/petio-linux
User=petio

[Install]
WantedBy=multi-user.target
```
{% endcode %}

* Reload systemd:

```bash
sudo systemd daemon-reload
```

* Start Petio:

```bash
sudo systemctl start petio
```

Once you've completed theses steps, you can navigate to `http://<hostname>:7777` to start [configuring Petio](../../configuration/first-time-setup.md).

