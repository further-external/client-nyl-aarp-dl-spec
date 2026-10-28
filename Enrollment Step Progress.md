# Enrollment Step Progress

The **Enrollment Step Progress** event captures the user reaching each step of an enrollment flow after the first. It shows how far a user got before dropping out.

---

## Event Specification

```javascript
window.appEventData = window.appEventData || [];
window.appEventData.push({
  "event": "Enrollment Step Progress",
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

#Implementation Notes:
---
Fires on load of each step after the first.

`enrollment.product` carries only the offer the user selected.

`enrollment.payment` is present from the step where the method is known. On the direct route that is step 3.

Deferred route: fires on the click of the "Include $20 AARP membership fee in my first month's New York Life bill" control on the offers screen. Set `stepName` to `membership-deferred`, `stepNumber` to `2`, `enrollment.payment.method` to `billed-with-premium`. This is the last event on that route.

| Step | Screen | stepName | stepNumber |
| ---- | ------ | -------- | ---------- |
| 1 | Select your AARP membership | `membership-offers` | `1` |
| 2 | AARP payment | `membership-payment` | `2` |
| 2 | Deferred to premium bill, chosen on the offers screen | `membership-deferred` | `2` |
| 3 | E Sign Consent | `esign-consent` | `3` |

The two step 2 entries are alternatives. A user takes one or the other.

The flow ends on the AARP membership information and confirmation screen, where Enrollment Complete fires. No step name or number is carried there.
