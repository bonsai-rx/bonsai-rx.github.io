---
layout: single
permalink: /introduction/
author_profile: false
---

Bonsai is a visual language designed for making software systems that require a rich interface with the external world. One of the most important characteristics of such systems is time. Events in the world do not wait for our computer program to be ready (e.g. button press; receiving an email). Also, the effects (or actions) caused by our programs are often not instantaneous, and may require an unspecified amount of time to complete successfully (e.g. moving a robotic arm; sending an email).

![Example workflow]({{ site.baseurl }}/assets/images/sampleframe.svg)

Because the dynamics of generating notifications also depends on the specific implementation of each node, the connection diagram by itself is not sufficient to fully describe the behaviour of a Bonsai program. In order to analyse the dynamics and behaviour of individual nodes we use a different representation called a marble diagram. An example marble diagram for the Grayscale operation is shown below:

![Grayscale operator]({{ site.baseurl }}/assets/images/grayscale.svg)