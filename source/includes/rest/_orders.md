Orders
===========

Add Purchase to Contact
----------------

> Example request

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/invoice
     -H 'Authorization: YOUR_API_KEY'
     -H 'Content-Type: application/json'
     -d '{
           "contact_id": 4,
           "id": 234115,
           "amount": 4500,
           "paid": 4500,
           "is_refunded": 0,
           "date_created": "2018-10-03 11:14:32",
           "items": [
             {
               "name": "Round Tuit",
               "product_id": 1556402307145,
               "amount": 4000,
               "total_paid": 4000
             },
             {
               "name": "Uber Trinket",
               "product_id": 82638,
               "amount": 500,
               "total_paid": 500
             }
           ]
         }'
```

Adds a purchase to the specified SegMetrics integration.

<aside class="notice">
If the `id` already exists, the existing invoice will be updated.
</aside>

### Endpoint

**POST** `/v1/<account_id>/<integration_id>/invoice`

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
`id` | Invoice Id
`contact_id` | Contact Id (Required if no contact email)
`email` | Contact's Email (Required if no contact id)
`amount` | Invoice Total in Cents
`paid` | Invoice Amount Paid in Cents
`date_created` | Invoice Date
`items` | Array of Invoice Items

<aside class="notice">
When sending a `contact_id` with the invoice, that contact <strong>MUST</strong> already exist in SegMetrics.<br/>
If the contact may or may not exist already, <strong>ONLY</strong> send the email, and SegMetrics will automatically
match the contact on the next data sync.
</aside>

### Optional parameters

Parameter | Description
------------- | -------------
`is_refunded` | Invoice Refunded Flag
`discount` | Invoice discount amount in Cents
`tax` | Invoice tax amount in Cents
`shipping` | Invoice shipping amount in Cents

### Item Parameters

For each invoice, include the line items of which products were included.
If the product does not exist in SegMetrics, one will be created.

Parameter | Description
------------- | -------------
`name` | Product Name
`product_id` | Product Id
`amount` | Product Price in Cents
`subscription_id` | (optional) The ID of the Subscription that the purchase is connected to 


Delete Invoice
----------------

> Example request

```shell
curl -X DELETE https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/invoice/<id>
     -H 'Authorization: YOUR_API_KEY'
```

> Successful Response

```json
{
    "id": "INVOICE_ID",
    "status": "success",
    "object": "invoice",
    "deleted": true
}
```

Permanently deletes an invoice from SegMetrics. This cannot be undone.

### Endpoint

**DELETE** `/v1/<account_id>/<integration_id>/invoice/<id>`

### Path parameters

Parameter | Description
------------- | -------------
`account_id` | Account API id available from your Account Settings Page
`integration_id` | This is the ID of the integration from your Account Settings Page
`id` | Id of the Invoice to delete
