# Identifying Visitors

## Connect a Contact to the Current Web Session

> Identify by email (string form)

```javascript
_segq.push(["identify", "john@example.com"]);
```

> Identify by contact id, email, or both (object form)

```javascript
_segq.push(["identify", { email: "john@example.com", contact_id: "abc123" }]);

// Contact id only — no email required
_segq.push(["identify", { contact_id: "abc123" }]);
```

The `identify` command lets you tie a contact in your email marketing platform to their actions on the website. 
You can identify a contact by their email address, by the `contact_id` from an external system, or both. The call automatically connects to the current session.

If neither a valid email nor a `contact_id` is supplied, the call is dropped (fail-closed).

<aside class="notice">
In most cases SegMetrics will automatically identify a contact when they enter their email address on your optin forms,
or when they follow a link from an email.

You will only need to use the identify command if the marketing pages you are using are preventing SegMetrics from
automatically identifying the user.  
</aside>


### Tracking Without the JavaScript API

> Manually Identifying a User by Email

```shell
curl -X GET -G https://track.segmetrics.io/identify \
     -d a=YOUR_ACCOUNT_ID \
     -d uid=SESSION_UID \
     -d e=john@example.com
```

> Manually Identifying a User by Contact ID

```shell
curl -X GET -G https://track.segmetrics.io/identify \
     -d a=YOUR_ACCOUNT_ID \
     -d uid=SESSION_UID \
     -d cid=abc123
```

> Identifying a User by Both Email and Contact ID

```shell
curl -X GET -G https://track.segmetrics.io/identify \
     -d a=YOUR_ACCOUNT_ID \
     -d uid=SESSION_UID \
     -d e=john@example.com \
     -d cid=abc123
```

In some cases you may want to manually identify a contact when you don't have access to the JavaScript API,
either through a webhook or backend system like Zapier.

In that case, you can make a standard HTTP request with the same information to connect a Session UID to a contact. 

The Session UID is always available in `_segs.data.uid`. If you do not have a Session UID, one will be generated automatically from the `cid` or `e` value you supply.

### Parameters

Parameter | Description
------------- | -------------
`a` | Account API id available from your Account Settings Page. **Required.**
`uid` | Session UID for the current web session (available in `_segs.data.uid`). Optional — if omitted, a UID is derived from `cid` or `e`.
`e` | Contact email address. Either `e` or `cid` must be supplied — both may be supplied together.
`cid` | Opaque contact id from an external system. Either `e` or `cid` must be supplied — both may be supplied together.
