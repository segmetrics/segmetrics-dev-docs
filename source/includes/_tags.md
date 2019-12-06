Tags
===========

Add Tags to Contact
----------------

> Example request (Tag Ids)

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/tags/add \
     -H 'Authorization: YOUR_API_KEY' \
     -H 'Content-Type: application/json' \
     -d '{
           "contact_id": 249,
           "tags": [ 3, 45, 8 ]
         }'
```

> Example request (Tag Names)

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/tags/add \
     -H 'Authorization: YOUR_API_KEY' \
     -H 'Content-Type: application/json' \
     -d '{
           "contact_id": 249,
           "tags": [
               "New Lead",
               "2018 Holiday Special",
               "Platinum Customer"
           ]
         }'
```

> Example request (Tag Objects)

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/tags/add \
     -H 'Authorization: YOUR_API_KEY' \
     -H 'Content-Type: application/json' \
     -d '{
           "contact_id": 249,
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
             }
           ]
         }'
```

Tags can be submitted in three different ways depending on how they're available in your application. Examples are shown to the right.

### Endpoint

**POST** `/v3/<account_id>/<integration_id>/tags/add`

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
`tags` | Array of Tags.


### Tag Format

Parameter | Description
------------- | -------------
`id` | Tag Id
`name` | Tag Name
`date` | DateTime the Tag was applied (defaults to now)

Remove Tags to Contact
----------------

> Example request (Tag Ids)

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/tags/remove \
     -H 'Authorization: YOUR_API_KEY' \
     -H 'Content-Type: application/json' \
     -d '{
           "contact_id": 249,
           "tags": [ 3, 45, 8 ]
         }'
```

> Example request (Tag Names)

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/tags/remove \
     -H 'Authorization: YOUR_API_KEY' \
     -H 'Content-Type: application/json' \
     -d '{
           "contact_id": 249,
           "tags": [
               "New Lead",
               "2018 Holiday Special",
               "Platinum Customer"
           ]
         }'
```

> Example request (Tag Objects)

```shell
curl -X POST https://import.segmetrics.io/api/v1/<account_id>/<integration_id>/tags/remove \
     -H 'Authorization: YOUR_API_KEY' \
     -H 'Content-Type: application/json' \
     -d '{
           "contact_id": 249,
           "tags": [
             {
               "id": 3,
               "name": "New Lead"
             },
             {
               "id": 45,
               "name": "2018 Holiday Special"
             }
           ]
         }'
```

Tags can be submitted in three different ways depending on how they're available in your application. Examples are shown to the right.

### Endpoint

**POST** `/v3/<account_id>/<integration_id>/tags/remove`

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
`tags` | Array of Tags.


### Tag Format

Parameter | Description
------------- | -------------
`id` | Tag Id
`name` | Tag Name
