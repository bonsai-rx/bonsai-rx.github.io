---
title: "SkipUntil"
permalink: /docs/operators/skipuntil
excerpt: "Discard items emitted by an observable sequence until another observable emits a notification."
breadcrumbs: true
category: 'filtering'
last_modified_at: 
---

The `SkipUntil` operator allows you to discard notifications from the beginning of an observable sequence until a notification is emitted from a second observable. After the first notification is received from that second sequence, `SkipUntil` forwards all subsequent notifications from the first sequence.

![SkipUntil operator](/assets/images/skipuntil.svg)
