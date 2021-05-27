# Using Optimizely in Segment

Out of the box, [Segment will not send events to Optimizely](https://segment.com/docs/connections/destinations/catalog/optimizely-web/#implementation-prerequisite).

> Optimizely works differently than other Segment destinations: Because the Optimizely Web Snippet and Full Stack SDKs are used to modify and deliver experiences to users, they generally must be implemented at a point in your Website or app that allows them to make visual modifications in-time for users.

Instead, we must set up both Optimizely and Segment:

> Because of this Optimizely requires that customers implement their Web Snippet and SDKs natively, before the Segment snippet or implementation.
> 
> Although Segment maps `track`, and in some cases `page`, events to Optimizely’s [custom events](https://help.optimizely.com/Build_Campaigns_and_Experiments/Custom_events_in_Optimizely_X), customers must implement the snippet on their site to ensure that experiments run and Optimizely decision events can be sent to Optimizely and Segment.

So, in order to [send events to Optimizely](https://segment.com/docs/connections/destinations/catalog/optimizely-web/#optimizely-full-stack-javascript-sdk), we need to:

1. Include the Optimizely snippet
2. Include the Segment snippet
3. Wrap the Segment snippet in a function, such as `window.setupSegment()`
4. Initialize the Optimizely client
5. Expose the Optimizely client to Segment by attaching the client to `window.optimizelyClientInstance`
6. Call `window.setupSegment()` after attaching the Optimizely client

Now, Segment will correctly send events to Optimizely.
