---
nav_title: Setting Custom Attributes
platform: iOS
page_order: 3
search_rank: 5
---
# Setting Custom Attributes

Braze provides methods for assigning attributes to users. You'll be able to filter and segment your users according to these attributes on the dashboard.

Before implementation, be sure to review examples of the segmentation options afforded by Custom Events vs. Custom Attributes vs Purchase Events in our [Best Practices section][1], as well as our notes on [event naming conventions]({{ site.baseurl }}/user_guide/data_and_analytics/custom_data/event_naming_conventions/).

## Assigning Standard User Attributes

To assign user attributes, you need to set the appropriate field on the shared `ABKUser` object. For example, to assign the current user's first name to be "Jeff," you would use the following line of code:

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[Appboy sharedInstance].user.firstName = @"Jeff";
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.firstName = "Jeff"
```

{% endtab %}
{% endtabs %}

The following attributes should be set on the `ABKUser` object:

- `firstName`
- `lastName`
- `email`
- `dateOfBirth`
- `country`
- `language`
- `homeCity`
- `bio`
- `phone`
- `userID`
- `avatarImageURL`
- `twitterAccountIdentifier`
- `gender`

__We strongly recommend collecting email addresses__ even if you're not sending emails through Braze. Email makes it easier to search for individual user profiles and troubleshoot issues as they arise.

## Assigning Custom User Attributes

Beyond the attributes above, Braze also allows you to define Custom Attributes using a number of different data types:
For more information regarding the segmentation options each of these attributes will afford you see our ["Best Practices" documentation][1] within this section.

### Custom Attribute with a Boolean Value

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[[Appboy sharedInstance].user setCustomAttributeWithKey:@"your-attribute-string" andBOOLValue:yourBOOLValue];
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.setCustomAttributeWithKey("your-attribute-string", andBOOLValue: yourBoolValue)
```

{% endtab %}
{% endtabs %}

### Custom Attribute with an Integer Value

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[[Appboy sharedInstance].user setCustomAttributeWithKey:@"your-attribute-string" andIntegerValue:yourIntegerValue];
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.setCustomAttributeWithKey("your-attribute-string", andIntegerValue: yourIntegerValue)
```

{% endtab %}
{% endtabs %}

### Custom Attribute with a Double Value

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[[Appboy sharedInstance].user setCustomAttributeWithKey:@"your-attribute-string" andDoubleValue:yourDoubleValue];
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.setCustomAttributeWithKey("your-attribute-string", andDoubleValue: yourDoubleValue)
```

{% endtab %}
{% endtabs %}

>  Braze treats FLOAT and DOUBLE values exactly the same within our database.

### Custom Attribute with a String Value

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[[Appboy sharedInstance].user setCustomAttributeWithKey:@"your-attribute-string" andStringValue:"Your String"];
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.setCustomAttributeWithKey("your-attribute-string", andStringValue: "Your String")
```

{% endtab %}
{% endtabs %}

### Custom Attribute with a Date Value

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[[Appboy sharedInstance].user setCustomAttributeWithKey:@"your-attribute-string" andDateValue:yourDateValue];
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.setCustomAttributeWithKey("your-attribute-string", andDateValue:yourDateValue)
```

{% endtab %}
{% endtabs %}

>  Dates passed to Braze with this method must either be in the [ISO 8601][2] format, e.g `2013-07-16T19:20:30+01:00` or in the `yyyy-MM-dd'T'HH:mm:ss.SSSZ` format e.g `2016-12-14T13:32:31.601-0800`

### Custom Attribute with an Array Value
The maximum number of elements in Custom Attribute Arrays defaults to 25. The maximum for individual arrays can be increased to up to 100 in the Braze Dashboard, under "Manage App Group -> Custom Attributes". Arrays exceeding the maximum number of elements will be truncated to contain the maximum number of elements. For more information on Custom Attribute Arrays and their behavior, see our [Documentation on Arrays][8].

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
// Setting a custom attribute with an array value
[[Appboy sharedInstance].user setCustomAttributeArrayWithKey:@"array_name" array:@[@"value1",  @"value2"]];
// Adding to a custom attribute with an array value
[[Appboy sharedInstance].user addToCustomAttributeArrayWithKey:@"array_name" value:@"value3"];
// Removing a value from an array type custom attribute
[[Appboy sharedInstance].user removeFromCustomAttributeArrayWithKey:@"array_name" value:@"value2"];
// Removing an entire array and key
[[Appboy sharedInstance].user setCustomAttributeArrayWithKey:@"array_name" array:nil];
```

{% endtab %}
{% tab swift %}

```swift
// Setting a custom attribute with an array value
Appboy.sharedInstance()?.user.setCustomAttributeArrayWithKey("array_name", array: ["value1",  "value2"])
// Adding to a custom attribute with an array value
Appboy.sharedInstance()?.user.addToCustomAttributeArrayWithKey("array_name", value: "value3")
// Removing a value from an array type custom attribute
Appboy.sharedInstance()?.user.removeFromCustomAttributeArrayWithKey("array_name", value: "value2")
```

{% endtab %}
{% endtabs %}

### Unsetting a Custom Attribute

Custom Attributes can also be unset using the following method:

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[[Appboy sharedInstance].user unsetCustomAttributeWithKey:@"your-attribute-string"];
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.unsetCustomAttributeWithKey("your-attribute-string")
```

{% endtab %}
{% endtabs %}

### Incrementing/Decrementing Custom Attributes

This code is an example of an incrementing custom attribute. You may increment the value of a custom attribute by any positive or negative integer or long value.

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[[Appboy sharedInstance].user incrementCustomUserAttribute:@"Attribute Key" by:incrementIntegerValue];
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.incrementCustomUserAttribute("Attribute Key", by: incrementIntegerValue)
```

{% endtab %}
{% endtabs %}

### Setting a Custom Attribute via the REST API

You can also use our REST API to set user attributes. To do so refer to the [user API documentation][3].

### Custom Attribute Value Limits

Custom attribute values have a maximum length of 255 characters; longer values will be truncated.

#### Implementation Example

User Attributes are set within the [`UserAttributesViewController.m` file][4] within the Stopwatch sample application.

- More details can be found within the [`ABKUser.h` file][5].
- In addition, you may refer to the [ABKUser documentation][6] for more information.
- Additional examples of setting arrays as user attributes can be found within [`UserAttributesArrayViewController.m`][7] in the Stopwatch sample application.

## Setting Up User Subscriptions

To set up a subscription for your users (either email or push), call the functions `setEmailNotificationSubscriptionType` or `setPushNotificationSubscriptionType`, respectively. Both of these functions take the enum type `ABKNotificationSubscriptionType` as arguments. This type has three different states:

| Subscription Status | Definition |
| ------------------- | ---------- |
| `ABKOptedin` | Subscribed, and explicitly opted in |
| `ABKSubscribed` | Subscribed, but not explicitly opted in |
| `ABKUnsubscribed` | Unsubscribed and/or explicitly opted out |

Users who grant permission for an app to send them push notifications are defaulted to the status of `ABKOptedin` as iOS requires an explicit opt in.

> Users will be set to `ABKSubscribed` automatically upon receipt of a valid email address, however we suggest that you establish an explicit opt-in process and set this value to `OptedIn` upon receipt of explicit consent from your user. [See the User Guide for details][12].

### Setting Email Subscriptions

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[[Appboy sharedInstance].user setEmailNotificationSubscriptionType: ABKNotificationSubscriptionType]
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.setEmailNotificationSubscriptionType(ABKNotificationSubscriptionType)
```

{% endtab %}
{% endtabs %}

### Setting Push Notification Subscriptions

{% tabs %}
{% tab OBJECTIVE-C %}

```objc
[[Appboy sharedInstance].user setPushNotificationSubscriptionType: ABKNotificationSubscriptionType]
```

{% endtab %}
{% tab swift %}

```swift
Appboy.sharedInstance()?.user.setPushNotificationSubscriptionType(ABKNotificationSubscriptionType)
```

{% endtab %}
{% endtabs %}

>  Users who grant permission for an app to send them push notifications are defaulted to the status of `ABKOptedin` as iOS requires an explicit optin.

For more information on implementing subscriptions, visit our page on [managing user subscriptions][10].

[1]: {{ site.baseurl }}/developer_guide/platform_wide/analytics_overview/#user-data-collection
[2]: http://en.wikipedia.org/wiki/ISO_8601
[3]: {{ site.baseurl }}/developer_guide/rest_api/user_data/#user-data
[4]: https://github.com/Appboy/appboy-ios-sdk/blob/master/Example/Stopwatch/UserAttributesViewController.m
[5]: https://github.com/Appboy/appboy-ios-sdk/blob/master/AppboyKit/headers/AppboyKitLibrary/Appboy.h
[6]: http://appboy.github.io/appboy-ios-sdk/docs/interface_a_b_k_user.html
[7]: https://github.com/Appboy/appboy-ios-sdk/blob/master/Example/Stopwatch/UserAttributesArrayViewController.m
[8]: {{ site.baseurl }}/developer_guide/platform_wide/analytics_overview/#arrays
[10]: {{ site.baseurl }}/user_guide/message_building_by_channel/email/managing_user_subscriptions/#managing-user-subscriptions
[12]: {{ site.baseurl }}/user_guide/message_building_by_channel/email/managing_user_subscriptions/#managing-user-subscriptions
