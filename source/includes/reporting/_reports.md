Saved Reports
===========

Get Report Data
----------------

> Example request

```shell
curl -X GET https://api.segmetrics.io/<account_id>/report/<report_type>/<report_id>            
     -H 'Authorization: YOUR_API_KEY'
     -H 'Content-Type: application/json'
     -d start=2020-01-01 \
     -d end=2020-11-24 \
     -d scale=day \
```

Retrieves all key metrics, for the specified report and time period.

### Endpoint

**GET** `/<account_id>/report/<report_type>/<report_id>`

### Path parameters

Parameter | Description
------------- | -------------
`account_id` | Account API id available from your Account Settings Page
`report_type` | The report type that you would like to query. One of: `leads`, `revenue`, `ads` or `subscriptions`
`report_id` | *(Optional)* The ID of the saved report that you would like to return

### Optional parameters

Parameter | Description
------------- | -------------
`start` | The start date of the required period of data. Either a [Relative DateTime](https://www.php.net/manual/en/datetime.formats.relative.php), or an ISO-8601 formatted date, e.g. 2020-01-01
`end` | The end date of the required period of data. Either a [Relative DateTime](https://www.php.net/manual/en/datetime.formats.relative.php), or an ISO-8601 formatted date, e.g. 2020-01-01
`scale` | Breakdown for the graph metrics. One of `day` (default), `week`, or `month`



Customer Journey
----------------

> Example request

```shell
curl -X GET https://api.segmetrics.io/<account_id>/report/<report_type>/<report_id>/contacts            
     -H 'Authorization: YOUR_API_KEY'
     -H 'Content-Type: application/json'
     -d start=2020-01-01 \
     -d end=2020-11-24 \
     -d extend=tags,events
```

> Example response

```json
{
  "data" : [
    {
      "contact_id": "1004",
      "first_name": "Linda",
      "last_name": "Dare",
      "email": "linda.dare@example.com",
      "status": "active",
      "date_created": "2021-12-18T19:07:50+00:00",
      "last_updated": "2021-12-31T00:00:00+00:00",
      "custom_fields": {
        "City": "Mortimerville",
        "State": "UT",
        "Phone1": "780.555.3533",
        ...
      },
      "orders": [
        {
          "order_id": "26",
          "contact_id": "1012",
          "is_paid": true,
          "is_refunded": false,
          "subtotal": 500,
          "total_tax": 0,
          "total_shipping": 0,
          "total_discount": 0,
          "total": 500,
          "total_paid": 500,
          "date_created": "2021-12-12T20:32:11+00:00",
          "line_items": [
            {
              "contact_id": "1012",
              "order_item_id": "894689",
              "product_id": null,
              "order_id": "26",
              "subscription_id": null,
              "product_name": "Launching a Marketing Plan",
              "order_type": "product",
              "is_paid": true,
              "is_refunded": false,
              "amount": 500,
              "total_paid": 500,
              "total_due": 500,
              "date_created": "2021-12-12T20:32:11+00:00",
              "imported_at": "2021-12-12T20:32:11+00:00",
              "last_imported_at": "2021-12-31T00:00:00+00:00"
            }
          ]
        }
      ],
      "events": [
        {
          "type": "page_view",
          "contact_id": "1004",
          "uid": null,
          "fingerprint": null,
          "date_created": "2021-12-18T19:07:50+00:00",
          "ip_address": "3159:c782:bf13:9cdc:6b0d:c76b:d20a:5167",
          "country_code": "BV",
          "region": "port",
          "city": "North Benton",
          "postal_code": "39433",
          "latitude": "1.490988",
          "longitude": "-174.138608",
          "url": "https://example.com./top-page",
          "full_url": "https://example.com./top-page?utm_campaign=Retargeting&utm_medium=cpc&utm_source=fb&utm_term=WARM+Retarget&utm_content=RT+-+Testimonial+-+J&ad_id=559675250&fbclid=1",
          "referrer": "lifehacker.com",
          "host": "example.com",
          "path": "/top-page",
          "args": {
            "utm_campaign": "Retargeting",
            "utm_medium": "cpc",
            "utm_source": "fb",
            "utm_term": "WARM Retarget",
            "utm_content": "RT - Testimonial - J",
            "ad_id": "559675250",
            "fbclid": 1,
            "sega_prod": null
          },
          "meta": null,
          "channel": "paid",
          "utm_source": "fb",
          "utm_medium": "cpc",
          "utm_campaign": "Retargeting",
          "utm_term": "WARM Retarget",
          "utm_content": "RT - Testimonial - J",
          "ad_id": "559675250"
        },
        ...
      ]
    } ...
  ],  
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 5,    
    "path": "https://api.segmetrics.io/example/report/ads/contacts",
    "per_page": 20,
    "to": 20,
    "total": 85
  }
}
```

Retrieves the customer journey for all contacts in the specified report and time period.

### Endpoint

**GET** `/<account_id>/report/<report_type>/<report_id>/contacts`

### Path parameters

Parameter | Description
------------- | -------------
`account_id` | Account API id available from your Account Settings Page
`report_type` | The report type that you would like to query. One of: `leads`, `revenue`, `ads` or `subscriptions`
`report_id` | *(Optional)* The ID of the saved report that you would like to return

### Optional parameters

Parameter | Description
------------- | -------------
`start` | The start date of the required period of data. Either a [Relative DateTime](https://www.php.net/manual/en/datetime.formats.relative.php), or an ISO-8601 formatted date, e.g. 2020-01-01
`end` | The end date of the required period of data. Either a [Relative DateTime](https://www.php.net/manual/en/datetime.formats.relative.php), or an ISO-8601 formatted date, e.g. 2020-01-01
`extend` | By default only the core contact data is returned. If you would like to include other data, you can do so by adding a CSV of the following options: `events`, `tags`, `orders`, `subscriptions`, `lists`. e.g. `events,tags`
`limit` | Number of records to return in a page, 1 - 100 (Default 20)
`page` | Result page to return
