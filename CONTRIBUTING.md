# Contributing

If you are adding, deleting, or modifying methods in any way or shape, please make sure you also complete these steps:

- The [Table of Content file](_data/specification-0-1-toc.yml) needs to be updated accordingly
- The [Linkable types file](_data/linkableTypes.yml) needs to be updated accordingly
- When creating a new type, please make sure the name is not already used somewhere else.
- The `Client Capability` and `Server Capability` need to be updated accordingly. Make sure to check the exhaustive definition of those in the LSP Specification.
- Tag new additions with the PSP version (eg: if next version is 0.2, tag it with 0.2)
- If you make a breaking change, mention it in the PR. Or early version of PSP it is possible there are breaking changes added, but overall we try not to break things.
