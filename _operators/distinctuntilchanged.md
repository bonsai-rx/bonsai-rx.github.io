---
title: "DistinctUntilChanged"
permalink: /docs/operators/distinctuntilchanged
excerpt: "Suppress consecutive duplicate items from an observable sequence."
breadcrumbs: true
category: 'filtering'
last_modified_at: 
---

The `DistinctUntilChanged` operator allows you to filter consecutive duplicate items from an observable sequence. This means that the resulting sequence will only emit items when there are changes in the input. As long as the input sequence keeps repeating the same value, the result will be silent.

![DistinctUntilChanged operator](/assets/images/distinctuntilchanged.svg)

This operator can be useful to turn a periodic, or continuous, sequence of data values into a discrete event stream, where a new event will be signalled only when there is a change in value.