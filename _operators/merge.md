---
title: "Merge"
permalink: /docs/operators/merge
excerpt: "Combine multiple observables into one by merging all their notifications."
breadcrumbs: true
category: 'combining'
last_modified_at: 
---

The `Merge` operator allows you to combine the output of multiple observables so that you can treat them as if they were the same observable. This is done by merging all the notifications from all the input sequences into a single sequence, as described in the marble diagram below.

![Merge operator](/assets/images/merge.svg)

The merged observable will terminate successfully when all the input sequences have terminated successfully, or exceptionally as soon as any sequence raises an error.