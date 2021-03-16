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
           "status": 'active',
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
           ],
           "custom_fields": {
                "shirt_size": "Medium",
                "Awesome Sauce": "Applesauce2"
           }
         }'
```

Adds a contact to the specified SegMetrics integration.

<aside class="notice">
If the `contact_id` already exists, the existing contact will be updated.
</aside>

### Endpoint

**POST** `/v1/<account_id>/<integration_id>/contact`

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
`contact_id` | Contact Id (Required if no contact email)
`email` | Contact Email Address (Required if no contact_id)

<aside class="notice">
When looking for a contact to update, the API gives priority to the contact_id over email.<br/>
When passing a contact_id, if the email address already exists, that contact_id will be updated with the new id. 
</aside>


### Optional parameters

Parameter | Description
------------- | -------------
`date_created` | Date Created
`first_name` | Contact First Name
`last_name` | Contact Last Name
`status` | Optin status of the contact. `active` or `inactive` (defaults to `active`)
`tags` | List of TagIds or Array of Tag Objects
`custom_fields` | Object containing custom field data. E.g. `{ "shirt_size": "Medium" }`.
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

<aside class="notice">
When updating `custom_fields`, data will be **appended** to the existing data.<br/>
When updating `tags`, data will *replace* the existing data. Use `tags/add` to add tags to a contact. 
</aside>

Delete Contact
----------------

> Example request

```shell
curl -X DELETE https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/contact/<contact_id_or_email>
     -H 'Authorization: YOUR_API_KEY'
```

> Successful Response

```json
{
    "id": "CONTACT_ID",
    "status": "success",
    "object": "contact",
    "deleted": true
}
```

Permanently deletes a contact from SegMetrics. This cannot be undone.<br/> 
This will not delete any invoices or purchases from the contact in the same integration.

### Endpoint

**DELETE** `/v1/<account_id>/<integration_id>/contact/<contact_id_or_email>`

### Path parameters

Parameter | Description
------------- | -------------
`account_id` | Account API id available from your Account Settings Page
`integration_id` | This is the ID of the integration from your Account Settings Page
`contact_id_or_email` | Contact Id or Email Address of the contact to delete.

<aside class="notice">
If the delete contact request is made with an email address all contacts in the integration that use the same email address will be deleted.
</aside>
