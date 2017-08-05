---
title: "Workflow Editor"
permalink: /docs/editor/
excerpt: "A quick introduction to the Bonsai workflow editor."
last_modified_at: 
---

{% include toc icon="columns" title="Editor" %}

When Bonsai starts you will be taken directly to the workflow editor. This is where you can create, configure, and run Bonsai workflows. The editor is composed of three main panels, described below:

![The Bonsai workflow editor](/assets/images/editor.png)

## Toolbox

The `Toolbox` allows you to search for available Bonsai operators to place in the workflow. The listing is organized into five main categories:

| Category                                     | Description                                           |
| :------------------------------------------: | ----------------------------------------------------- |
| ![Source](/assets/images/source.svg)         | generate event streams from devices or files          |
| ![Transform](/assets/images/transform.svg)   | convert or process individual data items              |
| ![Sink](/assets/images/sink.svg)             | save data or trigger external outputs                 |
| ![Combinator](/assets/images/combinator.svg) | manage control flow or synchronize parallel inputs    |
| ![Snippet](/assets/images/snippet.svg)       | reusable workflow fragments stored in `.bonsai` files |

Operators inside each major category are further organized by package namespaces. These namespaces come from the packages you have installed at any given moment. The name of each namespace can give you a hint about what kind of operations or devices can be accessed inside (e.g. the `Audio` namespace provides access to audio capture devices or WAV file readers).

Once you have found which operator you want to insert, you can place it by double-clicking, dragging it to the workflow or alternatively right-clicking and selecting a specific placement option (see below).

### Search Operators

Another way to quickly find operators is to use the `Search` textbox. Any text inserted here is matched against available operator or namespace names for a match in any order. This means you can search not only for a specific operator name but also by category names to locate all the operators in a namespace (e.g. try typing `Arduino`).

**ProTip:** You can also directly type and search for operator names when the `Workflow` panel has the input focus. This allows you to simply start typing an operator name and directly select which operator you want with the up/down arrow keys. Once you have the right operator, hit the `Return` key to place it. You can repeat the process multiple times to very quickly chain a sequence of operators.
{: .notice--info}

## Workflow

The `Workflow` panel is where you place reactive operators to create data processing pipelines or other asynchronous computations. Each operator in Bonsai is represented by a circular node. Nodes can be connected together, forming a directed feedforward graph from left to right. Connections indicate which operators receive data from which other operators (see the [Introduction](/introduction/) and the [Language Guide](/docs/observables/) for an extended discussion).

The most useful action to learn your way around the `Workflow` panel is right-clicking. This will bring up the context menu for the specific node you selected, or a list of possible actions you can do with the current selection:

![The workflow context menu](/assets/images/contextmenu.png)

If only one node is selected, the `Output` menu item will display the type of the elements emitted in the observable sequence of that operator.

**ProTip:** If the output of an operator is a complex type, you can also inspect its public data members from the context menu. Clicking on any one of these members will automatically place a new `MemberSelector` transform which selects that member from the output.
{: .notice--info}

The context menu also allows you to externalize public properties of the operator into explicit nodes in the workflow, so you can change their values dynamically based on the output of other nodes (see the Language Guide for more information).

Finally, it is possible to group nodes into nested workflows both for organizational and more advanced functional purposes. The most basic grouping is the logical group which allows you to encapsulate a workflow fragment inside a single node. This `NestedWorkflow` can be assigned a `Name` and `Description` for ease of reference. Any named properties which are externalized by nodes in the group will be shown as properties of the `NestedWorkflow` so you can literally treat the group as a single node.

**ProTip:** You can use `NestedWorkflow` nodes to document your workflow by adding names and descriptions to individual processing branches. No additional processing cost is incurred by the use of logical groups.
{: .notice--info}

Other advanced uses of node groups are discussed in the corresponding section of the Language Guide.

### Type Visualizers

Type visualizers allow you to inspect online the data that is generated by any specific node during the execution of the workflow. They are useful to debug the result of image or signal processing operations or to debug the behaviour of the workflow itself.

![Example of image type visualizers](/assets/images/visualizers.png)

Types can have more than one visualizer available (e.g. text and image), and new visualizers can be added by installing new packages. You can enable or disable the active type visualizer for a specific node by using the context menu.

If you leave one or more visualizers open when you stop the workflow, Bonsai will memorize the position and size of each active window. When you run the workflow again, the same visualizer windows will be opened following the memorized layout. Bonsai stores these settings in a `.layout` file which is saved side by side with the workflow so they will persist between editor sessions.

**ProTip:** Many visualizers allow you to access more detailed information or advanced configuration parameters by right-clicking on the visualizer window.
{: .notice--info}

### Snippets

You can create and save workflow snippets by selecting one or more nodes and clicking the `Save Snippet As...` button in the context menu.

Snippets are a powerful way to reuse common workflow patterns across projects. When you save a new snippet file it will immediately show up in the `Toolbox` panel for placement. Placing a snippet is equivalent to copying the workflow fragment stored in the snippet file into your current workflow.

It is possible to organize snippets into folders so you can search them by keyword, similar to the role of namespaces found in compiled Bonsai packages.

## Properties

Each Bonsai operator exposes a set of configuration properties that parameterize the operator's behaviour (e.g. the `Timer` operator exposes the period between generated values, whereas a `Threshold` on images exposes the brightness cutoff value applied to individual pixels).

The `Properties` panel will display all the configuration properties which are available for the currently selected operator. A summary description of the currently selected property can be found in the textbox at the bottom of the panel. Similarly, a description of the behaviour of the currently selected operator itself is shown at the top of the panel.

Most properties can be configured simply by changing the text value in the corresponding row of the property grid. Some properties have further specialized editors which can be accessed by clicking the drop-down or dialog button which will be displayed to the right of the property text.

**ProTip:** Some operators have even more specialized editor windows such as camera configuration dialogs or media player controls. If such property pages exist for the currently selected operator, the small `Property Pages` button above the property grid will become active.
{: .notice--info}