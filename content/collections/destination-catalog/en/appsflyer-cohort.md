---
id: 4e48a01b-3b64-49e6-b6ee-f545e42f1347
blueprint: destination-catalog
title: 'Appsflyer (Cohort)'
connection: destination
integration_type:
  - cohorts
integration_category:
  - attribution
partner_maintained: false
integration_icon: partner-icons/appsflyer.svg
exclude_from_sitemap: false
updated_by: 0c3a318b-936a-4cbd-8fdf-771a90c297f0
updated_at: 1720114013
---
{{partial:admonition type="beta" heading=""}}
The AppsFlyer destination is in open beta, and is still in active development. If you have any feedback to help improve the AppsFlyer destination and its documentation, contact your AppsFlyer CSM or send an email to [hello@appsflyer.com](mailto:hello@appsflyer.com).
{{/partial:admonition}}

[AppsFlyer Audiences](https://www.appsflyer.com/products/audiences/) is a privacy-first audience segmentation and analytics solution aimed at increasing user retention and LTV through personalized interactions on owned and paid channels. With Audiences, you can effectively build, manage, and connect your audiences to more than 70 different partners and measure their performance and incremental impact from a single dashboard.

By sending Amplitude cohorts to AppsFlyer Audiences, you can leverage your first-party Amplitude data to create rich audiences that power performance and organic marketing initiatives at scale.


## Considerations

- You must define a separate data destination in Amplitude for each app for which you are syncing data to AppsFlyer. For example, if you have an Android and an iOS app, you need to create two destinations in Amplitude: one for the Android app, and one for the iOS app.

## Setup

### AppsFlyer setup

Get your AppsFlyer App ID and AppsFlyer API token. 

#### Get app ID

Copy the app ID from your AppsFlyer dashboard.


#### Get API token 

1. In AppsFlyer, access the user menu (email address drop-down in the top right corner).
2. Select **Security center**.
3. In the AppsFlyer API tokens section, click **Manage your AppsFlyer API tokens**.
4. Copy the V2.0 token.

### Amplitude setup 

#### Add the destination

1. In Amplitude Data, click **Catalog** and select the **Destinations** tab.
2. In the Cohort section, click **AppsFlyer**.
3. Click **Add another destination**.
4. Enter *Name* and then paste your *AppsFlyer App ID* and *AppsFlyer API Token V2*.
5. Choose a platform.
6. Map your user identifier.
      - For iOS audiences: iOS Advertiser ID, Amplitude User ID, or AppsFlyer Customer User ID
      - For Android audiences: Google Advertiser ID, Amplitude User ID, or AppsFlyer Customer User ID
7. Save the destination.

## Send a cohort

Follow these steps to sync any of your Amplitude cohorts to your AppsFlyer destinations:

1. From the Cohorts page in Amplitude, click the cohort to sync to AppsFlyer, or create a cohort.
2. Click **Sync**.
3. Select **AppsFlyer**, then click **Next**.
4. From the *Select an API target to sync to list*, select your AppsFlyer destination.
5. Define the sync cadence.
6. Click **Sync** to start syncing.

When the first sync finishes running, a new audience for this cohort is visible the Audiences tab of the Audiences dashboard in AppsFlyer.

By default, the name of the new audience is the name of the synced Amplitude cohort, followed by an alphanumeric identifier. You can edit the audience name from the Audiences dashboard if you wish.