Products
===========

Add Product
----------------

> Example request

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/tags/add \
     -H 'Authorization: YOUR_API_KEY' \
     -H 'Content-Type: application/json' \
     -d '{
           "contact_id": 249,
           "tags": [ 3, 45, 8 ]
         }'
```

Adds a product to the specified SegMetrics integration.

<aside class="notice">
If the `id` already exists, the existing product will be updated.
</aside>

### Endpoint

**POST** `/v1/<account_id>/<integration_id>/product`

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
`id` | Product Id
`name` | Name of the Product
