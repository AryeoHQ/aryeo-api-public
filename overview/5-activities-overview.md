# Activities Overview

_Learn about webhooks and how activities are triggered for your account._

Activities are our way of letting you know when something interesting happens in your account. When an event occurs, we create a new `Activity` object. If you registered a webhook endpoint to receive that activity, we send it to your endpoint as part of a POST request.

```json
{
  "object": "ACTIVITY",
  "id": "f1906537-ef23-478a-9757-588e02fc353c",
  "name": "LISTING_DELIVERED",
  "occurred_at": "2023-03-14T01:04:40Z",
  "resource": {
    "object": "LISTING",
    "id": "0cf74179-5e49-4557-bdb4-5eb55f2552a6"
   	...
  }
}
```

The activity object includes a nested `resource` attribute, which is the subject of the activity. For example, the `LISTING_DELIVERED` activity will include a `Listing` object as its nested resource.

Using the ID of the nested resource, additional details or relationships can be queried for using the Aryeo API.