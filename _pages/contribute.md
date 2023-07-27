---
title: "Contribution Guide"
layout: single
permalink: /contribute/
author_profile: false
toc: true
---

Bonsai is a programming language with a growing community of users and developers. Anyone is welcome to participate by reporting bugs, proposing features or improvements, or contributing pull requests directly to our open-source repositories.

This document is a guide to help you through the process of becoming an effective Bonsai contributor.

## Reporting bugs

You can report [here](https://github.com/bonsai-rx/bonsai/issues/new) any bugs you find in the compiler, IDE or standard library packages. However, we recommend starting the process by opening a [discussion](https://github.com/orgs/bonsai-rx/discussions) to help us understand and diagnose the issue in more detail. Once we have fleshed out the problem we will then convert the discussion to an issue. Conversely, if you have submitted a bug report and we need more information, we may also convert your original issue to a discussion.

## Proposing features or improvements

In addition to bugs, we welcome ideas and proposals for new language features, improvements to the IDE or new standard library packages. As above, we recommend opening a [discussion](https://github.com/orgs/bonsai-rx/discussions/categories/ideas) first so we can ask questions and flesh out the pros and cons of your proposal and also to assess the amount of effort required.

Discussions that are self-contained and stay on topic are much more likely to be read and understood by the community and developers. Examples, graphics, or diagrams are very welcome, but please do your best to describe the new language feature or improvement succinctly. Proposals that show a strong understanding of the language and the development trade-offs with the existing implementation will likely be more easy to review and accept for inclusion in the roadmap.

## Contributing pull requests

We welcome pull requests for fixing any bugs or implementing new language features.

It is often easier to understand and review the nature of a contribution if there is a discussion or issue raised beforehand, so please make sure to [link your pull request to an existing issue if available](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue).

Aim to develop high-quality contributions. Even if your pull request does not get merged, your work may still be useful to other developers.

Before we can merge any of your contributions, we will need you to fill and sign our [Contributor License Agreement](cla.md) so we can keep track of the provenance of all contributions and clarify the expectations around licensing of your contributions to our project.

### Code style

We aim to keep the code style uniform across all our projects following the [Framework Design Guidelines](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/). This makes it easier for maintainers to review contributions, navigate the organization of existing sources, and improve the quality of code across all the repositories. It also makes it easier for users of the language to study the source code when developing their own extensions and to understand the internals of the compiler and standard library.

Almost all operators are developed using a combination of [Rx.NET](https://github.com/dotnet/reactive) and [Expression Trees](https://learn.microsoft.com/en-us/dotnet/csharp/advanced-topics/expression-trees/) so reading documentation on both of these technologies and developing some proficiency for their core concepts is highly recommended.

### Document your progress

One of our main goals is to maintain high-quality documentation for language features and standard library functionality. If your pull request adds new method overloads, or new operators and classes, you must document them in the source code with [XML documentation comments](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/recommended-tags) for your contribution to be accepted.

As with source code, we aim to keep consistent terminology in our technical documentation to make it easier for both maintainers and users to study the reference manual. When in doubt, you can consult other documentation comments in the source code or ask our developer community.

We recommend starting a pull request early in your development cycle and engaging with the maintainers, especially for first time contributions. This will allow us to onboard you and make suggestions about the pull request and overall development strategy before you go all in.

### Be mindful of commit history

Keeping commit history readable and clear is very important to allow us to understand the impact of code changes when debugging or reviewing changelogs. Below are some tips to keep your pull request history tidy and clean:

- When updating your fork or branch with upstream changes, please use `git pull --rebase` to avoid merge commits. These commits make the pull request history unnecessarily hard to read.
- Write short commit messages. The commit message should describe the overall impact of your changes. If the commit message is long and you feel it cannot be made any shorter, consider whether it might be best to split the commit into multiple smaller ones.
- If you are making multiple contributions to the project, consider creating one branch in your fork for each contribution. This way you can open multiple pull requests that can be reviewed in parallel.
- Feel free to rewrite the commit history in your branch if it makes the changes easier to understand. Once contributions are merged they will be shared with everyone and cannot be changed so take every opportunity to tidy things up before then.

## Communicating with developers

Our project has several communication channels for different purposes. You can join us for a quick conversation on our Discord server or open a [discussion](https://github.com/orgs/bonsai-rx/discussions) on GitHub. We try to respond to all interactions as much as possible and are happy to provide help on any questions you may have.

## Code of Conduct

Our project has adopted the Contributor Covenant to clarify expected behavior in our community. By participating, you are expected to uphold our [Code of Conduct](code-of-conduct.md).