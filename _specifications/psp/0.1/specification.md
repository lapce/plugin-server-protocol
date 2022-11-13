---
title: Specification
shortTitle: 0.1
layout: specifications
sectionid: specification-0-1
toc: specification-0-1-toc
fullTitle: Plugin Server Protocol Specification - 0.1
index: 2
redirect_from:
  - specification
  - specification/
  - specifications/specification-current
  - specifications/specification-current/
---

This document describes the 0.1.x version of the plugin server protocol. An implementation for Rust of the 0.1.x version of the protocol can be found [here](https://github.com/lapce/lapce-rust).

**Note:** edits to this specification can be made via a pull request against this markdown [document](https://github.com/lapce/plugin-server-protocol/blob/gh-pages/_specifications/psp/0.1/specification.md).

**Please do note that while PSP is a superset of LSP, its specification will not be found here, but rather [here](https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/)**

## <a href="#pluginServerProtocol" name="pluginServerProtocol" class="anchor"> Plugin Server Protocol </a>

### <a href="#lifeCycleMessages" name="lifeCycleMessages" class="anchor"> Server lifecycle </a>

The current protocol specification defines that the lifecycle of a server is managed by the client (e.g. a tool like Lapce, VS Code or Emacs). It is up to the client to decide when to start (process-wise) and when to shutdown a server.

{% include_relative general/initialize.md %}

### <a href="#pluginFeatures" name="pluginFeatures" class="anchor">Plugin Features</a>

Plugin Features provide much of the behavior in the Plugin Sever Protocol. The main language feature categories are:

* LSP features (stemming from LSP), and some methods for LSP handling
* Settings features, like adding new settings or registering commands
* UI features, like drawing on the screen, or in a new window.

### <a href="#serverProtocolFeatures" name="serverProtocolFeatures" class="anchor">Server Protocol Features</a>

{% include_relative plugin/lsp.md %}
{% include_relative plugin/dap.md %}

### <a href="#commandFeatures" name="commandFeatures" class="anchor">Command Features</a>

{% include_relative plugin/httpRequest.md %}

### <a href="#interactionFeatures" name="interactionFeatures" class="anchor">Interaction Features</a>

{% include_relative plugin/registerCommand.md %}
{% include_relative plugin/askChoice.md %}
