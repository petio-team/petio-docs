---
description: >-
  If you notice any mistakes that need to be corrected, please reach out on
  Discord!
---

# General Settings

## Settings

The settings tab is where you will configure your general settings such as email, webhooks, base path \(subdirectory\), etc.

### Email

You can configure these email settings in order to get notifications when users request content and when content you've requested is marked available by Plex.

#### From Address

Modify this if you want the email to show up as something other than who you authenticate as. For example `petio@myemail.com` or `brucewillis@myemail.com`

#### Username

This is the username you use to log in. Most of the time is your actual email or sometimes you can use just the first part without specifying `@myemail.com`

#### Password

I think I don't really have to do write what a password is, do I? However, this is the password you use to log in to the email account. Not your Plex password, not your Petio password and not the password to your bank. I really hope you aren't using the same password across those 3 services...

{% hint style="warning" %}
**NOTE:** If you are using Gmail make sure [to read ](https://support.google.com/accounts/answer/185833)what to do if you use 2FA on your account.
{% endhint %}

#### SMTP Server

This one is all dependent on who your provider is, if you self host your own email server I hope you know your SMTP server. 

#### Port

The port is again dependent on your provider. Below you can find a table for the most common providers with SMTP server, and their SSL/TLS ports

| Mail Provider | SMTP Server | TLS Port | SSL Port |
| :--- | :--- | :--- | :--- |
| Gmail | smtp.gmail.com | 587 | 465 |
| GSuite/Google Workspace | smtp-relay.gmail.com | 587 | N/A |
| SendGrid | smtp.sendgrid.net | 587 | 465 |
| MailGun |  |  |  |

{% hint style="info" %}
Depending on what port you pick you might need to be sure **to not check** the box that says "Use Secure"
{% endhint %}

### Base Path

A base path is helpful if you are wanting to serve Petio behind a reverse proxy using the subdirectory method, otherwise known as a `base URL`, `base path`, or `subdirectory`. Please see our reverse proxy section for more information and examples.

### User Login

This setting will determine which login method is used to login to Petio. For the admin panel you will **always** need a username/password if you don't use Plex oAuth.

However, for the user panel you can specify `Standard Login` or `Fast Login`. The difference is that with `Fast Login` your users will only need to specify their Plex email/username whereas with `Standard Login` they will need to use your Plex email/username and password.

### Webhooks

#### Discord

{% hint style="info" %}
We assume you either have your own Discord or are in one where you have adminitrator permissions to perform these steps
{% endhint %}

* Create a new channel or use an existing one.
* Click `Edit Channel`.
* Click `Integrations`.
* Click `Webhooks`.
* Click `New Webhook`.
* Give it a `Name` and select the `Correct channel` then copy `Webhook URL` and save.
* Go to Petio then Admin panel -&gt; Settings. Scroll down until you find `Discord`.
* Paste the `Webhook URL` -&gt; Test -&gt; Save.

### Popular Content On Plex

{% hint style="danger" %}
This feature **requires** Plex Pass 
{% endhint %}

Adds the most popular Movies and TV Shows on Plex in the last 30 days based on user plays. It shows up when you click on the Movies/TV section

![](../.gitbook/assets/popular_tv_in_plex.png)

![](../.gitbook/assets/popular_movies_in_plex.png)

