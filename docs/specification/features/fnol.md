---
title: First Notice of Loss
---

## Code

```js
window.appEventData = window.appEventData || [];

appEventData.push({
  "event": "Form Info",
  "form": {
    "progress": {
      "name": "First Notice Of Loss",
      "step": "<step number>",
      "status": "<progress status>"
    },
    "attributes": {
      "state": "<state>",
      "capacity": "<capacity selection>"
    },
    "result": {
      "cause": "<grief cause>",
      "claimNumber": "<claim number>"
    }
  }
});
```

## Definitions
|Field|Type|Required|Description|Examples|
|---|---|---|---|---|
|form.progress.name|string|Required.|Form name|lb10|
|form.progress.step|string|Required.|Form step/page number|Step 1, Step 2, Complete|
|form.progress.status|string|Required.|It’s a form when a user is on a form - complete on grief or success page|form OR complete|
|form.attributes.state|string|Required When Available.|State|Georgia|
|form.attributes.capacity|string|Required When Available.|Capacity|Individual Beneficiary
|form.result.cause|string|If Applicable.|Reason for hitting the grief page.|max age|
|form.result.claimNumber|string|If Applicable.|Claim Number|M76729-234233|