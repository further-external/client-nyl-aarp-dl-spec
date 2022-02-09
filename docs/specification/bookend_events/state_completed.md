---
title: Data Layer State Completed
---

The “State Completed” event should fire every time all Page/Screen Data events have propagated in the data layer.

## Example data layer push
```js
//Used to signify that the data layer has finished propagating page-state values.
//Useful when the desire is to combine info from several pushed events.
window.appEventData = window.appEventData || [];
window.appEventData.push({
  "event": "State Completed"
});
```
