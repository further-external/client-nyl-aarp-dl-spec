---
title: TMS Implementation Instructions
---

Launch embed tags are environmentalized to allow for different stages of the tag management workflow. Each tag must be placed in the correct environment for the workflow to ... work.

## Dev environment
For the Development site, please paste the following code inside the <head> tag of your document:

```html
<script src="//assets.adobedtm.com/e7dc5c5ab342/2297fcd88809/launch-3dbac574c690-development.min.js" async></script>
```

## Stage environment (if applicable)
For the Staging site (if applicable), please paste the following code inside the <head> tag of your document:

```html
<script src="//assets.adobedtm.com/e7dc5c5ab342/2297fcd88809/launch-fdab84a77a21-staging.min.js" async></script>
```

**Note:** Please only use this script if there are 3 environments. If there are only 2 environments (staging and production), use the Development script and Production script.

## Production environment
For the Production site, please paste the following code inside the <head> tag of your document:

```html
<script src="//assets.adobedtm.com/e7dc5c5ab342/2297fcd88809/launch-c19239d60952.min.js" async></script>
```

