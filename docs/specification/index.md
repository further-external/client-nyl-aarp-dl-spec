---
title: Data Layer Specification
---

## What is a data layer?
It's just a JavaScript array that lives in the global scope to which event objects are pushed.

```js
// politely initialize the data layer array
var appEventData = window.appEventData || [];

// push an event to it with a payload
appEventData.push({
  event: "State Initialized",
  page: {
    name: "Home Page"
  }
});

// push another event without a payload
appEventData.push({
  event: "State Completed"
});

// access the computed state on demand
appEventData.computedState;
```

For more information, see the [five concepts](https://techdocs.searchdiscovery.com/adobe-solutions/adobe-launch/launch-extensions/data-layer-manager).

## Why do we need it?
To facilitate front end data collection. Without it, we'd have to collect data from various disparate sources — scraping values from the DOM, snooping other objects in the global scope, etc. The data layer provides a central location to which we can push data that needs to be tracked.