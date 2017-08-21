---
title: "Bonsai"
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

One of the most important challenges in the development of such systems is dealing with time. Computers work by running sequences of instructions one after the other. However, events in the world---even a simple button press---do not wait for our programs to be ready. Also the effects (or actions) determined by software are often not instantaneous, and may require an unspecified amount of time to complete, e.g. moving a robotic arm or sending an email.

Setting up systems to handle these kinds of asynchronous events often requires specialized and careful software engineering, and they can quickly become difficult to maintain and change.

Furthermore, in modern systems we are often forced to combine not just one, but a large number of devices, each with their own independent processing units. Managing all of these different parallel components can be a challenge even for experienced programmers.

![Devices used in interactive systems](/assets/images/devices.jpg)

The core philosophy behind Bonsai is to embrace the natural constraints of the problem---heterogeneous devices and asynchronous computation---and provide development tools and languages that make it easier to put together interactive systems.

## A visual language for reactive programming

In the Bonsai programming language, interactive systems are assembled by graphical composition of reactive networks where operations are represented as colored nodes. Nodes can be connected to other nodes, indicating how data is propagated through the different elements in the system.

![Example workflow](/assets/images/sampleframe.svg)

Using Bonsai, it becomes possible to express complex interactive systems in a surprisingly compact format. For example, the workflow above describes a system that saves a snapshot from a camera into a file whenever there is a key press.

The essence of learning the Bonsai programming language is to master the art of composing arbitrarily complex interactive systems from elegant networks of simple operators. For a more in-depth discussion and an introduction to all the basic reactive operators, see the [Language Guide](/docs/observables/).

## A modular toolbox for interactive systems

Bonsai comes with an extensive collection of built-in packages and an integrated development environment to accelerate the creation of interactive applications. These packages include support for cameras, microphones, microcontrollers and many other input and output devices, as well as algorithms for image and signal processing, computer vision, data logging and visualization.

![Object tracking example](/assets/images/subtraction.png)

The integrated editor is fully extensible and allows you to easily develop your own custom reactive operators in Python, C# or any other .NET programming language. Packages that you develop can be immediately shared with the Bonsai community using the integrated NuGet package manager.

You can find installation instructions and more details of the Bonsai development environment in the [Getting Started](/docs/installation/) section.
