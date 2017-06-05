---
layout: single
permalink: /introduction/
author_profile: false
gallery:
 - url: /assets/images/fishtracking.jpg
   image_path: /assets/images/fishtracking-th.jpg
   title: "Small animal tracking"
 - url: https://www.youtube.com/watch?v=mJDV07ptQFk
   image_path: /assets/images/vr-th.jpg
   title: "Exploring Neural Data in VR"
 - url: https://www.youtube.com/watch?v=srcqJXd6Vz4&t=12m30s
   image_path: /assets/images/servoing-th.jpg
   title: "Visual servoing"
---

Bonsai is a visual language designed for making software systems that require rich and rapid interaction with the external world.

{% include gallery %}

One of the most important constraints in the development of such systems is time. Events in the world---even a simple button press---do not wait for our computer program to be ready. Also, the effects (or actions) determined by software are often not instantaneous, and may require an unspecified amount of time to complete (e.g. moving a robotic arm; sending an email).

Setting up systems to handle these kinds of asynchronous events often requires specialized and careful software engineering, and can quickly become difficult to maintain and change.

Furthermore, in modern systems we are often forced to combine not just one, but a large number of asynchronous sensors and actuators operating together, each with their own independent processing units which are not intrinsically coordinated in any way. Managing all of these different parallel components can be a challenge even for experienced programmers.

![Devices used in interactive systems](/assets/images/devices.jpg)

The core philosophy behind Bonsai is to embrace the natural constraints of the problem---heterogeneous devices and asynchronous computation---and provide development tools and languages that make it easier to put together interactive systems.

## A metaphor for asynchronous computation

To do this, Bonsai makes use of a unified model for data streams: the observable sequence. Our favorite approach to explain what exactly is an observable sequence is to use a metaphor.

Think about your favorite social networking service, and how your personal account works within that service. There are usually two main actions available. First, you can post text messages or share content such as pictures or videos. Second, you can follow other accounts so that you get notified whenever they send out their own messages. Very often users will post new messages in reaction to other posts they have just seen.

Finally, user accounts can be terminated. The user can naturally close her own account, indicating there will be no more future posts, or the account can be terminated exceptionally by a moderator, perhaps due to a breach in the terms of service.

Observable sequences behave in a very similar way to a social network account. They can be "followed", or rather subscribed to, so that its observers get notifications whenever there are new values available in the sequence. These notifications can be sent out at anytime, usually dependent on how specific data sources work. Also notifications can be sent out in reaction to other notifications.

Imagine your webcam had its own user account, where it posted new images periodically from time to time. Other accounts could "follow" the camera in order to react whenever the camera posts a new image. For example, they could repost all the original images sent out from the camera, but in grayscale. Other accounts could follow both the camera and the keyboard, and aggregate or filter out posts from one depending on the notifications from the other.

## The Bonsai visual language

The Bonsai programming language manipulates such reactive networks explicitly using workflow diagrams where observable sequences are represented graphically as colored nodes. Nodes can be connected to other nodes, from left to right.

![Example workflow](/assets/images/sampleframe.svg)

By chaining networks of observable sequences in this way, it becomes possible to express very complex interactive systems in a surprisingly compact format. For example, the workflow above describes a system that saves a snapshot from a camera into a file whenever there is a key press.

The essence of learning the Bonsai programming language is to master the art of composing arbitrarily complex interactive systems from elegant networks of simple operators. To get started, we have to go through the basic reactive operators, as well as some details of the Bonsai development environment, which are covered in the [Documentation](/docs/installation/) pages.

## Marble diagrams

To understand how this example works, however, we need not only the network of connections -- who follows who -- but also what are the rules for each operator to generate a notification. We use a different representation called a marble diagram to analyse the dynamics and behaviour of individual nodes. An example marble diagram for the `Grayscale` operation is shown below.

![Grayscale operator](/assets/images/grayscale.svg)

In a marble diagram, time is represented linearly from left to right. The timing of individual notifications is marked by the colored shapes which we call marbles. The `Grayscale` operation is represented by the white box. Arrows entering the box indicate that the operator was subscribing to, or "following", those notifications. Arrows leaving the box show notifications that are sent by the operator itself.

The diagram makes clear that the `Grayscale` operator is reacting to each of the notifications from the camera by sending out new images where all color information has been removed. This is an example of an operator which simply transforms incoming values into a different form. However, there are other operators like `Sample` which can have slightly more interesting marble diagrams.

![Sample operator](/assets/images/sample.svg)

First, we can see from the connection diagram above that the `Sample` operator subscribes to two sequences: the result from `Grayscale` and also `KeyDown`. The marble diagram shows an hypothetical example of these two independent streams of notifications. `Grayscale` is sending out images periodically, following the camera. However, `KeyDown` sends out a notification only when there is a key press, which can happen at any moment, even in between image notifications.

The diagram makes clear the behavior of `Sample`: it sends out the latest image that was received from `Grayscale` whenever there was a new key press. Marble diagrams are a useful tool to convey graphically the intuition of what a reactive operator is doing and will be used extensively throughout these pages.