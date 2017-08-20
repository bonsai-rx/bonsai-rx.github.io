---
title: "Concat"
permalink: /docs/operators/concat
excerpt: "Creates a single sequence by concatenating multiple observables one after the other."
breadcrumbs: true
category: 'combining'
last_modified_at: 
---

The `Concat` operator allows you to combine the output of multiple observables so that you can treat them as if they were the same observable. This is done by concatenating the notifications from the input observables sequentially, such that the next sequence starts only after the previous sequence has terminated, as described in the marble diagram below.

![Concat operator](/assets/images/concat.svg)

The resulting observable will terminate successfully when the last observable sequence has terminated successfully, or exceptionally as soon as any sequence raises an error.