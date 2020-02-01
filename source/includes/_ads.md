Ads
===========

Record Ad Performance
----------------

> Example request

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/ad/performance
     -H 'Authorization: YOUR_API_KEY'
     -H 'Content-Type: application/json'
     -d '{
           "ad": 5489788855,
           "adcampaign": {             
              "id": 123456789,
              "name": "My Amazing Ad Campaign",
           },
           "adset": {             
              "id": 5678910,
              "name": "My Amazing Ad Set",
              "adcampaign": 123456789,
           },           
           "spend": 4500,
           "clicks": 7844,
           "impressions": 15487,
           "date": "2018-10-03",           
         }'
```

Adds the add performance for a specific day to SegMetrics.

The AdPerformance endpoint allows passing the Ad Set and Ad Campaign values
in addition to the performance to allow users to skip campaign creation API calls
in order to simplify performance. 

<aside class="notice">
If the `ad` and `date_created` already exists, the existing ad performance will be updated.
</aside>

### Endpoint

**POST** `/v3/<account_id>/<integration_id>/ad/performance`

### Path parameters

Parameter | Description
------------- | -------------
`account_id` | Account API id available from your Account Settings Page
`integration_id` | This is the ID of the integration from your Account Settings Page

### Request Body Schema
`application/json`

### Required parameters

Parameter | Description
------------- | -------------
`ad` | The Id of the Ad. Alternately, an `ad` object may be passed (see below)
`spend` | Amount spent on the ad for this day in Cents
`date` | Date that the clicks, spend and impressions apply to

### Optional parameters

Parameter | Description
------------- | -------------
`adcampaign` | The `adcampaign` object that the ad belongs to (see below)
`adset` | The `adset` object that the ad belongs to (see below)
`clicks` | Number of clicks on the ad for this day
`impressions` | Number of impressions on the ad for this day

### Ad Object Required Parameters
`ad` may be passed as either an existing ID or an object.
 If an object is passed, then the `ad` will be created in SegMetrics, similar to if the **Create Ad** 
 endpoint was being called, with the following values:

Parameter | Description
------------- | -------------
`id` | Id of the Ad
`name` | Name of the Ad
`adcampaign` | Ad Campaign Id of the Ad
`adset` | Ad Set Id of the Ad

### AdSet Object Required Parameters
`adset` may be passed as either an existing ID or an object.
 If an object is passed, then the `AdSet` will be created in SegMetrics, similar to if the **Create AdSet** 
 endpoint was being called, with the following values:

Parameter | Description
------------- | -------------
`id` | Id of the AdSet
`name` | Name of the AdSet
`adcampaign` | Ad Campaign Id of the AdSet

### AdCampaign Object Required Parameters
`adcampaign` may be passed as either an existing ID or an object.
 If an object is passed, then the `Campaign` will be created in SegMetrics, similar to if the **Create AdCampaign** 
 endpoint was being called, with the following values:

Parameter | Description
------------- | -------------
`id` | Id of the Ad Campaign
`name` | Name of the Ad Campaign
