---
title: "TakeUntil"
permalink: /docs/operators/takeuntil
excerpt: "Stop an observable sequence when another observable emits a notification."
breadcrumbs: true
category: 'filtering'
last_modified_at: 
---

The `TakeUntil` operator allows you to stop an observable sequence when a notification is emitted from a second observable. `TakeUntil` starts by forwarding all notifications from the first observable. As soon as a notification is received from the second observable, `TakeUntil` cancels the subscription to the first observable and terminates successfully.

![TakeUntil operator](/assets/images/takeuntil.svg)
