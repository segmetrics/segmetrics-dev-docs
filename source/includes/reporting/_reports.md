Saved Reports
===========

Retrieves all key metrics, for the specified report and time period.
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

Returns a saved report, or a new report of the set type.

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
