# FAQ

### Roadmap

A public roadmap is planned and will be made soon!

### Plex oAuth

Petio supports Plex oAuth

### MongoDB

Petio doesn't use relational data. MongoDB in this instance is way faster for us to parse straight into the API worker.

### Single Season TV Show

At this time, only whole shows can be requested. However, TV Show request granularity is a planned enhancement

### Plex Library Scan

A partial scan is ran every 30 mins and a full scan is ran everyday at midnight.

### Unable to log in to the admin portal

If you aren't using Plex oAuth to sign in to Petio - when you first set up Petio, you were prompted to set up a custom password. Make sure you are using the correct password and not your Plex password.

### Localization

Translations will be a part of the next development phase using i18n strings.

### Request with a yellow warning

A TV request without a TVDB ID can't be passed to Sonarr, this is usually because TMDB doesn't have a TVDB ID for this show yet. Petio will check for the TVDB ID as part of a cron and once one is found it will be processed. You can also manualy add one to TMDB.

### Why are all my requests pending?

Are your requests being approved? Take a look at the user profiles. Still having issues? Read over our [user profiles](configuration/user-profiles.md) section.

### Notifications/Webhooks

The current notification system will undergo an overhaul.

### Lidarr Support

Lidarr support is planned

### Backups

Backup options are planned including database backup

