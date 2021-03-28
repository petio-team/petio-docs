---
description: >-
  If you notice any mistakes that need to be corrected, please reach out on
  Discord!
---

# UnRAID

## MongoDB

### Template

### Community Applications

### 

### MongoDB Remotely

* Register for Atlas [here](https://www.mongodb.com/cloud/atlas/register).
* Create a free cluster.

![](../.gitbook/assets/remote_mongodb_cluster.jpg)

* Change the provider or region if you need to. It may take some time to create the cluster.

![](../.gitbook/assets/remote_mongodb_server_region.jpg)

* After the cluster is made, click on connect and select MongoDB Compass and follow the instructions on screen.

![](../.gitbook/assets/remote_mongodb_compass.jpg)

* Move on to the next section to start [installing Petio](unraid.md#petio).

## Petio

There are two ways to get Petio installed on unRAID. You can either import your own template or install it from the Community Applications plugin.

### Template

* Add the repo to `Template Repositories` under the Docker header:
  * [https://github.com/PotentialIngenuity/petio-unraid](https://github.com/PotentialIngenuity/petio-unraid)

![](../.gitbook/assets/unraid_template_repo.png)

* Click on`Add Container`

![](../.gitbook/assets/unraid_add_container.png)

* Configure the container like all the others on unRAID.

![](../.gitbook/assets/unraid_container_settings.png)

### Community Applications

* Go to the Apps page within unRAID and search for `Petio`. You can use either use ChargingCosmonaut's \(Official\) or Hotio's template.

![](../.gitbook/assets/unraid_template_ca.png)

* Configure the container like all the others on unRAID.

![](../.gitbook/assets/unraid_container_settings.png)

Once you've completed theses steps, you can navigate to `http://<hostname>:7777` to start [configuring Petio](../configuration/first-time-setup.md).

