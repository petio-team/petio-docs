---
description: >-
  If you notice any mistakes that need to be corrected, please reach out on
  Discord!
---

# Sonarr

You can add multiple Sonarr servers to your Petio instance. This will show you how to connect an existing Sonarr server to Petio.

{% hint style="warning" %}
We support all Sonarr versions for now. V2 support will be dropped soon
{% endhint %}

{% hint style="info" %}
In the screenshots below we assume you are using locally accessible docker containers that are on the same docker network as Petio.
{% endhint %}

\*\*\*\*

## Step 1

Click on `Add New`

![](../.gitbook/assets/sonarr_setup_1.png)

## Step 2

After clicking `Add New` you need to specify all your Sonarr settings and give it a friendly name you can recognize. Your `host` and `port` fields will vary depending on what installation method you chose.

If you are hosting Sonarr behind a reverse proxy and have configured a base URL, you need to specify it on the `URL Base` field. If this all sounds like alien speak, you don't have to write anything there.

{% hint style="danger" %}
Make sure that the URL Base field has a preceding slash like `/sonarr`
{% endhint %}

You can obtain your Sonarr API key by going to your Sonarr instance and clicking on `Settings > General`.

![](../.gitbook/assets/sonarr_setup_2.png)

## Step 3

Hit `Test` to make sure you configured it correctly. You will not be able to configure your `Profile` and `Path` without testing the connection ahead of time. You should see a little message on the bottom right that says `Sonarr Test Connection success!`

![](../.gitbook/assets/sonarr_setup_3.png)

Once you are done hit `Save` and you are ready to requests TV Shows!

