---
layout: default
title: Getting the Code
---

## Bring on the code!

You can recursively clone and initialize all of {{site.project_title}}'s submodules with a single git command.

**To get the code, run:**

    git clone git://github.com/Polymer/polymer-all.git --recursive

This creates a `polymer-all/` folder with the following top-level files and folders:

- **platform/** — The platform shims and polyfills.
- **polymer/polymer.js** — The [{{site.project_title}} kernel](polymer.html)
- **polymer-elements/** — A collection of core utility elements.
- **polymer-ui-elements/** — A collection of UI elements.
- **projects/** — Larger examples, demos, and tools that use {{site.project_title}}.
- Each platform (polyfill) also has a sibling repo.

More on repository structure is below.

### Test your environment

To check that your development environment is ready, start a local web
server and run one of the included sample projects:

1. **Start a local web server** in the folder where you have `polymer-all/` checked out.
2. In your browser, navigate to
    [http://localhost/toolkit-ui/workbench/menu.html](http://localhost/toolkit-ui/workbench/menu.html), or whichever port you started the server on. You should see a menu of items, as shown below.

<iframe src="/polymer-all/toolkit-ui/workbench/menu.html" style="width:270px;height:220px;border:none;"></iframe>

### About branches

See [Branching Workflow](branching-strategy.html).

### Updating {{site.project_title}} submodules

Periodically, we will update the project's submodules on GitHub. To
update your local copy's submodules, run the following command
from the `polymer-all/` folder:

    git submodule update --init --recursive

## Repository structure

The entirety of the {{site.project_title}} is composed of a number of Git
repositories. All are included as submodules in the main `polymer-all` repository.
However, understanding the various pieces will help you navigate the codebase.

We have factored our repositories into atomic chunks. For example, the following repositories may be useful individually:

* `CustomElements`
* `HTMLImports`
* `ShadowDOM`
* `mdv`
* `PointerGestures`

Some repositories depend on others in {{site.project_title}} and must be siblings of the same parent directory to function completely:

* `polymer`
* `platform`
* `toolkit-ui`

### /platform repository

[github.com/polymer/platform](https://github.com/polymer/platform)

Each new web platform feature has a corresponding polyfill repository. The
reasoning for this is two-fold:

1. make the polyfills work across all modern browsers
2. each polyfill can stand on its own and be used à la carte in projects.

The [`platform`](https://github.com/polymer/platform) repository references each of the polyfills as a sibling directory, and contains integration tests, loader, and build tools for the amalgamated polyfills.

See [Tooling Strategy](tooling-strategy.html) for information.

### /polymer repository

[github.com/polymer/polymer](https://github.com/polymer/polymer)

The [`polymer`](https://github.com/polymer/polymer) repository contains the guts
of the project. It expects the [`platform`](https://github.com/polymer/platform)
polyfill repo to be a sibling directory, and hosts the
[{{site.project_title}} kernel](polymer.html) with its tools and tests.

If you want to see the development activity, checkout the _master_ branch directly:

    git clone -b master https://github.com/Polymer/polymer.git --recursive

<p class="alert">
<b>Remember</b>: If you don't specify <em>master</em>, you'll get the <em>stable</em> branch by default.
See <a href="/branching-strategy.html">Branching Workflow</a> for more info.
</p>

### /toolkit-ui repository

[github.com/polymer/toolkit-ui](https://github.com/polymer/toolkit-ui)

The [`toolkit-ui`](https://github.com/polymer/toolkit-ui) repository contains examples of
the types of things you can do when writing a [{{site.project_title}} element](/polymer.html).

- **elements/** — `g-*` custom element definitions.
- **workbench/** — demos of the {{site.project_title}}-style elements found in `elements/`.

