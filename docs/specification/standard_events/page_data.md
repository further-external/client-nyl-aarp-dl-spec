---
title: Site and Page/Screen Data
---

This should trigger every time a page or screen (for SPA) loads.

## Code

```js
window.appEventData = window.appEventData || [];

appEventData.push({
  "event": "Page Data",
  "page": {
    "name": "<page name>",
    "canonical": "<canonical page URL>",
    "programName": "<program name>",
    "section": "<section name>",
    "concept": "<page concept>",
    "type": "<page type>",
    "previous": "<previous page>",
    "productCategory": "<product category>",
    "productName": "<product name>",
    "sourceCode": "<source code>"
  },
  "site": {
    "domain": "<domain name>",
    "server": "<server name>"
  },
  "sitecore": {
    "testName": "<test name>",
    "testGroup": "<test group>",
    "visitorId": "<sitecore visitor id>"
  },
  "user": {
    "id": "<user id>"
  },
  "userProducts": [
    {
      "name": "<product name>",
      "status": "<payment status>",
      "payFrequency": "<payment frequency>",
      "eftEnrolled": "<EFT enrollment>",
      "beneficiary": "<beneficiary assigned>",
      "faceAmount": "<face amount range>",
      "policyNumber": "<policy number>"
    }
  ]
});
```

## Definitions
|Field|Type|Required|Description|Examples|
|---|---|---|---|---|
|page.name|string|Always|Page name|life insurance > ez1 > qnc1|
|page.canonical|string|Always|Page URL without query string or hash|https://www.nylaarp.com/|
|page.programName|string|Always|The name of the program corresponding with the page.|long term care|
|page.section|string|Required.|Site section, which aligns with the top-level URL folder structure (but cleaned up).|life insurance, learning center|
|page.concept|string|If Applicable.|The template of the page.|infographic|
|page.type|string|Required.|The type of page, which will be one of the 6 example options.|content, form, grief-out, completion, page error, server error|
|page.previous|string|Required.|The previous page (or screen URL for SPAs).|https://www.nylaarp.com/|
|page.productCategory|string|If Applicable.|Product corresponding with the page|Term|
|page.productName|string|If Applicable.|Product corresponding with the page|lb10|
|page.sourceCode|string|Required.|Internal campaign source code corresponding with the session|abc123|
|sitecore.testName|string|If Applicable.|The name of a test.|Term Short Form|
|sitecore.testGroup|string|If Applicable.|The group to which a prospect is assigned.|Control, Test A, Test B|
|sitecore.visitorId|string|Required.|A sitecore user ID to identify their session.|BDF972AB-93DC-4976-9C94-4602A4668392|
|site.domain|string|Required.|The TLD|www.nylaarp.com|
|site.server|string|Required.|Server corresponding with the current page.|i-08cd931590ae60d26|
|user.id|string|Required.|Anonymous user ID|1234567|
|userProducts[N].beneficiary|boolean|Required.|Has the user assigned beneficiaries to all open accounts?|true, false|
|userProducts[N].name|string|Required.|Product name|level benefit 123|
|userProducts[N].status|string|Required.|Payment status|Inforce, Extended Term, Cancelled, Expired, Mature Contract, Lapse, Past Due|
|userProducts[N].payFrequency|string|If Applicable.|Payment frequency methodology|monthly, quarterly|
|userProducts[N].faceAmount|string|Required.|Product face amount range|10000-15000|
|userProducts[N].eftEnrolled|boolean|Required.|Is the product enrolled in EFT|true|
|userProducts[N].policyNumber|string|Required.|Policy number|12345|
