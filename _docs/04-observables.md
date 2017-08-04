---
title: "Observables"
permalink: /docs/observables/
excerpt: "A metaphor for asynchronous computation."
last_modified_at: 
---

Bonsai makes use of a unified model for asynchronous data streams: the observable sequence. Our favorite approach to explain what exactly is an observable sequence is to use a metaphor.

## A metaphor for asynchronous computation

Think about your favorite social networking service, and how your personal account works within that service. There are usually two main actions available. First, you can post text messages or share content such as pictures or videos. Second, you can follow other accounts so that you get notified whenever they send out their own messages. Very often users will post new messages in reaction to other posts they have just seen.

Social network accounts can also be terminated. The user can naturally close her own account, indicating there will be no more future posts, or the account can be terminated exceptionally by a moderator, perhaps due to a breach in the terms of service.

Now imagine your webcam had its own user account in the social network, where it posted new images periodically from time to time. Other accounts would now be able to "follow" the camera in order to react whenever it posts a new image. They could, for example, repost all the original images shared by the camera, but in grayscale or using other image processing filters. Other devices could have their own accounts, such as keyboards, microphones or temperature sensors. In this case other accounts could, for example, follow both the camera and the keyboard, and aggregate or filter out posts from one depending on the notifications from the other.

Observable sequences are asynchronous sequences of data which behave in exactly this way. They can be "followed", or rather subscribed to, so that its observers get notifications whenever there are new values available in the sequence. These notifications can be sent anytime or in reaction to other notifications, depending on the details of the sequence.

Observable sequences can also terminate naturally when there is no more data to send out, or exceptionally, if there is an error with the device or during data processing.

## The Bonsai visual language

The Bonsai programming language manipulates such reactive networks explicitly using workflow diagrams where observable sequences are represented graphically as colored nodes. Nodes can be connected to other nodes, from left to right, indicating that the rightmost node subscribes to the notifications of the leftmost node.

![Example workflow](/assets/images/sampleframe.svg)

By chaining networks of observable sequences in this way, it becomes possible to express very complex interactive systems in a surprisingly compact format. For example, the workflow above describes a system that saves a grayscale snapshot from a camera into a file whenever there is a key press.

## Marble diagrams

To understand how this example works, however, we need to know not only the network of connections -- who follows who -- but also the rules used by each operator to generate notifications. Specifically, for each operator we need to know exactly *what* notifications are sent out, and *when*. In order to analyse the behavior and dynamics of individual nodes, we use a different representation called a marble diagram. An example marble diagram for the `Grayscale` operation is shown below.

![Grayscale operator](/assets/images/grayscale.svg)

In a marble diagram, time is represented linearly from left to right. The timing of individual notifications is marked by the colored shapes which we call marbles. The `Grayscale` operation is represented by the white box. Arrows entering the box indicate that the operator was subscribing to, or "following", those notifications. Arrows leaving the box show notifications that are sent by the operator itself.

The diagram makes clear that the `Grayscale` operator is reacting to each of the notifications from the camera by sending out new images where all color information has been removed. This is an example of an operator which simply transforms incoming values into a different form. However, there are other operators like `Sample` which can have slightly more interesting marble diagrams.

![Sample operator](/assets/images/sample.svg)

First, we can see from the connection diagram above that the `Sample` operator subscribes to two sequences: `Grayscale` and `KeyDown`. The marble diagram shows an hypothetical example of these two independent streams of notifications. `Grayscale` is sending out images periodically, following the camera. However, `KeyDown` sends out a notification only when there is a key press, which can happen at any moment, even in between image notifications.

The diagram makes clear the behavior of `Sample`: it sends out the latest image that was received from `Grayscale` whenever there was a new key press. Marble diagrams are a useful tool to convey graphically the intuition of what a reactive operator is doing and will be used extensively throughout these pages.