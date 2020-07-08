# Identifying Visitors

## Connect a Contact to the Current Web Session

> Example identify request

```javascript
_segq.push(["identify", "john@example.com"]);
```


The `identify` command lets you tie a contact in your email marketing platform to their actions on the website. 
It includes an email address, and automatically connects to the current session.

<aside class="notice">
In most cases SegMetrics will automatically identify a contact when they enter their email address on your optin forms,
or when they follow a link from an email.

You will only need to use the identify command if the marketing pages you are using are preventing SegMetrics from
automatically identifying the user.  
</aside>


### Tracking Without the JavaScript API

> Manually Identifying a User

```shell
curl -X GET -G https://track.segmetrics.io/identify     
     -d account_id=YOUR_ACCOUNT_ID
     -d seg_uid=SESSION_UID
     -d email=john@example.com     
```

In some cases you may want to manually identify a contact when you don't have access to the JavaScript API,
either through a webhook or backend system like Zapier.

In that case, you can make a standard HTTP request with the same information to connect a Session UID to a contact. 

The Session UID is always available in `_segs.data.uid`
