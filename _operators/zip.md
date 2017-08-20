---
title: "Zip"
permalink: /docs/operators/zip
excerpt: "Combines the items emitted by all the observables, matching items by the order that they arrived."
breadcrumbs: true
category: 'combining'
last_modified_at: 
---

The `Zip` operator allows you to combine the items emitted by two or more observable sequences. Items are matched by the order in which they were emitted by each of the sequences, independently of time.

![Zip operator](/assets/images/zip.svg)

The first item emitted by observable #1 is matched to the first item emitted by observable #2; the second item emitted by observable #1 is matched to the second item emitted by observable #2; and so on.

The operator will terminate when all possible pairs have been formed. This means that the resulting sequence will only be as long as the shortest of the input sequences.