Contacts
===========

Add or Update Contact
----------------

> Example request

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/contact
     -H 'Authorization: YOUR_API_KEY'
     -H 'Content-Type: application/json'
     -d '{
           "contact_id": 249,
           "first_name": "Joey",
           "last_name": "Bloggs",
           "email": "joey@bloggs.com",
           "date_created": "2018-10-02 16:15:00",
           "last_updated": "2018-11-28 09:28:42",
           "utm_source": "facebook",
           "utm_content": "holiday special",
           "utm_medium": "facebook",
           "utm_campaign": "holiday",
           "utm_term": "awesomeness",
           "referring_url": "reallycoolurl.com",
           "optin_url": "evencoolerurl.com",
           "ip_address": "8.8.8.8",
           "affiliate_id": "123",
           "geo_lat": "45.523064",
           "geo_lon": "-122.676483",
           "tags": [
             {
               "id": 3,
               "name": "New Lead",
               "date": "2018-10-02 16:15:00"
             },
             {
               "id": 45,
               "name": "2018 Holiday Special",
               "date": "2018-11-28 09:25:33"
             },
             {
               "id": 8,
               "name": "Platinum Customer",
               "date": "2018-11-28 09:28:42"
             }
           ]
         }'
```

Adds a contact to the specified SegMetrics integration.

<aside class="notice">
If the `contact_id` already exists, the existing contact will be updated.
</aside>

### Endpoint

**POST** `/v3/<account_id>/<integration_id>/contact`

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
`contact_id` | Contact Id
`email` | Contact Email Address


### Optional parameters

Parameter | Description
------------- | -------------
`date_created` | Date Created
`first_name` | Contact First Name
`last_name` | Contact Last Name
`tags` | List of TagIds or Array of Tag Objects
`last_updated` | Date Last Updated
`utm_campaign` | UTM Campaign
`utm_content` | UTM Content
`utm_medium` | UTM Medium
`utm_source` | UTM Source
`utm_term` | UTM Term
`referring_url` | Referring URL
`optin_url` | Optin URL
`ip_address` | IP Address
`affiliate_id` | Affiliate ID
`geo_lat` | Geographic Latitude
`geo_lon` | Geographic Longitude
