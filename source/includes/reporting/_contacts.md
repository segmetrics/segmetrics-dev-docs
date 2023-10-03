Contact API
===========

Get Contact
----------------

> Example request

```shell
curl -X GET https://api.segmetrics.io/<account_id>/contact/<contact_id_or_email>            
     -H 'Authorization: YOUR_API_KEY'
     -H 'Content-Type: application/json'
     -d extend=tags,events
```

> Example response

```json
{
  "data": {
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
    "tags": [
      {
        "tag_id": "115",
        "name": "marketing-blueprint",
        "contact_id": "1060",
        "date_created": "2021-11-18T05:07:44+00:00"
      },
      ...
    ],
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
  }
}
```

Returns the full customer journey of a single contact, either by email or contact_id.

### Endpoint

**GET** `/<account_id>/contact/<contact_id_or_email>`

### Path parameters

Parameter | Description
------------- | -------------
`account_id` | Account API id available from your Account Settings Page
`contact_id_or_email` | The email address or external contact_id of the contact to return

### Optional parameters

Parameter | Description
------------- | -------------
`extend` | By default only the core contact data is returned. If you would like to include other data, you can do so by adding a CSV of the following options: `events`, `tags`, `orders`, `subscriptions`, `lists`. e.g. `events,tags`
