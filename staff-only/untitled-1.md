# Petio Pre-Release Workflow For Testers

## Installation & First Time Setup

1. Wipe all **test** mongo/petio config folders
2. Pull latest `preview` tag and recreate Petio container
   * Optional: Create your appdata folders ahead of time to prevent permissions issues
3. Go to `http://hostname:port` and verify Petio redirects you to `/admin` when no `config.json` is present
4. Go through the initial setup and verify it completes without issues.

## Admin Panel Login

1. Log in to the admin panel with your credentials.
   * Errors?
2. Log in to the admin panel with Plex oAuth
   * Errors?

## Dashboard

1. Go to `Dashboard`
   * Do you have Plex Pass?
     * Yes
       * Are Plex Pass features available?
     * No
       * Do you see any errors?

## Requests

1. Click on `Requests`
   * Errors?

## Issues

1. Click on `Issues`
   * Errors?

## Reviews

1. Click on `Reviews`
   * Errors?

## Users

1. Click on `Users`
   * Create a new user profile with auto approve and no quota
     * Errors?
   * Create a new user profile with auto approve and quota
     * Errors?
   * Create a new user profile without auto approve and a quota
     * Errors?
   * Create a new user profile without auto approve and no quota
     * Errors?
   * Create a new user profile and set it as a default
     * Errors?
   * Bulk Edit and assign new user profiles to multiple users
     * Errors?

## Settings

1. Click on `Settings`
   * Errors?

### General

1. Under `General`
   * Test Plex connection
     * Errors?
   * Test email notification
     * Errors?
   * Test setting a base path
     * Restart Petio
       * Try to access admin panel by going to `http:\\hostname:port/petio/admin`
         * Errors?
   * Test `Standard` and `Fast` login methods
     * Errors?
   * Test enabling and disabling `Popular content on Plex`
     * Do you have Plex Pass?
       * Yes
         * Is Popular Content available when enabled and unavailable when disabled?
       * No
         * Do you see any errors when clicking on Movies/TV Shows?

### Radarr

1. Click on `Radarr`
   * Errors?
   * Test adding a new Radarr server
     * Errors?

### Sonarr

1. Click on `Sonarr`
   * Errors?
   * Test adding a new Sonarr server
     * Errors?

### Filters

1. Click on `Filters`
   * Errors?
   * Test creating filters
     * Test your filters and report back any filters with logic errors

### Console

1. Click on `Console` and verify you can filter through logging levels

## Request Content

1. Request content
   * Do notifications work as intended?
   * Are requests getting auto approved if set to be?
   * Are requests getting default values?

## General Testing

1. Report any typo, general errors you saw, wiki updates, etc.

