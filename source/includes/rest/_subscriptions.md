Subscriptions
===========

Add Subscription
----------------

> Example request

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/subscription
     -H 'Authorization: YOUR_API_KEY'
     -H 'Content-Type: application/json'
     -d '{
           "email": "mwiegand@gmail.com",
           "id": 234115,
           "amount": 4500,
           "product_id": 108,
           "start_date": "2019-12-03 11:14:32",
           "last_bill_date": "2019-12-03 11:14:32",
           "billing_cycle": "month",
           "frequency": 1
         }'
```

Adds a subscription to the existing contact. If the subscription id already exist, it will be updated.
<aside class="warning">
Adding a subscription **does not** create a corresponding order. That must be done separately.
If the specified product does not exist in SegMetrics, one will be created.
</aside>

### Endpoint

**POST** `/v1/<account_id>/<integration_id>/subscription`

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
`id` | Subscription Id
`contact_id` | Contact Id (Required if no contact email)
`email` | Contact's Email (Required if no contact id)
`amount` | Subscription Total in Cents
`product_id` | Product Id that the Subscription applies to
`start_date` | DateTime that the Subscription started
`last_bill_date` | DateTime that the Subscription was last billed
`billing_cycle` | One of `year`, `month`, `week` or `day` The frequency with which a subscription should be billed.
`frequency` |  The number of intervals (specified in the `billing_cycle` property) between subscription billings. For example, `billing_cycle=month` and `frequency=3` bills every 3 months.

<aside class="notice">
When sending a `contact_id` with the subscription, that contact <strong>MUST</strong> already exist in SegMetrics.<br/>
If the contact may or may not exist already, <strong>ONLY</strong> send the email, and SegMetrics will automatically
match the contact on the next data sync.
</aside>

### Optional parameters

Parameter | Description
------------- | -------------
`name` | Product Name that the Subscription applies to
`quantity` | The quantity of the plan to which the customer is subscribed. Defaults to 1
`trial_end_date` | If the subscription has a trial, the end of that trial.
`end_date` | A date in the future at which the subscription will automatically get canceled
`canceled_date` | If the subscription has been canceled, the date of that cancellation.


Delete Subscription
----------------

> Example request

```shell
curl -X DELETE https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/subscription/<id>
     -H 'Authorization: YOUR_API_KEY'
```

> Successful Response

```json
{
    "id": "SUBSCRIPTION_ID",
    "status": "success",
    "object": "subscription",
    "deleted": true
}
```

Permanently deletes a subscription from SegMetrics. This cannot be undone.

### Endpoint

**DELETE** `/v1/<account_id>/<integration_id>/subscription/<id>`

### Path parameters

Parameter | Description
------------- | -------------
`account_id` | Account API id available from your Account Settings Page
`integration_id` | This is the ID of the integration from your Account Settings Page
`id` | Id of the Subscription to delete
