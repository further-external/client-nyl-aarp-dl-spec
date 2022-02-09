---
title: Data Layer Specification
---

## What is a data layer?
It's just a JavaScript array that lives in the global scope to which event objects are pushed.

## Why do we need it?
To facilitate front end data collection. Without it, we'd have to collect data from various disparate sources. The data layer provides a central location to which we can push data that needs to be tracked.