---
title: page Resource
---

The `page` resource describes a page or screen.

```json
{
  "name": string,
  "canonical": string,
  "programName": string,
  "section": string,
  "concept": string,
  "type": string,
  "previous": string,
  "productCategory": string,
  "productName": string,
  "sourceCode": string
}
```

## Page properties
|Field|Type|Required|Description|Examples|
|---|---|---|---|---|
|name|string|Always|Page name|life insurance > ez1 > qnc1|
|canonical|string|Always|Page URL without query string or hash|https://www.nylaarp.com/|
|programName|string|Always|The name of the program corresponding with the page.|long term care|
|section|string|Required.|Site section, which aligns with the top-level URL folder structure (but cleaned up).|life insurance, learning center|
|concept|string|If Applicable.|The template of the page.|infographic|
|type|string|Required.|The type of page, which will be one of the 6 example options.|content, form, grief-out, completion, page error, server error|
|previous|string|Required.|The previous page (or screen URL for SPAs).|https://www.nylaarp.com/|
|productCategory|string|If Applicable.|Product corresponding with the page|Term|
|productName|string|If Applicable.|Product corresponding with the page|lb10|
|sourceCode|string|Required.|Internal campaign source code corresponding with the session|abc123|