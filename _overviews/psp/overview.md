---
title: Overview
topic: PSP
layout: overview
sectionid: overview
redirect_from:
  - /overview
---

## What is the Plugin Server Protocol?

If you are not aware of the Language Server Protocol, please read [this overview]({{ "/overviews/lsp/overview" | prepend: site.baseurl }}) first
<br>
<br>

The idea behind the <i>Plugin Server Protocol (PSP)</i> is to standardize the protocol for how plugins an server communicate, so a single <i>Plugin Server</i> can be re-used in multiple development tools, and tools can support plugins with minimal effort.

PSP is a win for both plugin providers and tools vendors!

## How it works

PSP uses the same base as LSP, only with some tweaks and added methods. The JSON-RPC communication is still the same, even some requests are reused. In short, PSP works as a superset of LSP. The most notable differences are:

- New fields in the initialize handshake for events. A plugin will only receive subscribed events.
- Some LSP Methods are disabled. This is because some of these requests only make sense in a Language Server context (TODO: add one example of such requests)
- New Methods are added, to reflect all type of actions needed for a plugin (modifying settings, adding palette commands, drawing on screen,etc.)

## Capabilities

PSP uses the same kind of capabilities that LSP defined, and adds more.

## Libraries (SDKs) for PSP providers and consumers

To simplify the implementation of language servers and clients, there are libraries or SDKs:

//TODO: link PSP server and client sdks (we mostly won't provide client sdk as it would need decoupling of Lapce's proxy inner workings, but a client sdk definitely needs to be a thing)
