---
title: "Workflow Editor"
permalink: /docs/editor/
excerpt: "A quick introduction to the Bonsai workflow editor."
last_modified_at: 
---

{% include toc icon="columns" title="Editor" %}

When Bonsai starts you will be taken directly to the workflow editor. This is where you can create, edit, and run Bonsai workflows. The editor is composed of three main panels, described below:

![The Bonsai workflow editor](/assets/images/editor.png)

## Toolbox

The `Toolbox` allows you to search for available Bonsai modules to place in the workflow. The listing is organized into five main categories:

| Category                                     | Description                                           |
| :------------------------------------------: | ----------------------------------------------------- |
| ![Source](/assets/images/source.svg)         | generate event streams from devices or files          |
| ![Transform](/assets/images/transform.svg)   | convert or process individual data items              |
| ![Sink](/assets/images/sink.svg)             | save data or trigger external outputs                 |
| ![Combinator](/assets/images/combinator.svg) | manage control flow or synchronize parallel inputs    |
| ![Snippet](/assets/images/snippet.svg)       | reusable workflow fragments stored in `.bonsai` files |

Modules inside each major category are further organized by package namespaces. These namespaces come from the packages you have installed at any given moment. The name of each namespace can give you a hint about what kind of operations or devices are controlled by modules inside that namespace (e.g. the `Audio` namespace provides access to audio capture devices or WAV file readers).

Once you have found which module you want to insert, you can place it by double-clicking, dragging it to the workflow or alternatively right-clicking and selecting a specific placement option (see below).

### Search Modules

Another way to quickly find modules is to use the `Search` textbox. Any text inserted here is matched against available module or namespace names for a match in any order. This means you can search not only for a specific module name but also by category names to locate all the modules in a namespace (e.g. try typing `Arduino`).

**ProTip:** You can directly type and search for module names even when the `Workflow` canvas is selected. You can then quickly pick which module you want with the up/down arrow keys and hit the `Return` key to place it. Repeat this process to very quickly chain a sequence of Bonsai operators.
{: .notice--info}

## Workflow



## Properties

Each Bonsai module has its own distinct set of configuration properties that specify the behaviour of individual nodes (e.g. the `Timer` module exposes the period between generated values, whereas a `Threshold` on images exposes the brightness cutoff value).

The `Properties` panel will display all the configuration properties exposed by the currently selected node. A summary description of the currently selected property can be found in the textbox at the bottom of the panel. Similarly, a description of the behaviour of the currently selected node itself is shown at the top of the panel.