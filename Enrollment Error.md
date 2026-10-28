# Enrollment Error

The **Enrollment Error** event captures a failure during an enrollment, separating a genuine error from a user choosing to leave.

---

## Event Specification

```javascript
window.appEventData = window.appEventData || [];
window.appEventData.push({
  "event": "Enrollment Error",
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
    ],
    "payment": {
      "method": "<method>"
    },
    "error": {
      "type": "<type>",
      "code": "<code>",
      "message": "<message>"
    }
  }
});
```

#Variable Definition:
---
| Field | Type | Description | Example |
| ----- | ---- | ----------- | ------- |
| **enrollment.name** | string | The enrollment being undertaken. | `aarp-membership` |
| **enrollment.variant** | string | Which version of the enrollment experience the user is shown. Set by the payment choice made earlier in the application flow, so it is already known when the enrollment starts. | `autopay`, `non-autopay` |
| **enrollment.stepName** | string | Named step within the enrollment. | `membership-offers`, `esign-consent` |
| **enrollment.stepNumber** | integer | Position of the step in the series, 1 indexed. | `1`, `2`, `3` |
| **enrollment.product[].id** | string | Identifier for the offer. | `aarp-1yr-auto` |
| **enrollment.product[].name** | string | Offer name as displayed on screen. | `1 Year`, `3 Years` |
| **enrollment.product[].term** | integer | Membership length in years. Carried as a number so average term length can be calculated for converted versus abandoned enrollments. | `1`, `3`, `5` |
| **enrollment.product[].price.basePrice** | number | The undiscounted figure, shown struck through where a discount applies. | `20.00` |
| **enrollment.product[].price.sellingPrice** | number | What the customer pays. | `15.00` |
| **enrollment.product[].price.currency** | string | ISO currency code. | `USD` |
| **enrollment.product[].defaultValue** | boolean | Whether the offer was pre selected when the offers screen loaded. | `true`, `false` |
| **enrollment.payment.method** | string | How the membership fee is being paid. Where a card is used the value concatenates the method and the card provider with a pipe, so both can be segmented from a single variable without a second eVar. | `credit-card\|visa`, `online-check`, `billed-with-premium` |
| **enrollment.error.type** | string | Category of failure. | `payment-declined`, `validation`, `service-unavailable` |
| **enrollment.error.code** | string | System or vendor error code where one exists. | `E4021` |
| **enrollment.error.message** | string | Message surfaced to the user. No customer data. | `Card declined by issuer` |

#Implementation Notes:
---
Fires on failure, at whatever step it occurs.

`enrollment.product` carries the selected offer once past the first step. On the offers screen it carries every offer on display.

`enrollment.payment` is included once the method is known.

No step field on the error object. Use `enrollment.stepName`.

| Step | Screen | stepName | stepNumber |
| ---- | ------ | -------- | ---------- |
| 1 | Select your AARP membership | `membership-offers` | `1` |
| 2 | AARP payment | `membership-payment` | `2` |
| 3 | E Sign Consent | `esign-consent` | `3` |

The flow ends on the AARP membership information and confirmation screen, where Enrollment Complete fires. No step name or number is carried there.
