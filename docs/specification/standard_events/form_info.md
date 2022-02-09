---
title: Form Pages
---

This object should be triggered on each form and result page, whether it is a grief or success confirmation page.

## Code
```js
window.appEventData = window.appEventData || [];

appEventData.push({
  "event": "Form Info",
  "form": {
    "action": "<form action>",
    "progress": {
      "name": "<form name>",
      "step": "<step number>",
      "status": "<progress status>"
    },
    "attributes": {
      "state": "<state>",
      "age": "<age>",
      "gender": "<gender>",
      "smoker": "<smoker status>",
      "membership": "<membership status>",
      "coverage": "<coverage amount>",
      "health": ["<health conditions>"],
      "capacity": "<capacity selection>"
    },
    "validation": {
      "attempts": "<attempt number>",
      "aarpLookupNumber": "<aarp lookup number>",
      "aarpLookupDetail": "<aarp lookup detail>"
    },
    "result": {
      "cost": "<quote amount>",
      "cause": "<grief cause>",
      "causeDetail": "<grief cause detail>",
      "controlNumber": "<application control number>",
      "leadControlNumber": "<agent lead control number>",
      "payment": "<payment selection>",
      "mmsId": "<MMS ID>",
      "claimNumber": "<claim number>"
    },
    "errors": ["<form errors>"]
  }
});
```

## Definitions
|Field|Type|Required|Description|Examples|
|---|---|---|---|---|
|form.action|string|If Applicable.|Action a user is taking on the form.|Sign-Up, Update, and Cancel, Add Beneficiary|
|form.progress.name|string|Required.|Form name|lb10|
|form.progress.step|string|Required.|Form step|Application Personal Info|
|form.progress.status|string|Required.|It’s a form when a user is on a form - complete on grief or success page|form, grief, OR complete|
|form.attributes.state|string|Required When Available.|State|Georgia|
|form.attributes.age|string|Required When Available.|Age that was input by the user from any form.|42|
|form.attributes.gender|string|Required When Available.|Gender that was input by the user from any form.|male OR female|
|form.attributes.smoker|string|Required When Available.|Smoker status that was input by the user from any form.|s OR n|
|form.attributes.membership|string|Required When Available.|AARP membership status that was input by the user from any form.|yes OR no|
|form.attributes.coverage|string|Required When Available.|Coverage amount that was input by the user from any form.|$42,000|
|form.attributes.health|string|If Applicable.|Health afflictions specified by the user on the e-sig form.|`[“stroke”,”cancer”]`|
|form.validation.attempts|integer|If Applicable.|Number of attempts for lookup utility.|1, 2, 3|
|form.validation.serviceNumber|string|If Applicable.|Grouping status ID number.|1008000003|
|form.validation.serviceDetail|string|If Applicable.|Grouping status ID detail.|Expire|
|form.result.cost|string|If Applicable.|Cost of the plan from a successful form submission.|$5/month|
|form.result.cause|string|If Applicable.|Reason for hitting the grief page.|max age|
|form.result.controlNumber|string|If Applicable.|Application control number|v000456643|
|form.result.leadControlNumber|string|If Applicable.|Agent control number|v000456643|
|form.result.payment|string|If Applicable.|Payment selection|bill later OR eft|
|form.result.mmsId|string|Required When Available.|MMS ID|75639661 OR Undefined|
|form.errors[n]|array|Required When Available.|Array of inline form field errors.|`[First Name, Last Name]`|
