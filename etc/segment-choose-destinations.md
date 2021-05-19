# Choosing Destinations in Segment

[Segment](https://segment.com/) provides one endpoint to send analytics events to multiple destinations. With a single call to `window.analytics.track()`, we can track events in Google Analytics, Mixpanel, Optimizely, and more.

But, sometimes [we don't want to track events across all destinations](https://segment.com/docs/connections/sources/catalog/libraries/website/javascript/#managing-data-flow-with-the-integrations-object).

To send an event to specific destinations only:

```js
window.analytics.track(eventName, eventProperties, {
  integrations: {
    All: false,
    Optimizely: true,
  },
});
```

To exclude destinations from receiving an event:

```js
window.analytics.track(eventName, eventProperties, {
  integrations: {
    Optimizely: false,
  },
});
```

Note that `All` is a special property that refers to _all_ destinations. It defaults to `true`.

While Segment is often used to send events to many destinations, we can also specify and exclude destinations.
