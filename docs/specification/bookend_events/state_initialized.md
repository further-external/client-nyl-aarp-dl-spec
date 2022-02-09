---
title: Data Layer State Initialized
---

For SPA's it is often desirable to reset the data layer prior to pushing new values to the data layer. This can be done manually with the Javascript `window.appEventData.length=0` or by calling `window.appEventData._reset()`.

## Example data layer push

```js
//Used to signify that a new page/screen is being loaded
window.appEventData = window.appEventData || [];
window.appEventData.push({
  "event": "State Initialized"
});
```

