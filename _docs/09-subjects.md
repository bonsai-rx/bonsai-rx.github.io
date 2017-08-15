---
title: "Subjects"
permalink: /docs/subjects/
excerpt: "Operators for sharing observable sequences."
last_modified_at: 
---

Subjects are a special type of operator that allows reusing and sharing of observable sequences. A subject acts as a bridge or proxy; it will subscribe to an observable sequence and reemit all items it receives to downstream operators. Subjects play a role similar to branches by allowing multiple operators to subscribe to a single observable sequence.

Subjects have two important differences from branches. First, they allow you to control the [temperature](/docs/observables/#temperature) of the shared sequence. You can convert a sequence from *cold* to *hot* using `PublishSubject` or from *hot* to *cold* using `ReplaySubject`.

Second, subjects must be given a name. You can subscribe to a named subject from anywhere in the workflow using the `SubscribeSubject` operator, making subjects very useful to define sources of data that can be accessed even at different stages of processing. The following workflow demonstrates how to share an observable sequence of images using subjects.

![Example of using subjects to share observable sequences](/assets/images/subjects.svg)

**ProTip:** Subject names have scope. A subject with a given name can be accessed anywhere at the same level it is defined, or inside any node groups defined at that level. You cannot access a subject that was defined in a node group below the level you are in. If node groups are used to define [higher-order observable sequences](/docs/higher-order), any subjects defined inside that group will be unique to each created sequence.
{: .notice--info}