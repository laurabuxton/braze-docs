---
nav_title: Overview
page_order: 0
search_rank: 5
---
# API Overview

Braze provides a high performance REST API to allow you to track users, send messages, export data, and more.

## What is a REST API?

A REST API is a way to programmatically transfer information over the web using a predefined schema. Braze has created many different endpoints with specific requirements that will perform various actions and/or return various data. API access is done using HTTPS web requests to your company's REST API endpoint. Typically this is `https://rest.iad-01.braze.com`, but your Success Manager will provide an alternative endpoint URL if necessary.

{% alert note %}
Customers using Braze's EU database should use `https://rest.fra-01.braze.eu/`. For more information on REST API endpoints for customers using Braze's EU database see our [EU/US Implementation Differences documentation]({{ site.baseurl }}/developer_guide/eu01_us3_sdk_implementation_differences/overview/).
{% endalert %}

## API Definitions

Below is some terminology that you may see in the Braze REST API documentation and what it means.

### Endpoints

Braze manages a number of different instances for our Dashboard and REST Endpoints. When your account is provisioned you will log in to one of the corresponding URLs below. Use the correct REST Endpoint based on which instance you are provisioned to. If you are unsure, open a support ticket or use the table below to match the URL of the dashboard you use to the correct REST Endpoint.

|Instance|URL|REST Endpoint|SDK Endpoint|
|---|---|---|
|US-01| `https://dashboard-01.braze.com` | `https://rest.iad-01.braze.com` | `https://sdk.iad-01.braze.com` |
|US-02| `https://dashboard-02.braze.com` | `https://rest.iad-02.braze.com` | `https://sdk.iad-02.braze.com` |
|US-03| `https://dashboard-03.braze.com` | `https://rest.iad-03.braze.com` | `https://sdk.iad-03.braze.com` |
|US-04| `https://dashboard-04.braze.com` | `https://rest.iad-04.braze.com` | `https://sdk.iad-04.braze.com` |
|US-06| `https://dashboard-06.braze.com` | `https://rest.iad-06.braze.com` | `https://sdk.iad-06.braze.com` |
|US-08| `https://dashboard-08.braze.com` | `https://rest.iad-08.braze.com` | `https://sdk.iad-08.braze.com` |
|EU-01| `https://dashboard-01.braze.eu` | `https://rest.fra-01.braze.eu` | `https://sdk.fra-01.braze.eu` |

{% alert important %}
When integrating your SDK, use the "SDK Endpoint", not the "REST Endpoint".

When using endpoints for API calls, use the "REST Endpoint".
{% endalert %}

### Company Secret Explanation

The `company_secret` was formerly included with all API requests but has been deprecated as of October 2014. This field will be ignored for all future API requests to ensure backwards compatibility.

### App Group REST API Keys

The `api_key` included in each request acts as an authentication key that allows your server code to utilize our REST APIs. Within your company, each app group will have a unique set of REST API Keys. They can be found within the Braze dashboard by navigating to the Developer Console section for each app group. To use the REST API for any given App Group, you must create keys and give them permissions.

![REST API Keys][27]

#### API Key Permissions

API Keys are used to authenticate an API call. When you create a new REST API Key, you need to give it access to specific endpoints. By assigning specific permissions to an API Key, you can limit exactly which calls an API Key is able to authenticate.

A good security practice is to assign a user only as much access as is necessary to complete his or her job: this principle can also be applied to API Keys by assigning permissions to each key. These permissions give you better security and control over the different areas of your account.

![REST API Key Permissions][25]

{% alert warning %}
Given that REST API Keys allow access to potentially sensitive REST API endpoints, please ensure they are stored and used securely. For example, do not use this key to make AJAX calls from your website or expose it in any other public manner.
{% endalert %}

If accidental exposure of a key occurs, it can be deleted from the [Developer Console][8]. For help with this process, please [open a support ticket][support].


#### API IP Whitelisting

For additional security, you can specify a whitelist of IP addresses and subnets which are allowed to make REST API requests for a given REST API Key. To whitelist specific IP addresses or subnets, add them to the API IP Whitelisting section when creating a new REST API Key:

![API IP Whitelisting][26]

#### Creating and Managing REST API Keys

To create a new REST API Key, visit the [Developer Console][8] on your Braze Dashboard. This page displays your existing API Keys. To create a new key, click the "Create New API Key" button.

![Create New API Key][28]

You will then be able to:

- Give your new key a name for easy identification
- Select which permissions you would like to be associated with your new key
- Specify whitelisted IP addresses and subnets for the new key

Existing REST API Keys can be Viewed or Deleted by clicking the gear icon and selecting the corresponding option.

![API Key Options][29]

{% alert important %}
Keep in mind that once you create a new API Key, you cannot edit the scope of permissions or the whitelisted IPs. This limitation is in place for security reasons. If you need to change the scope of a key, create a new key with the updated permissions and implement that key in place of the old one. Once you've completed your implementation, go ahead and delete the old key.
{% endalert %}

###  External User ID Explanation

The `external_id` serves as a unique user identifier for whom you are submitting data. This identifier should be the same as the one you set in the Braze SDK in order to avoid creating multiple profiles for the same user.

### User Alias Object

{% include archive/aliasing.md platform="REST" %}

###  Braze User ID Explanation

The `braze_id` serves as a unique user identifier that is set by Braze. This identifier can be used to delete users through the REST API in addition to external_ids.

#### For more information see:

- [Setting User IDs - iOS][9]
- [Setting User IDs - Android][10]
- [Setting User IDs - Windows Universal][12]

##  API Limits

The Braze API infrastructure is designed to handle high volumes of data across our customer base. We enforce API rate limits in order to ensure responsible use of the API.

|Default API Rate Limit | Value|
|---|---|
|Requests to the `/users/track` endpoint|Unlimited, though this is subject to change as noted below. |
|Batching with the `/users/track` endpoint|75 Events, 75 Purchases, and 75 Attributes per API request. |
|Requests to the Send endpoint specifying a Segment or Connected Audience|250 per minute. |
|Send Identifier Creation|100 per day. |
|Requests of any other kind|250,000 per hour. |

{% alert warning %}
API Rate Limits and their Values (limited or unlimited) are subject to change depending on proper usage of our system. We encourage sensible limits when making an API call to prevent damage or misuse.
{% endalert %}

REST API rate limit increases are considered based on need for customers who are making use of the API batching capabilities. Please batch requests to our API endpoints:

- Each `/users/track` request can contain up to 75 Purchases, 75 Events and 75 Attribute updates. These can belong to different users, that is, each of the 75 Events in a request can belong to 75 different users.
- A single request to the Messaging endpoints can reach any one of the following:
  - Up to 50 specific `external_ids`, each with individual message parameters
  - A segment of any size created in the Braze dashboard, specified by its `segment_id`
  - An ad-hoc audience segment of any size, defined in the request as a [Connected Audience][7] object

The response headers for any valid request include the current rate limit status:

Header Name             | Description
----------------------- | -----------------------
`X-RateLimit-Limit`     | The maximum number of requests that the consumer is permitted to make per hour.
`X-RateLimit-Remaining` | The number of requests remaining in the current rate limit window.
`X-RateLimit-Reset`     | The time at which the current rate limit window resets in UTC epoch seconds.

If you have questions about API limits please contact your Customer Success Manager or please [open a support ticket][support].


[7]: {{ site.baseurl }}/developer_guide/rest_api/messaging/#connected-audience-object
[8]: https://dashboard-01.braze.com/app_settings/developer_console/ "Developer Console"
[9]: {{ site.baseurl }}/developer_guide/platform_integration_guides/ios/analytics/setting_user_ids/
[10]: {{ site.baseurl }}/developer_guide/platform_integration_guides/android/analytics/setting_user_ids/
[12]: {{ site.baseurl }}/developer_guide/platform_integration_guides/windows_universal/analytics/setting_user_ids/#setting-user-ids
[18]: {{ site.baseurl }}/developer_guide/rest_api/basics/#what-is-a-rest-api
[support]: {{ site.baseurl }}/support_contact/
[25]: {% image_buster /assets/img_archive/api-key-permissions.png %}
[26]: {% image_buster /assets/img_archive/api-key-ip-whitelisting.png %}
[27]: {% image_buster /assets/img_archive/rest-api-key.png %}
[28]: {% image_buster /assets/img_archive/create-new-key.png %}
[29]: {% image_buster /assets/img_archive/api-key-options.png %}
