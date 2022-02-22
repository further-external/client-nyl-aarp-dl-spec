---
title: Edit Beneficiary
---

When a user edits their beneficiary distribution for a policy, a [Form Info](../../../standard_events/form_info/) event should be pushed.

## Code

```js
window.appEventData = window.appEventData || [];

appEventData.push({
  "event": "Form Info",
  "form": {
    "action": "<form action>",
    "progress": {
      "name": "<form name>",
      "status": "<form status>"
    },
    "attributes": {
      "type": "<beneficiary type>",
      "class": "<beneficiary class>",
      "distribution": "<beneficiary distribution>"
    }
  }
});
```

|Field|Type|Required|Description|Examples|
|---|---|---|---|---|
|form.action|string|Required.|Action taken on beneficiary|edit, remove|
|form.progress.name|string|Required.|Form name.|Edit Beneficiary|
|form.progress.status|string|Required.|Form status.|form OR complete|
|form.attributes.type|string|Required.|Type of beneficiary|person, estate, funeral home, business|
|form.attributes.class|string|Required.|Beneficiary class modified|1, 2, 3|