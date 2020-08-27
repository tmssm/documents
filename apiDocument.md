# Mediumin Bulk API Documentation

## Get offers via api request

### API request url
`http://api.mediumin.com/offers/?aff_id={yourAffId}&aff_token={yourAffToken}`

Get aff_id and aff_token from your account manager.

|Field|Require|Description|Example|
|----|----|--------------|----------------|
|aff_id|YES|your aff_id| / |
|aff_token|YES|your aff_token| / |
|get_creatives|NO|set '1' if you need creatives,default '0'|'1'|

## Response
Response is in json format.


|Field|Type|Description|Example|
|----|----|--------------|----------------|
|error|boolean|when success,error=false|false|
|counts|int|offer counts|1200|
|data|offer[]|offers array|[{"id":"112...}...]|

### Offer
|Field|Type|Description|Example|
|----|----|--------------|----------------|
|id|string|offer id|"101191479200702"|
|offer_name|string|offer name|"facebook in jp"|
|tracking_link|string|our click url|`"http://tr.mediumin.com/aff_c?offer_id=101191479200702&aff_id=10001"`|
|offer_desc|string|offer description |"facebook is a popular app..."|
|offer_price|string|offer price(USD) |"0.12"|
|pricing_model|string|offer payout type |"cpi"|
|daily_cap|number|offer daily conversion limit |30|
|regions|string| countries code,uppercase,split by `,` |"US,JP"|
|kpi|string|offer kpi |"CVR < 3% ..."|
|app_title|string|app name|"Facebook"|
|package|string|package id or apple bundle id|"com.facebook.demo"|
|os|string|operator system,android/ios/other|"android"|
|os_version|string|operator system version|"4.0"|
|icon|string|icon url |`"https://lh3.googleusercontent.com/demo.icon"`|
|app_category|string|category show on app shop |"Tools"|
|creatives|string|creatives of offer|`"http://cdn..."`|
|preview_url|string|the preview url of the offer|`"https://itunes.apple.com/il/app/..."`|
|block_subs|array|your subs that should be blocked|["203","311"]|
|white_subs|array\|null|your subs that can access.if null,offer is block sub mode|["201","sub33"]|
|app_name_required|boolean|app name is required(aff_sub5 in Tracking link) if true|false|
|target_network|string|network operator|"U MOBILE"|
|target_model|string|conver model|"2 CLICKS"|
|impression_link|string|impression link|`"http://tr.mediumin.com/aff_c?offer_id=101191479200702&aff_id=10001"`|

### Example
```
{
    "error": false,
    "counts": 1,
    "data": [
        {
            "id": 101181498899914,
            "offer_name": "Words With Friends2 Android [US]",
            "tracking_link": "http://tr.mediumin.com/aff_c?offer_id=101181498899914&aff_id=1018",
            "kpi": "CVR below 3% and 2nd retention rate >10%;Traffic KPI: none Incent,no fraud,no cheating,no adult",
            "offer_desc": "",
            "offer_price": "2.06",
            "currency": "USD",
            "pricing_model": "cpi",
            "daily_cap": 0,
            "regions": "US",
            "package": "com.zynga.words3",
            "app_title": "",
            "os": "android",
            "os_version": "",
            "icon": "",
            "creatives": "",
            "preview_url: "",
            "description": "",
            "app_category": "Tools",
            "block_subs":[],
            "white_subs":null
        }
    ]
}
```
## Tracking link
You can pass these parameters to us.

|Field|Type|Description|
|----|----|--------------|
|aff_sub|string|your clickid|
|sub_channel|string|your channel|
|gaid|string|Google Advertising ID|
|idfa|string|ios bundle id|
|aff_sub2|string|your custom parameter|
|aff_sub3|string|impression id|
|aff_sub4|string|app name|
|aff_sub5|string|application bundle that click occus on |
|ip|string|IP address(for example: 13.14.255.1) Only for ios ver >= 14|
|language|string|Language(for example: en-US) Only for ios ver >= 14|
|user_agent|string|User agent, should be URL encode, for example: "Mozilla%2F5.0+%28iPhone%3B+CPU+iPhone+OS+13_6+like+Mac+OS+X%29+AppleWebKit%2F605.1.15+%28KHTML%2C+like+Gecko%29+Mobile%2F15E148" Only for ios ver >= 14|

### Example
`http://tr.mediumin.com/aff_c?offer_id=101191479200702&aff_id=10001&aff_sub=a1233&sub_channel=128`

## Postback
You are able to login in the dashboard to set postback.

Login url: `http://channel.mediumin.com/channel/#/login`

Postback support parameters:

|Field|Type|Description|
|----|----|--------------|
|aff_sub|string|your clickid|
|imp_id|string|your impression id|
|sub_channel|string|your channel|
|gaid|string|Google Advertising ID|
|idfa|string|ios bundle id|
|aff_sub2|string|your custom parameter|
|aff_sub3|string|impression id|
|aff_sub4|string|app name|
|aff_sub5|string|application bundle that click occus on |
|payout|string|offer price|
|offer_id|string|offer id in our system|
|country|string| which country click occurs,like `"US"`|


### Example 
If your postback is `http://pb.my.com/pb?clickid={aff_sub}&price={payout}`

We will request `http://pb.my.com/pb?clickid=a1233&price=0.2` to postback to you.


## Event Postback

Event Postback support parameters:

|Field|Type|Description|
|----|----|--------------|
|aff_sub|string|your clickid|
|event_name|string|event name|
|event_value|string|event value|
|event_time|string|the time event occurs|

Contact the AM if you need the event postback.




