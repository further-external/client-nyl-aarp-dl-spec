# Membership Complete

The **Membership Complete** event captures a successful membership.

---

## Event Specification

```javascript
window.appEventData = window.appEventData || [];
window.appEventData.push({
  "event": "Membership Complete",
  "membership": {
    "name": "<name>",
    "variant": "<variant>",
    "option": [
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
| **membership.name** | string | The membership being undertaken. | `aarp-membership` |
| **membership.variant** | string | Which version of the membership experience the user is shown. Set by the payment choice made earlier in the application flow, so it is already known when the membership starts. | `autopay`, `non-autopay` |
| **membership.option[].id** | string | Identifier for the offer. | `aarp-1yr-auto` |
| **membership.option[].name** | string | Offer name as displayed on screen. | `1 Year`, `3 Years` |
| **membership.option[].term** | integer | Membership length in years. Carried as a number so average term length can be calculated for converted versus abandoned enrollments. | `1`, `3`, `5` |
| **membership.option[].price.basePrice** | number | The undiscounted figure, shown struck through where a discount applies. | `20.00` |
| **membership.option[].price.sellingPrice** | number | What the customer pays. | `15.00` |
| **membership.option[].price.currency** | string | ISO currency code. | `USD` |
| **membership.option[].defaultValue** | boolean | Whether the offer was pre selected when the offers screen loaded. | `true`, `false` |
| **membership.payment.method** | string | How the membership fee is being paid. Where a card is used the value concatenates the method and the card provider with a pipe, so both can be segmented from a single variable without a second eVar. | `credit-card\|visa`, `online-check`, `billed-with-premium` |

#Implementation Notes:
---
Fires on load of the AARP membership information and confirmation screen. That screen fires nothing today, so this is new tagging.

No `stepName` or `stepNumber` on this event.

Does not fire on the deferred route. That route ends on Membership Step Progress.

| Step | Screen | stepName | stepNumber |
| ---- | ------ | -------- | ---------- |
| 1 | Select your AARP membership | `membership-offers` | `1` |
| 2 | AARP payment | `membership-payment` | `2` |
| 3 | E Sign Consent | `esign-consent` | `3` |

The flow ends on the AARP membership information and confirmation screen, where Membership Complete fires. No step name or number is carried there.
