---
nav_title: Public APIs
platform: Message_Building_and_Personalization
subplatform: Personalization
page_order: 5
---

# Public APIs

There are a variety of publicly available APIs that can be used for Connected Content. As seen in the examples above, public APIs allow you to insert custom data in messages.  We've compiled a list below of public APIs that could be used for Connected Content. However, there are many more APIs out there, providing a wide variety of potential Connected Content uses.  [Let us know](mailto:success@braze.com) if you have an API to share!

>  Public APIs can be subject to usage restrictions and rate limiting.  Be sure to read through API documentations and contact API providers about your intended use.

### News and Information

|	 API 	| Description |
| --------- | --- |
| [OpenWeatherMap][7] | Provides current weather data, 5 and 16 day forecast, and historical data. |
| [NYT Article Search][8] | Provides NYT article data which includes headline, topic, URL, date, abstract, etc. |
| [The Guardian API][9] | Provides Guardian article data which includes headline, topic, URL, date, abstract, etc.|
| [Alchemy][10] | Provides data from an index of 250-300 thousand news articles and blogs. |

### Events and Ticketing

|	 API 	| Description |
| --------- | --- |
| [SeatGeek][11]| Provides ticket information for concerts, sports, and theater events.  |
| [OnConnect][12] | Provides box-office movie information and showtimes in US and Canadian theaters. |
| [Eventbrite][19] | Provides data on a variety of public events. |
| [Eventful][20] | Provides data on a variety of public events |
| [Ticketmaster][38] | Provides data on public events, venues, and prices |

### Food & Drink

|  API  | Description |
| --------- | --- |
| [BreweryDB][40] | Provides information on breweries, beers, and beer events. |
| [Zomato][41] | Provides a variety of restaurant information, including ratings, locations, and cuisine. |

### Finance

|  API  | Description |
| --------- | --- |
| [Barchart OnDemand][36] | Provides a variety of stock, futures, and foreign exchange data. |
| [CoinDesk][37] | Provides a variety of cryptocurrency data. |
| [Yahoo Finance][23] | Provides a variety of stock data. |

### Health

|  API  | Description |
| --------- | --- |
| [AirVisual][42] | Provides Air quality and weather data. |
| [Nutritionix Worlds][43] | Provides verified nutrition data. |
| [openFDA][44] | Provides FDA data on drugs, devices, and foods |
| [USDA Nutrients][45] | Provides access to the National Nutrient Database. |

### Music

|	 API 	| Description |
| --------- | --- |
| [Last.fm][14] | Provides a variety of music data including artist information, recommended artists, and more. |
| [iTunes][24] | Provides data on a variety of items in the iTunes, App Store, and iBooks stores. |
| [Bandsintown][13] | Provides local concert information and recommends live music events. |
| [Songkick][22] | Provides live music information with artists, venues, locations, etc. |
| [Discogs][21] | Provides information on artists, labels, and recordings. |

### Product Information

|	 API 	| Description |
| --------- | --- |
| [Semantics3][25] | Provides product metadata in a variety of categories. |
| [Factual][26] | Provides various product data including nutrition and ingredients data. |
| [eBay][15] | Provides live eBay data including item data, popular searches, and more. |

### Miscellaneous

|	 API 	| Description |
| --------- | --- |
| [Numbers API][18] | Provides random numerical trivia facts. |
| [Clearbit][27] | Provides company logo images. |
| [London Unified][28] and [NYC MTA][29] | Provide realtime public transit data including line statuses, arrival times, etc. |
| [Sunrise and Sunset][39] | Provides Sunset and sunrise times for a given latitude and longitude. |

[1]: #aborting-connected-content
[6]: {% image_buster /assets/img_archive/Connected_Content_Syntax.png %} "Connected Content Syntax Usage Example"
[7]: http://openweathermap.org/api
[8]: http://developer.nytimes.com/docs/read/article_search_api_v2
[9]: http://open-platform.theguardian.com/documentation/
[10]: http://alchemyapi.readme.io/v1.0/docs/introduction
[11]: http://platform.seatgeek.com/
[12]: http://developer.tmsapi.com/docs/read/data_v1_1/movies/movie_showtimes
[13]: http://www.bandsintown.com/api/overview
[14]: http://www.last.fm/api
[15]: http://developer.ebay.com/devzone/shopping/docs/concepts/shoppingapiguide.html
[16]: [success@braze.com](mailto:success@braze.com)
[17]: {% image_buster /assets/img_archive/connected_weather_push2.png %} "Connected Content Push Usage Example"
[18]: http://numbersapi.com/
[19]: http://developer.eventbrite.com/
[20]: http://api.eventful.com/
[21]: http://www.discogs.com/developers/
[22]: http://www.songkick.com/developer
[23]: http://www.enclout.com/api/v1/yahoo_finance
[24]: http://www.apple.com/itunes/affiliates/resources/documentation/itunes-store-web-service-search-api.html
[25]: http://www.semantics3.com/products/pull
[26]: http://factual.com/products/cpg
[27]: http://blog.clearbit.com/logo
[28]: http://api.tfl.gov.uk/#Line
[29]: http://datamine.mta.info/
[30]: {{ site.baseurl }}/user_guide/personalization_and_dynamic_content/connected_content/about_connected_content/
[31]: https://docs.transifex.com/api/translation-strings
[32]: {% image_buster /assets/img_archive/TransifexUI.png %}
[33]: {% image_buster /assets/img_archive/terminal.png %}
[34]: {% image_buster /assets/img_archive/basic_auth_mgmt.png %}
[35]: {% image_buster /assets/img_archive/basic_auth_token.png %}
[36]: https://www.barchartondemand.com/free
[37]: https://www.coindesk.com/api/
[38]: http://developer.ticketmaster.com/products-and-docs/apis/getting-started/
[39]: https://sunrise-sunset.org/api
[40]: http://www.brewerydb.com/
[41]: https://developers.zomato.com/api
[42]: https://airvisual.com/api
[43]: https://developer.nutritionix.com/
[44]: https://open.fda.gov/api/
[45]: https://ndb.nal.usda.gov/ndb/doc/index
[46]: http://www.json.org
[47]: {{ site.baseurl }}/user_guide/engagement_tools/campaigns/testing_and_more/rate-limiting/#delivery-speed-rate-limiting
[48]: https://developer.accuweather.com/accuweather-locations-api/apis
[49]: https://developer.accuweather.com/accuweather-forecast-api/apis
[50]: https://developer.accuweather.com/accuweather-current-conditions-api/apis
[51]: https://developer.accuweather.com/accuweather-indices-api/apis
[52]: https://developer.accuweather.com/accuweather-weather-alarms-api/apis
[53]: https://developer.accuweather.com/accuweather-alerts-api/apis
[54]: https://developer.accuweather.com/accuweather-imagery-api/apis
[55]: https://developer.accuweather.com/accuweather-tropical-api/apis
[56]: https://developer.accuweather.com/accuweather-translations-api/apis
[57]: https://developer.accuweather.com
[58]: https://developer.accuweather.com/user/me/apps
[59]: https://developer.accuweather.com/weather-alarm-thresholds
[60]: {% image_buster /assets/img_archive/Accuweather_APIKey2.png %}
[61]: https://developer.accuweather.com/weather-icons
[62]: {{ site.baseurl }}/user_guide/personalization_and_dynamic_content/connected_content/about_connected_content/
