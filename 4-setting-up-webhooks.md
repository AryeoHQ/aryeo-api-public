# Setting Up Webhooks

_Listen for activities in your Aryeo account so your integration can automatically trigger reactions._

> ### 📘 Feature Flagged
>
> Custom webhook management via the Aryeo Web UI is currently feature flagged, and coming soon to all accounts!
>
> Interested in setting up your own custom webhooks? Reach out to our team with your use case to help us craft our upcoming feature roadmap.

Aryeo uses webhooks to notify your application when an event or activity happens in your account. Webhooks are particularly useful for asynchronous events like when a order is fulfilled, a customer is created, an invoice is paid, media is delivered, and more.

### How Aryeo Uses Webhooks

A webhook enables Aryeo to push real-time notifications to your app. Aryeo uses HTTPS to send these notifications to your app as a JSON payload. You can then use these notifications to execute actions in your backend systems. To learn more about the events Aryeo supports for webhooks, see Aryeo webhook activities overview.

### Steps To Receive Webhooks

You can start receiving event notifications in your app using the steps in this section:

1. Identify the events you want to monitor and the event payloads to parse.
2. Create a webhook endpoint as an HTTP endpoint (URL) on your local server.
3. Handle requests from Aryeo by parsing each event object and returning 2xx response status codes.
   1. If the receiving endpoint doesn't respond with a response code starting with 2, Aryeo will retry calling the webhook after 10 seconds. If that second attempt fails, Aryeo will attempt to call the webhook a final time after 100 seconds.
   2. After that, no further attempts will be made.
4. Deploy your webhook endpoint so it’s a publicly accessible HTTPS URL.
5. Register your publicly accessible HTTPS URL in the Aryeo dashboard or by reaching out to our team.

### How To Create a Webhook Endpoint

Creating a webhook endpoint is no different from creating any other page on your website. It’s an HTTP or HTTPS endpoint on your server with a URL.

You can use one endpoint to handle several different event types at once, or set up individual endpoints for specific events.

### Signing Webhooks

All Aryeo webhooks will include a header called `Signature` that your application can use to verify that the webhook payload hasn't been tampered with.

Any arbitrary string can be used as a secret to complete the signing. When set, `Signature` will represent a HMAC hash value generated using the`sha256` hashing algorithm, the webhook request body encoded as JSON as the message, and the secret as the key.

This is how Aryeo calculates that signature:

```php php
$signature = hash_hmac('sha256', $payloadJson, $secret);
```

### Other Custom Headers

Some applications may prefer to set other custom headers on their webhook requests to further enable validation beyond the `Signature`.

Aryeo supports specifying any number of arbitrary headers on webhooks calls.