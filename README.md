## Features

This unofficial Facebook Ads API will make it easier and faster for you to extract advertising data and insights from Facebook Ads, including information about your competitors.

Facebook Ads Scraper supports the following functionality:

-   **Scrape ad details** - You can scrape advertisement details such as end date, number of assets used, advertiser, CDN URL of assets, creation date, platform, and much more.

-   **Scrape advertisements by filters** - Apply filters so that you only get the results you need.

-   **Scrape advertisers** - If you're looking for data on a specific advertiser's ads, you can directly target them.

-   **Scrape by keyword** - Search and extract data based on any keyword. You can also directly select country and advertisement type using this feature.

## Suggested use cases
-   **Competitor analysis**: Get detailed information about your competitor's Facebook ads strategy.
-   **Data Analysis**: Analyze Facebook Ads data for any country, category, and keyword.
-   **Signals**: Get notified about new ads or campaigns in specific countries, categories, and keywords.

## Tutorial
Check out [how to scrape Facebook Ads without using Facebook Ads API](https://blog.apify.com/how-to-scrape-facebook-ads-without-using-facebook-ads-api/) for more tips on using the scraper.

## Bugs, fixes, updates, and changelog
This scraper is under active development. If you have any feature requests, please create an issue from [here](https://github.com/tugkan/facebookads-scraper/issues).

## Setup & usage
Learn how Facebook Ads Scraper works in these videos:

### Using Start URLs
[![Apify - Facebook Ads Scraper - Start URLs](https://img.youtube.com/vi/UvnerqFkVmo/0.jpg)](https://www.youtube.com/watch?v=UvnerqFkVmo)

You can check the dataset from this video [here](https://api.apify.com/v2/datasets/82Df92jrg9M0xkeYE/items?clean=true&format=json).

### Using Search
[![Apify - Facebook Ads Scraper - Search](https://img.youtube.com/vi/VJHdodVbIbg/0.jpg)](https://www.youtube.com/watch?v=VJHdodVbIbg)

You can check the dataset from this video [here](https://api.apify.com/v2/datasets/kHg9dhIXLQu29XfRh/items?clean=true&format=json).

## Input parameters
The input for this scraper should be JSON containing the list of pages on Facebook Ads that should be visited. Required fields are:

| Field     | Type    | Description                                                                                                                                                                        |
| --------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| startURLs | Array   | (optional) List of Facebook Ads URLs. You should only provide advertiser detail, location, or listing/search URLs.                                                                   |
| maxItems  | Integer | (optional) You can limit the number of objects to be scraped. This is useful when scraping big subcategories.                                                                     |
| search    | String  | (optional) Keyword that can be searched in the Facebook Ads search engine. When this is present, `adType` and `country` must also be used.                                            |
| country   | String  | (optional) 2-digit country code that needs to be provided if `search` keyword is provided. It can be used to target/filter results by country.                             |
| adType    | String  | (optional) Ad type is required when the `search` keyword is required. Not all of the types exist for all countries, so `all` is strongly recommended. |
| endPage   | Integer | (optional) The total number of page that you want to scrape. The default is `Infinite`.                                                                                                    |
| proxy     | Object  | Proxy configuration                                                                                                                                                                |

This solution **requires the use of proxy servers**. You can use either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Specific Facebook Ads
Don't worry if you get slightly different advertisements than you see in a browser page. Facebook Ads orders ads differently for each user, depending on the location, language, and the user who is logged in.

### Tip
When you want to filter a search URL, go to Facebook Ads, create filters for the search list, and copy and paste the link as one of the **start URLs**.

If you would like to scrape only the first page of a search list, add the link for the page and set the `endPage` as 1.

If you would like to scrape a specific advertiser, just open its profile on the website, then copy and paste the link as one of the **start URLs**.

## Compute unit consumption
The actor is optimized to run extremely fast and scrape many as ads as possible, so it forefronts all advertisement detail requests. If the actor doesn't get blocked very often, it will scrape 100 ads in 2 minutes and consume ~0.15-0.20 compute units.

## Future improvements
-   Performance optimizations
-   Advertisement detail URLs as start URLs

## Facebook Ads Scraper Input example
```json
{
    "startUrls": [
        {
            "url": "https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=US&view_all_page_id=127843679186911&sort_data[direction]=desc&sort_data[mode]=relevancy_monthly_grouped&search_type=page&media_type=all"
        }
    ],
    "proxy": {
        "useApifyProxy": true,
        "groups": ["RESIDENTIAL"]
    },
    "endPage": 1,
    "maxItems": 50,
    "adType": "all",
    "country": "US",
    "search": "game"
}
```

## During the run
During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Facebook Ads data export
During the run, the actor stores the results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node.js/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from Facebook Ads Scraper.

## Scraped Facebook Ads output example
The structure of each item in Facebook Ads products looks like this:

```json
{
    "adid": "0",
    "adArchiveID": "782129142700742",
    "archiveTypes": [1],
    "categories": [0],
    "collationCount": 1,
    "collationID": 135949371832895,
    "currency": "",
    "endDate": 1619074800,
    "entityType": "regular_page",
    "fevInfo": null,
    "gatedType": "eligible",
    "hiddenSafetyData": false,
    "impressionsWithIndex": {
        "impressionsText": null,
        "impressionsIndex": -1
    },
    "isActive": true,
    "isProfilePage": false,
    "pageID": "127843679186911",
    "pageInfo": null,
    "pageIsDeleted": false,
    "pageName": "Rollic.",
    "politicalCountries": [],
    "reachEstimate": null,
    "reportCount": null,
    "snapshot": {
        "ad_creative_id": "23847372222400297",
        "cards": [],
        "body_translations": {},
        "byline": "",
        "caption": "apps.apple.com",
        "cta_text": "Game spelen",
        "dynamic_item_flags": {},
        "dynamic_versions": null,
        "edited_snapshots": [],
        "effective_authorization_category": "NONE",
        "event": [],
        "extra_images": [],
        "extra_links": [],
        "extra_texts": [],
        "extra_videos": [],
        "instagram_shopping_products": [],
        "display_format": "video",
        "title": null,
        "link_description": null,
        "link_url": "https://apps.apple.com/us/app/id1560643139",
        "page_welcome_message": null,
        "images": [],
        "videos": [
            {
                "video_hd_url": "https://video-ams4-1.xx.fbcdn.net/v/t42.1790-2/172943907_470300817616146_6153901163633194118_n.?_nc_cat=107&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=UBNV8d57huEAX9qu7DC&_nc_ht=video-ams4-1.xx&oh=eb31c7ff2a11e94dfa5bb676e4bec503&oe=60BD425C",
                "video_sd_url": "https://video-amt2-1.xx.fbcdn.net/v/t42.1790-2/173605913_843387012914883_1867447470221682759_n.mp4?_nc_cat=109&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=y5J0S1GEIt0AX8oyOJk&_nc_ht=video-amt2-1.xx&oh=ad0dc8539cb54fda9c0146c8b89933c5&oe=60BD441D",
                "video_preview_image_url": "https://scontent-ams4-1.xx.fbcdn.net/v/t39.35426-6/173506127_1070020040160602_8115173755307321180_n.jpg?_nc_cat=107&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=wwzbtozmWYsAX9XqflF&_nc_ht=scontent-ams4-1.xx&oh=1d8bb0f2af9ca7829370ea97c0fca76b&oe=60E43F90"
            }
        ],
        "creation_time": 1618463859,
        "page_id": 127843679186911,
        "page_name": "Rollic.",
        "page_profile_picture_url": "https://scontent-ams4-1.xx.fbcdn.net/v/t39.35426-6/s60x60/173286758_928737564608958_6613835230238664499_n.jpg?_nc_cat=108&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=j7ZftmvrVukAX-EPBmT&_nc_ht=scontent-ams4-1.xx&tp=7&oh=236d83acc3e6b757e85630a115fb5ff3&oe=60E36DD2",
        "page_categories": {
            "211579738882707": "Brand",
            "866898430141631": "Media/News Company"
        },
        "page_entity_type": "regular_page",
        "page_is_profile_page": false,
        "instagram_actor_name": "Rollic.",
        "instagram_profile_pic_url": "https://scontent-amt2-1.xx.fbcdn.net/v/t39.35426-6/171993136_146852247293530_5340708282215521594_n.jpg?_nc_cat=109&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=0J-bBMjklxYAX_1Tiom&_nc_ht=scontent-amt2-1.xx&oh=0fa53cae6f75a28c698a01be421fe3be&oe=60E2F3CA",
        "instagram_url": "",
        "instagram_handle": "",
        "is_reshared": false,
        "version": 3,
        "body": {
            "context": {},
            "markup": {
                "__html": ""
            },
            "callerHash": null
        },
        "brazil_tax_id": null,
        "branded_content": null,
        "current_page_name": "Rollic.",
        "disclaimer_label": null,
        "page_like_count": 97,
        "page_profile_uri": "https://www.facebook.com/gamesrollic/",
        "page_is_deleted": false,
        "root_reshared_post": null,
        "cta_type": "PLAY_GAME",
        "additional_info": null,
        "ec_certificates": null,
        "country_iso_code": null,
        "instagram_branded_content": null
    },
    "spend": null,
    "startDate": 1618383600,
    "stateMediaRunLabel": null,
    "publisherPlatform": [
        "facebook",
        "instagram",
        "audience_network",
        "messenger"
    ],
    "menuItems": [],
    "adCards": [
        {
            "adid": 0,
            "adArchiveID": 782129142700742,
            "archiveTypes": [1],
            "categories": [0],
            "collationCount": null,
            "collationID": 135949371832895,
            "currency": "",
            "endDate": 1619074800,
            "entityType": "regular_page",
            "fevInfo": null,
            "gatedType": "eligible",
            "hiddenSafetyData": false,
            "impressionsWithIndex": {
                "impressionsText": null,
                "impressionsIndex": -1
            },
            "isActive": true,
            "isProfilePage": false,
            "pageID": 127843679186911,
            "pageInfo": null,
            "pageIsDeleted": false,
            "pageName": "Rollic.",
            "politicalCountries": [],
            "reachEstimate": null,
            "reportCount": null,
            "snapshot": {
                "ad_creative_id": "23847372222400297",
                "cards": [],
                "body_translations": {},
                "byline": "",
                "caption": "apps.apple.com",
                "cta_text": "Game spelen",
                "dynamic_item_flags": {},
                "dynamic_versions": null,
                "edited_snapshots": [],
                "effective_authorization_category": "NONE",
                "event": [],
                "extra_images": [],
                "extra_links": [],
                "extra_texts": [],
                "extra_videos": [],
                "instagram_shopping_products": [],
                "display_format": "video",
                "title": null,
                "link_description": null,
                "link_url": "https://apps.apple.com/us/app/id1560643139",
                "page_welcome_message": null,
                "images": [],
                "videos": [
                    {
                        "video_hd_url": "https://video-ams4-1.xx.fbcdn.net/v/t42.1790-2/172943907_470300817616146_6153901163633194118_n.?_nc_cat=107&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=UBNV8d57huEAX9qu7DC&_nc_ht=video-ams4-1.xx&oh=eb31c7ff2a11e94dfa5bb676e4bec503&oe=60BD425C",
                        "video_sd_url": "https://video-amt2-1.xx.fbcdn.net/v/t42.1790-2/173605913_843387012914883_1867447470221682759_n.mp4?_nc_cat=109&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=y5J0S1GEIt0AX8oyOJk&_nc_ht=video-amt2-1.xx&oh=ad0dc8539cb54fda9c0146c8b89933c5&oe=60BD441D",
                        "video_preview_image_url": "https://scontent-ams4-1.xx.fbcdn.net/v/t39.35426-6/173506127_1070020040160602_8115173755307321180_n.jpg?_nc_cat=107&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=wwzbtozmWYsAX9XqflF&_nc_ht=scontent-ams4-1.xx&oh=1d8bb0f2af9ca7829370ea97c0fca76b&oe=60E43F90"
                    }
                ],
                "creation_time": 1618463859,
                "page_id": 127843679186911,
                "page_name": "Rollic.",
                "page_profile_picture_url": "https://scontent-ams4-1.xx.fbcdn.net/v/t39.35426-6/s60x60/173286758_928737564608958_6613835230238664499_n.jpg?_nc_cat=108&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=j7ZftmvrVukAX-EPBmT&_nc_ht=scontent-ams4-1.xx&tp=7&oh=236d83acc3e6b757e85630a115fb5ff3&oe=60E36DD2",
                "page_categories": {
                    "211579738882707": "Brand",
                    "866898430141631": "Media/News Company"
                },
                "page_entity_type": "regular_page",
                "page_is_profile_page": false,
                "instagram_actor_name": "Rollic.",
                "instagram_profile_pic_url": "https://scontent-amt2-1.xx.fbcdn.net/v/t39.35426-6/171993136_146852247293530_5340708282215521594_n.jpg?_nc_cat=109&ccb=1-3&_nc_sid=cf96c8&_nc_ohc=0J-bBMjklxYAX_1Tiom&_nc_ht=scontent-amt2-1.xx&oh=0fa53cae6f75a28c698a01be421fe3be&oe=60E2F3CA",
                "instagram_url": "",
                "instagram_handle": "",
                "is_reshared": false,
                "version": 3,
                "body": {
                    "context": {},
                    "markup": {
                        "__html": ""
                    },
                    "callerHash": null
                },
                "brazil_tax_id": null,
                "branded_content": null,
                "current_page_name": "Rollic.",
                "disclaimer_label": null,
                "page_like_count": 97,
                "page_profile_uri": "https://www.facebook.com/gamesrollic/",
                "page_is_deleted": false,
                "root_reshared_post": null,
                "cta_type": "PLAY_GAME",
                "additional_info": null,
                "ec_certificates": null,
                "country_iso_code": null,
                "instagram_branded_content": null
            },
            "spend": null,
            "startDate": 1618383600,
            "stateMediaRunLabel": null,
            "publisherPlatform": [
                "facebook",
                "instagram",
                "audience_network",
                "messenger"
            ],
            "menuItems": []
        }
    ]
}
```
