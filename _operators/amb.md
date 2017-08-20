---
title: "Amb"
permalink: /docs/operators/amb
excerpt: "Given two or more input observables, emit all the items only from the first of these observables to produce an item."
breadcrumbs: true
category: 'combining'
last_modified_at: 
---

The `Amb` operator allows you to setup a race condition between two or more observable sequences. This operator will emit all the items only from the first of the input sequences to produce a notification. You can think of it as a choice between all of the input sequences, where the decision criteria is speed of first response.

![Amb operator](/assets/images/amb.svg)

As soon as the first item or notification arrives from the winning sequence, all the subscriptions to the remaining sequences will be cancelled.