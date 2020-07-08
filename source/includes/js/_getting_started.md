<h1 id="js_getting_started">Getting Started</h1>

The SegMetrics tracking snippet has a number of API methods for performing tasks right from your website,
such as identifying contacts and tracking page views.
This document details everything you can do via our JavaScript API.

## Installing Your JavaScript Snippet

> The snippet for your site generally looks something like this:

```html
<!-- SegMetrics  -->
<script type="text/javascript">
  var _segq = _segq || [];
  var _segs = _segs || {};
  _segs.integration = `your account id`;

  (function(){var dc=document.createElement('script');
    dc.type='text/javascript';dc.async=true;
    dc.src='//tag.segmetrics.io/seg.js';
    var s=document.getElementsByTagName('script')[0];
    s.parentNode.insertBefore(dc,s);})();
</script>
<!-- end SegMetrics  -->
```

To interact with the JavaScript API, you'll need to have your SegMetrics snippet installed on your website. 
Each SegMetrics account has a unique snippet that can be found under [Settings → Site Setup](https://app.segmetrics.io/a/settings/snippet).

## How to Send a JS API Request

```javascript
_segq.push(["methodName", { key: "value", ... }]);
```

All requests follow the same conventions. If you've ever worked with the Google Analytics API, the code should look familiar. This is the basis structure of an API request.

API requests are executed asynchronously, so you may safely place then anywhere on the page (even above the SegMetrics snippet).
