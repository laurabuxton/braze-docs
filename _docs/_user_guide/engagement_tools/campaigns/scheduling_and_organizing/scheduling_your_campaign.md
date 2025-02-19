---
nav_title: Scheduling Your Campaign
platform: Campaigns
subplatform: Scheduling and Organizing
page_order: 0
---
# Scheduling Your Campaign

Every savvy marketer knows that timing is key, which is why Braze provides multiple scheduling options that will empower you to reach users at precisely the right time. Ample flexibility, however, may cause uncertainty over which type of schedule fits best with your campaign's goals. To help you get the most of Braze's platform, we've created this handy guide that reviews your scheduling options, best practices and use cases.

## Scheduled Delivery

Campaigns sent using time-based scheduled delivery are delivered on specified days.

![Time based][3]

### Option 1: Send as soon as Campaign is launched

If you choose to send a message as soon as it's launched, it will begin sending as soon as you finish creating your campaign.

![Immediately][10]

This type of schedule is designed for one-off campaigns that you wish to send immediately, such as messages pertaining to a current event. A sports app, for instance, may schedule push notifications on score updates using this option. In addition, when sending test messages aimed at just yourself or your team, this option allows you to deliver them immediately. If you plan on editing the campaign and re-sending it after viewing the test, be sure to check the box that makes users [re-eligible][24] to receive the campaign. By default, Braze sends a campaign to a user just once, unless that box is checked.

### Option 2: Sending at a Designated Time

Scheduling a campaign for a designated time allows you to specify the days and times your campaign will send. You can send a message once, daily, weekly or monthly at a certain time of day, as well as specify when your campaign should begin and end. If you choose Scheduled Delivery and don't choose to send at user local time, your campaign will send according to the time zone specified on your "Company Settings" page.

![Designated time][9]

#### Local Time Zone Campaigns

You can deliver the message in users' local time zones, so that members of your international audience won't receive a notification at 4am. Local time zone campaigns need to be scheduled 24 hours in advance to ensure that eligible users from all time zones can receive it. Read [our FAQ page on this feature][25] to understand how local time zone campaigns work and the associated delivery rules.

Segments targeted with local time zone campaigns should include at minimum a 2-day window to incorporate users from all time zones. For instance, if your campaign is scheduled to send in the evening but has just a 1-day window, then some users may have fallen out of the segment when their time zone is reached. Examples of filters that create a 2-day window are "last used more than 1 day ago" and "last used less than 3 days ago," or "first purchased more than 7 days ago" and "first purchased less than 9 days ago."

#### Use Cases

Designated time schedules are best suited for messages scheduled in advance and recurring campaigns - such as [onboarding][7] and retention - that run regularly on all qualified users.

### Option 3: Intelligent Delivery

Intelligent Delivery allows you to deliver a campaign to each user at a different time. Braze calculates each individual's time based on when that user typically engages with your app and its notifications. You can optionally specify that intelligent delivery campaigns send only during a certain portion of the day - for instance, if you are notifying users of a promotion that ends at midnight, you may want your messages to send by 10pm at the latest. Read our [page on Intelligent Delivery][8] for more details on how this feature works.

![Intelligent Delivery][14]

#### Delivery Rules

Because a user's optimal time can be anytime over the course of 24 hours, all Intelligent Delivery campaigns must be scheduled 24 hours in advance. In addition, similar to designated time campaigns, messages with a 1-day window will miss users who fall out of the segment before their optimal time in their time zone is reached. Segments for intelligent delivery campaigns should incorporate at minimum a 3-day window to account for this.

#### Use Cases

Intelligent Delivery campaigns work best for one-off and recurring messages where there is some flexibility regarding delivery time - for instance, they aren't well suited for breaking news or timed announcements.

## Action-Based Delivery (Event Triggered Campaigns)

Instead of sending your campaign on certain days, you can trigger them to send after a user completes a certain event. Here are the steps for setting up an event-based schedule:

### Setting Up a Triggered Campaign

__Step 1: Select a trigger event, which can be:__

- Starting a session
- Purchasing an item
- Interacting with News Feed cards (see [Braze's Campaign Connector][33])
- Interacting with other campaigns
- Entering a location
- Completing any custom event
- Performing the campaign's primary conversion event
- Performing the exception event for another campaign
- Adding an email address to a user profile

You can also further filter trigger events through Braze's [Custom Event Properties][32] which allows for customizable event properties for both custom events and in-app purchases. This feature allows you to further tailor which users receive a message based off of the specific attributes of the custom event, allowing for greater campaign personalization and more sophisticated data collection. For example, in the following screenshot, an Abandoned Cart custom event is further targeted by the "cart value" property filter. This campaign will only reach users who've left between $100 and $200 worth of goods in their carts.

![Custom Event Properties Pic][34]

Note that the trigger event "start session" can be the user's very first app open, if your campaign's segment applies to new users (for instance, if your segment consists of those with no sessions).

Keep in mind that you can still send a triggered campaign to a specific segment of users, so users who aren't a part of the segment won't be able to receive the campaign even if they complete the trigger event. If you notice users not receiving the campaign even though they qualified for the segment, please read our section on [reasons why a user might not have received a triggered campaign][49].

With respect to the trigger event for when a user adds an email address to their profile, the following rules apply:

- The trigger event will be fired after the user profile attribute updates. This means that the evaluation of the campaign's segments and filters will happen after the attribute updates. This is beneficial because it enables you do things like set up a filter of "email address matches gmail.com" to create a trigger campaign that only sends to Gmail users and fires as soon as they add their email address.
- The trigger event will fire when an email address is added to a user profile. If you have multiple user profiles that you create that have the same email address, the campaign may fire multiple times, once for each user profile.

In addition, triggered in-app messages still abide by [in-app message delivery rules][29] and will appear at the beginning of an app session.

![triggered 1][17]


__Step 2: Select how long to wait before sending the campaign, after the trigger criteria is met.__ Choose how long to delay your message after the user completes the trigger event.

In choosing your delay length, note that if you set a delay that is longer than the message's duration for sending (see Step 4), no users will receive your campaign. Additionally, users who complete the trigger event after your campaign is launched will be the first to start receiving the message once the delay has passed. Users who have completed the trigger event prior to the campaign launching will not qualify to receive the campaign.

![triggered 2][19]

You may also elect to send the campaign on either a specific day of the week (by choosing "on the next" and then selecting a day) or a specific number of days (by selecting "in") in the future. Choose the time you wish the user to receive your message on that day. Alternatively, you may choose to send your message using the [Intelligent Delivery][40] feature instead of manually selecting a delivery time.

![triggered 7][41]
![triggered 8][50]

__Step 3: Select an exception event that will disqualify users from receiving this campaign.__ You can only do this if your triggered message sends after a time delay. Exception events can be making a purchase, starting a session, performing one of a campaign's designated [conversion events][18], or performing a custom event. If a user completes the trigger event but then completes your exception event before the message sends due to the time delay, she will not receive the campaign. Users who do not receive the campaign due to the exception event will automatically be eligible to receive it in the future, the next time they complete the trigger event, even if you do not elect for users to become [re-eligible][24].

You can read more about how to employ exception events in our section on [use cases][22].

![triggered 3][20]

> If you are sending out a campaign with the trigger event equalling the same exception  event, the initial campaign will be cancelled. Instead of sending out both campaigns, your user's first campaign will be cancelled and we will automatically re-schedule a new campaign based on the exception event's message delivery time.
>
>For example, if your first trigger event starts at 5 minutes and the exception event's time starts at 10 minutes, you would rely on the exception event's 10 minutes as the official campaign's message delivery time). Please also note that you cannot make a "session start"  both the trigger event and exception event for a campaign (however, you always have the choice to select any other custom event outside of this option).



__Step 4: Assign the campaign's duration by specifying a start time and optional end time.__ If a user completes a trigger event during the specified time frame, but actually qualifies for the message outside of the time frame due to a scheduled delay, then she will not receive the campaign. Therefore, if you set a time delay that is longer than the message's time frame, no users will receive your campaign. In addition, you can elect to send the message in users' [local time zones][5].

![triggered 4][21]

__Step 5: Select whether the user will receive the campaign during a specific portion of the day.__ If you give the message a time frame and the user either completes the trigger event outside the time frame or the message delay causes her to miss the time frame, then by default the user will not receive your message.

![triggered 5][27]

In the case where a user completes the trigger event within the time frame, but the message delay causes the user to fall out of the time frame, you can check the box below so that these users will still receive the campaign:

![triggered next available][31]

If a user doesn't receive the message because she misses the time frame, then she will still be qualified to get it the next time she completes the trigger event, even if you did not elect for users to become [re-eligible][24]. If you do elect for users to become re-eligible, then users can receive the campaign each time they complete the trigger event, assuming they qualify during the specified time frame.

If you have also assigned the campaign a certain duration, then in order to receive the message, a user must qualify within both the duration and the specific portion of the day.

__Step 6: Determine whether users can become [re-eligible][24] for the campaign.__ If you allow users to become re-eligible, you may specify a time delay before the user can receive the campaign again. This will prevent your triggered campaigns from becoming spammy.

![triggered 6][28]


### Use Cases

Triggered campaigns are very effective for transactional or achievement-based messages.

Transactional campaigns include messages sent after the user completes a purchase or adds an item to her cart. The latter case is a great example of a campaign that would benefit from an exception event. Say your campaign reminds users of items in their cart that they haven't purchased. The exception event in this case would be the user buying the products in her cart. For achievement-based campaigns, you can send a message 5 minutes after the user completes a conversion or beats a game level.

In addition, when creating welcome campaigns, you can trigger messages to send after the user registers or sets up an account. Staggering messages to be sent on different days following registration will allow you to create a thorough [onboarding process][30].

### Why Did a User Not Receive My Triggered Campaign?

Any of these things will prevent a user who has completed the trigger event from receiving the campaign:

- The user completed the exception event before the time delay had fully elapsed.
- The time delay caused the user to become qualified to receive the campaign after the duration has ended.
- The time delay caused the user to become qualified to receive the campaign outside of the specified portion of the day.
- The user has already received the campaign, and users do not become re-eligible.
- While users are re-eligible to receive the campaign, they can only re-trigger it after a certain period of time, and that period of time has not yet elapsed.

[Segmenting][47] a triggered campaign on user data recorded at the time of the event may cause a _race condition_. This happens when a change in the user attribute on which the campaign is segmented hasn't yet been processed for the user at the time segment membership is determined and the campaign is sent, and can lead to the user not receiving the campaign.

For example, imagine you want to send an event-triggered campaign to male users who just registered. When the user registers, you record a custom event `registration`, and simultaneously set the user's `gender` attribute. The event may trigger the campaign before Braze has processed the user's gender, preventing them from receiving the campaign.

It is a best practice to make sure that the attribute on which the campaign is segmented is flushed to Braze's servers before the event. In cases where this is not possible, the best way to guarantee delivery is to use [Custom Event Properties][48] to attach the relevant user properties to the event, and apply a property filter for the specific event property instead of a segmentation filter. In the example above, you would add a `gender` property to the custom event `registration` so that Braze is guaranteed to have the data you need at the time your campaign is triggered.

## API Triggered Campaigns (Server Triggered Campaigns)

API Triggered Campaigns are ideal for more advanced transactional use-cases. Braze API Triggered Campaigns allow marketers to manage campaign copy, multivariate testing and re-eligibility rules within the Braze dashboard while triggering the delivery of that content from their own servers and systems. The API request to trigger the message can also include additional data to be templated into the message in real time.

### Setting up an API Triggered Campaign

Setting up an API Triggered Campaign is easy. First, create a new multichannel or single channel campaign (with multiviariate testing). Note that an API Triggered Campaign is different from an [API Campaign][46].

![API Triggered Creation Step][45]

Next, simply configure your copy and notifications the same way as you would were it a normally scheduled notification and select "API Triggered Delivery". For more information on the triggering of these campaigns from your server please see the documentation section on [API Triggered Campaigns][42].

![API Triggered Delivery Step][37]

### Using the Templated Content Included With an API request

In addition to triggering the message, you can also include content with the API request to be templated into the message within the `trigger_properties` object. This content can be referenced in the body of the message by saying something like
``{% raw %} {{ api_trigger_properties.${ some_value_included_with_request }}} {% endraw %}``.
See the following social notification example use-case for additional context:

![Social Example Delivery Window][38]

For information regarding triggering messages with API Triggered Delivery, please see [this section of our technical documentation][39].

### Re-eligibility with API Triggered Campaigns

The number of times a user receives an API triggered campaign can be limited using re-eligibility settings, meaning the user will receive the campaign only once, or once in a given window, regardless of how many times the API trigger is fired.

For example, if you are using an API triggered campaign to send the user a campaign about an item they recently viewed, you can limit the campaign to send a maximum of one message a day regardless of how many items they viewed while firing the API trigger for each item. On the other hand, if your API triggered campaign is transactional, you will want to make sure that the user receives the campaign every time they do the transaction by setting the delay to 0 minutes:

![Re-eligibility settings][43]

## Re-eligibility with Campaigns and Canvas

Whenever you schedule a recurring or triggered campaign or Canvas, you have the option of allowing users to become re-eligible for it. By default, Braze sends a message to a user only once, even if they re-qualify. By checking "Allow users to become re-eligible to receive campaign or re-enter this Canvas", you are overriding this default behavior and allowing qualified members to receive messages again once they've received the first instance of the campaign or Canvas. You can state the timeline on which users would ultimately become re-eligible.

Re-eligibility for Canvas variants is tied to Canvas entry rather than message receipt. Users who enter a Canvas and do not receive any messages will not be able to re-enter the Canvas unless re-eligibility is enabled. For example, let’s say that a user without an email address enters a daily recurring Canvas that contains one step. The Canvas step only contains an email message, so the user does not get the engagement. This user will not be able to enter the Canvas again, unless the Canvas has re-eligibility enabled. If you have an active recurring or triggered Canvas without re-eligibility, and you'd like users to re-enter the Canvas until they receive a message from it, you can consider allowing users to be re-eligible for entry by adding a filter to the entry criteria that excludes customers who’ve received a message from the Canvas.

In the case of triggered campaigns with re-eligibility turned on, users who [did not actually receive the campaign][26] (despite completing the trigger event) will automatically qualify for the message the next time they complete the trigger event, even if you did not make users re-eligible. By making users re-eligible for a triggered campaign, you are enabling them to actually receive (and not simply trigger) the message more than once.

Additionally, if you are trying to send a message immediately with a re-eligibility of 0 minutes, we will always attempt to schedule it right away regardless of how a user has received previous iterations of the Campaign or Canvas.

![re-eligible][24]

With regards to multivariate testing, Braze determines variant re-eligibility for all campaigns, triggered in-app messages, and Canvases using the following rules:

- When variant percentages are not changed, each user will always enter the same variant of a campaign, triggered in-app message, or Canvas entry every time they are re-eligible.
- If the variant percentages change, users may be redistributed to other variants.
- Control groups will remain consistent if the variant percentage is unchanged, and no users who previously received messages will ever enter the control group on a later send, nor will any user in the control group ever receive a message.

## Editing Campaigns After Launch

After launching your campaign, it's important to note what you can and cannot change and when the changes will come into effect.

### Content

Any content that is edited after your campaign is launched will be sent to your users correctly.

### Scheduling and Recipients

If you edit when your campaign is scheduled to send, or which users your campaign should be sent to, those changes won't be reflected in the actual campaign until after the current 24 hour period you are in ends.

### Send Rate

Changing the rate at which your messages will send will go into effect at the beginning of the next time zone that is set to be delivered to.


[1]: #scheduled-delivery
[2]: #immediately
[3]: {% image_buster /assets/img_archive/time_based.png %}
[4]: #designated
[5]: #local-time-zone-campaigns
[6]: #local-use
[7]: {{ site.baseurl }}/help/best_practices/user_onboarding/#user-onboarding
[8]: {{ site.baseurl }}/user_guide/engagement_tools/campaigns/scheduling_and_organizing/intelligent_delivery/#intelligent-delivery
[9]: {% image_buster /assets/img_archive/schedule_designated.png %}
[10]: {% image_buster /assets/img_archive/schedule_immediately.png %}
[11]: #delivery-rules
[12]: {{ site.baseurl }}/user_guide/engagement_tools/campaigns/scheduling_and_organizing/intelligent_delivery/#intelligent-delivery
[13]: #intelligent-use
[14]: {% image_buster /assets/img_archive/schedule_intelligent.png %}
[15]: #triggered
[16]: #setup
[17]: {% image_buster /assets/img_archive/schedule_triggered1.png %}
[18]: {{ site.baseurl }}/user_guide/engagement_tools/campaigns/testing_and_more/conversion_events/#conversion-events
[19]: {% image_buster /assets/img_archive/schedule_triggered22.png %}
[20]: {% image_buster /assets/img_archive/schedule_triggered32.png %}
[21]: {% image_buster /assets/img_archive/schedule_triggered43.png %}
[22]: #use-cases-2
[23]: #re-eligible
[24]: {% image_buster /assets/img_archive/ReEligible.png %}
[25]: {{ site.baseurl }}/help/faqs/#how-does-local-time-zone-delivery-work
[26]: #why-did-a-user-not-receive-my-triggered-campaign
[27]: {% image_buster /assets/img_archive/schedule_triggered5.png %}
[28]: {% image_buster /assets/img_archive/schedule_triggered6.png %}
[29]: {{ site.baseurl }}/help/best_practices/in-app_messages/in-app_message_behavior/#in-app-message-delivery-rules
[30]: {{ site.baseurl }}/help/best_practices/user_onboarding/#user-onboarding
[31]: {% image_buster /assets/img_archive/schedule_triggered_next_available.png %}
[32]: {{ site.baseurl }}/user_guide/data_and_analytics/custom_data/custom_events/
[33]: {{ site.baseurl }}/user_guide/engagement_tools/campaigns/scheduling_and_organizing/campaign_connector/#campaign-connector
[34]: {% image_buster /assets/img_archive/customEventProperties.png %}
[34]: {% image_buster /assets/img_archive/customEventProperties.png %}
[37]: {% image_buster /assets/img_archive/api_triggered_campaign_delivery.png %}
[38]: {% image_buster /assets/img_archive/api_trigger_photo_social_example_1.png %}
[39]: {{ site.baseurl }}/developer_guide/rest_api/messaging/#sending-messages-via-api-triggered-delivery
[40]: {{ site.baseurl }}/user_guide/engagement_tools/campaigns/scheduling_and_organizing/intelligent_delivery/#intelligent-delivery
[41]: {% image_buster /assets/img_archive/schedule_triggered7.png %}
[42]: {{ site.baseurl }}/developer_guide/rest_api/messaging/#sending-messages-via-api-triggered-delivery
[43]: {% image_buster /assets/img_archive/api-trigger-reeligible.png %}
[45]: {% image_buster /assets/img_archive/api_triggered_creation_step.png %}
[46]: {{ site.baseurl }}/developer_guide/rest_api/api_campaigns/#api-campaigns
[47]: {{ site.baseurl }}/user_guide/engagement_tools/campaigns/scheduling_and_organizing/scheduling_your_campaign/#why-did-a-user-not-receive-my-triggered-campaign
[48]: {{ site.baseurl }}/user_guide/data_and_analytics/custom_data/custom_events/#custom-event-properties
[49]: {{ site.baseurl }}/help/help_articles/campaigns_and_canvas/not_triggering/
[50]: {% image_buster /assets/img_archive/schedule_triggered8.png %}
