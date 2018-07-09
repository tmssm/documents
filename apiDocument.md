# Mediumin api usage for publisher

## Get offers by api request

### API request url
`http://api.mediumin.com/offers/?aff_id={yourAffId}&aff_token={yourAffToken}`

replace aff_id and aff_token you own.


## Response
response is in json format.


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
|icon|string|icon url |`"https://lh3.googleusercontent.com/demo.icon"`|
|app_category|string|category show on app shop |"Tools"|


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
            "icon": "",
            "app_category": "Tools"
        }
    ]
}
```
## Tracking link
you can pass these parameters to us.

|Field|Type|Description|
|----|----|--------------|
|aff_sub|string|your clickid|
|sub_channel|string|your channel|
|gaid|string|Google Advertising ID|
|idfa|string|ios bundle id|
|aff_sub2|string|your custom parameter|
|aff_sub3|string|your custom parameter|
|aff_sub4|string|your custom parameter|
|aff_sub5|string|your custom parameter|

### example
`http://tr.mediumin.com/aff_c?offer_id=101191479200702&aff_id=10001&aff_sub=a1233&sub_channel=128`

## Postback
you can login our channel dashboard to set postback.

login url: `http://channel.mediumin.com/channel/#/login`

postback support parameters.


|Field|Type|Description|
|----|----|--------------|
|aff_sub|string|your clickid|
|sub_channel|string|your channel|
|gaid|string|Google Advertising ID|
|idfa|string|ios bundle id|
|aff_sub2|string|your custom parameter|
|aff_sub3|string|your custom parameter|
|aff_sub4|string|your custom parameter|
|aff_sub5|string|your custom parameter|
|payout|string|offer price|
|offer_id|string|offer id in our system|
|country|string| which country click occurs,like `"US"`|


### example 
if your postback is `http://pb.my.com/pb?clickid={aff_sub}&price={payout}`

we will request `http://pb.my.com/pb?clickid=a1233&price=0.2` to postback to you.










