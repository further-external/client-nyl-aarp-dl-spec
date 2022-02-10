---
title: Forms
---

Represents a Form event object.

```json
{
  "action": string,
  "progress": {
    "name": string,
    "step": string,
    "status": string
  },
  "attributes": {
    "state": string,
    "age": string,
    "gender": string,
    "smoker": string,
    "membership": string,
    "coverage": string,
    "health": [ string ],
    "capacity": string
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
```