Contact API
===========

Retrieves the full customer journey for a single contact.
----------------

> Example request

```shell
curl -X GET https://api.segmetrics.io/<account_id>/contact/<contact_id_or_email>            
     -H 'Authorization: YOUR_API_KEY'
     -H 'Content-Type: application/json'
     -d extend=tags,events
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
