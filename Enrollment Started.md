# Enrollment Started

The **Enrollment Started** event captures the user arriving on the first screen of an enrollment flow. It marks entry into the funnel.

---

## Event Specification

```javascript
window.appEventData = window.appEventData || [];
window.appEventData.push({
  "event": "Enrollment Started",
  "enrollment": {
    "name": "<name>",
    "variant": "<variant>",
    "stepName": "<stepName>",
    "stepNumber": "<stepNumber>",
    "product": [
      {
        "id": "<id>",
        "name": "<name>",
        "term": "<term>",
        "price": {
          "basePrice": "<basePrice>",
          "sellingPrice": "<sellingPrice>",
          "currency": "<currency>"
        },
        "defaultValue": "<defaultValue>"
      }
    ]
  }
});
```

#Variable Definition:
---
| Field | Type | Description | Example |
| ----- | ---- | ----------- | ------- |
| **enrollment.name** | string | The enrollment being undertaken. | `aarp-membership` |
| **enrollment.variant** | string | Which version of the enrollment experience the user is shown. Set by the payment choice made earlier in the application flow, so it is already known when the enrollment starts. | `autopay`, `non-autopay` |
| **enrollment.stepName** | string | Named step within the enrollment. | `membership-offers` |
| **enrollment.stepNumber** | integer | Position of the step in the series, 1 indexed. | `1` |
| **enrollment.product[].id** | string | Identifier for the offer. | `aarp-1yr-auto` |
| **enrollment.product[].name** | string | Offer name as displayed on screen. | `1 Year`, `3 Years` |
| **enrollment.product[].term** | integer | Membership length in years. Carried as a number so average term length can be calculated for converted versus abandoned enrollments. | `1`, `3`, `5` |
| **enrollment.product[].price.basePrice** | number | The undiscounted figure, shown struck through where a discount applies. | `20.00` |
| **enrollment.product[].price.sellingPrice** | number | What the customer pays. | `15.00` |
| **enrollment.product[].price.currency** | string | ISO currency code. | `USD` |
| **enrollment.product[].defaultValue** | boolean | Whether the offer was pre selected when the offers screen loaded. | `true`, `false` |

#Implementation Notes:
---
Fires once, on load of the first screen in the flow.

Does not fire where the joins offer is not applicable to the user.

`enrollment.product` carries every offer on display, not a selection.

`enrollment.variant` is set from the application flow and is already populated on this event.

No `payment` object on this event.

| Step | Screen | stepName | stepNumber |
| ---- | ------ | -------- | ---------- |
| 1 | Select your AARP membership | `membership-offers` | `1` |
| 2 | AARP payment | `membership-payment` | `2` |
| 3 | E Sign Consent | `esign-consent` | `3` |

The flow ends on the AARP membership information and confirmation screen, where Enrollment Complete fires. No step name or number is carried there.
