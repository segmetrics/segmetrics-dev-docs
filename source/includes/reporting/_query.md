Ad-hoc Report Query
===================

Run any report definition against the SegMetrics data layer. This endpoint accepts the same `reportQuery` payload that the in-app Data Explorer builds, so anything you can configure visually can also be fetched via the API.

<aside class="notice">
The easiest way to get a valid payload is to open any report in the SegMetrics app, open the report-actions menu, and choose <strong>Access from API</strong>. The app generates a ready-to-run <code>curl</code> command — pre-filled with your account id, API key, and the exact JSON body for the current explorer state — pointed at this endpoint. We recommend starting there for any first-time integration, then editing the resulting payload to suit your needs.
</aside>

Run a Report Query
------------------

> Example request

```shell
curl -X POST --location "https://api.segmetrics.io/v2/<account_id>/data/query" \
     -H "Content-Type: application/json" \
     -H "Authorization: YOUR_API_KEY" \
     -d '{
        "type": "leads",
        "dimensions": ["clicks.channel"],
        "metrics": ["leads", "revenue"],
        "date_range": {
            "start": "-30 day",
            "end": "now",
            "scale": "day"
        },
        "filters": [],
        "options": {
            "attribution_model": "last_touch",
            "include_source": true
        }
     }'
```

> Example response

```json
{
    "type": "leads",
    "fields": [
        {
            "name": "Channel",
            "key": "channel",
            "type": "STRING",
            "aggregation": null
        },
        {
            "name": "Leads",
            "key": "leads",
            "type": "NUMBER",
            "aggregation": "SUM"
        },
        {
            "name": "Revenue",
            "key": "revenue",
            "type": "CURRENCY",
            "aggregation": "SUM"
        }
    ],
    "rows": [
        ["paid", 33, 2900],
        ["social", 2, 0],
        ["direct", 7, 450]
    ],
    "totals": [42, 3350],
    "date_range": {
        "start_date": "2026-04-20",
        "end_date": "2026-05-20",
        "scale": "day"
    },
    "comparison": null,
    "v": "2022-06"
}
```

Executes an ad-hoc report query and returns the raw result set (`fields` + `rows`), the same payload the Data Explorer renders into a chart or table.

### Endpoint

**POST** `/v2/<account_id>/data/query`

<aside class="warning">
Unlike the other Reporting endpoints, this endpoint is served under the <code>/v2/</code> prefix.
</aside>

### Path parameters

Parameter | Description
------------- | -------------
`account_id` | Account API id available from your Account Settings Page

### Body parameters

Send the body as `application/json`. Most fields are arrays/objects mirroring what the in-app Data Explorer builds — refer to the **Access from API** modal for a copy of the exact shape currently in use.

Parameter | Description
------------- | -------------
`type` | Report type slug. One of `leads`, `revenue`, `ads`, `subscriptions`, `funnel`, etc.
`dimensions` | Array of dimension slugs to group by, e.g. `["clicks.channel"]`
`metrics` | Array of metric slugs to return, e.g. `["leads", "revenue"]`
`date_range` | Object: `{ "start", "end", "scale" }`. `start` / `end` accept [Relative DateTime](https://www.php.net/manual/en/datetime.formats.relative.php) strings (e.g. `-30 day`) or ISO-8601 dates. `scale` is one of `day`, `week`, `month`.
`filters` | Array of filter objects scoping the report.
`steps` | Array of funnel-step definitions. *Funnel reports only.*
`options` | Object of report-wide options. Common keys: `attribution_model`, `include_source`.
`compare` | *(Optional)* Comparison period — same shape as `date_range`. When present, returns a `comparison` block in the response.
