---
title: Bookend events
---

The two page **bookend events** let us know when the data layer has initialized and then when it has fully propagated. The [State Initialized](state_initialized.md) event will always execute first on a page or screen load. The [State Completed](state_completed.md) event will always execute when the page’s data layer has been fully populated. All other events having to do with the page load will fire somewhere in between, and will therefore be "bookended" by these events — hence the clever name.