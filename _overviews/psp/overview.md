---
title: Overview
topic: PSP
layout: overview
sectionid: overview
redirect_from:
  - /overview
---

## What is the Plugin Server Protocol?

If you are not aware of the Language Server Protocol, please read [this overview](https://microsoft.github.io/language-server-protocol/overviews/lsp/overview/) first
<br>
<br>

The idea behind the *Plugin Server Protocol (PSP)* is to standardize the protocol between editors (clients) and plugins (servers); so that a single Plugin Server can be re-used in multiple development tools, and tools can support plugins with minimal effort.

PSP is a win for both plugin providers and tool vendors!

## How it works

The Plugin Server Protocol serves as an extension of the existing Language Server Protocol, which standardized how language tooling communicated with editors. Much of the communication and methods are inherited from it, though with some changes: new methods are added for functionality expected by plugins. (Adding commands to the palette, settings information, starting LSP servers,etc.). This allows to broaden a plugin capability to the scope of an entire editor!

## Capabilities

The PSP inherits the same capabilities defined in the [LSP specification](https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/), and adds more that are specific to the protocol.

## Libraries (SDKs) for PSP providers and consumers

To simplify the implementation of language servers and clients, libraries and SDKs are currently being worked on.
