Getting started
=========================

## Overview

Welcome to the SegMetrics API!

The SegMetrics API v1 is a way to enable customer to import their own data into their SegMetrics account, either through a custom integration,
or to modify existing information in their integrations.

Calls for the SegMetrics API v1 are relative to the url:
`https://import.segmetrics.io/api/v1/<account_id>/<integration_id/`

API v1 is in active development.

## Authentication

The SegMetrics API uses two pieces of information to authorize your account.

> Authorization

```shell
curl "https://import.segmetrics.io/api/v1/<account_id>/<integration_id/<endpoint>" \  
  -H 'Authorization: YOUR_API_KEY'
  -H 'Content-Type: application/json'
```

- Your `Account ID` is appended to the URL of each request that you'll make to the API
- Your `API Key` is sent as an authorization header on each request.

You can find your `Account Id` and `API Key` in the [SegMetrics Account page](https://app.segmetrics.io/a/account/edit).

## Responses

> Successful Call

```json
{
    "status": "success"
}
```

When an API call succeeds, the API will return a 200 HTTP response and a JSON response body unless otherwise noted.

If there's an error, the API will return an HTTP response in the 400 or 500 range and a response body indicating what caused the error.


### Bad data

When you create or update a field, you may receive an HTTP 400 if any fields contain bad data or required fields are missing.

> Missing Data

```json
{
    "status": "error",
    "errors": [
        "missing 'id' field "
    ]
}
```

### Internal server errors

If the server is overloaded or you encounter a bug, you will get a 500 error. 
Try again after a short period, and if you continue to encounter an error, please raise the issue with support.
