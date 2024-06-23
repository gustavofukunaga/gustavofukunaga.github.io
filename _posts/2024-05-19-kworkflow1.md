---
title: "Contributing to kworkflow"
date: 2024-05-19
---

In this blog post, I will talk about the process of contributing to kworkflow, an open source project providing Linux kernel development tools, reducing the environment and setup overhead of developing for the Linux kernel.

- kworkflow repository: [https://github.com/kworkflow/kworkflow](https://github.com/kworkflow/kworkflow)

- kworkflow documentation: [https://kworkflow.org/](https://kworkflow.org/)

## The issue

Despite the size of the project, kworkflow has a relatively large code base. For this reason, there are parts of the code base that do not comply with coding style rules, either because they were implemented before the coding style was introduced, or because they slipped through the review and remained.

kworkflow codingstyle: [https://kworkflow.org/content/codingstyle.html](https://kworkflow.org/content/codingstyle.html)

A relatively common case is using single quotes (') instead of double quotes when there are no Bash expansions. For example, if there is something like:

```bash
var="literal-value"
```

the correct form would be

```bash
var='literal-value'
```

This rule is quite fundamental and is was not documented in the website.

## The Solution

Me and [Caio Dantas](https://github.com/Caio-Dantas), worked on adding the documentation to single quotes use and fix codestyle for files in `/src` directory.

Adding the documentation to the website was simple, only writing a new section in the file `documentation/content/codingstyle.rst` was enough. Sphinx makes converting a `.rst` file to a HTML website quite easy.

To find all the cases where single quotes were not used for literal bash values, we used the bash command `grep`, searching a regex pattern for all the files inside `/src` dir.

```bash
grep -rnh '^[^#]* "[^"$]*" '
```

Still there were some edge cases where double quotes were necessary despite no bash extensions were used, such as:

```bash
complain 'No local or global config found. Please reinstall kw or run "kw init" to create a .kw in this dir.'
```

In this case, `"kw init"` have no bash extensions, but the use of double quotes are necessary to print the message. For edge cases like this one, a manual verification was used.

## Pull request

The pull request was created in [https://github.com/kworkflow/kworkflow/pull/1103](https://github.com/kworkflow/kworkflow/pull/1103), with 2 commits, one for documentation and one for `/src` file changes. It was closed and merged in the project `unstable` branch.

## Final thoughts

This was a great learning experience to open source projects in GitHub, kworkflow has a active growing community and the process of creating a PR was easy and simple. I definitely fell more confortable to create new contributions to this and other open source projects in GitHub.