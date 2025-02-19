#### <a href="#startLsp" name="startLsp" class="anchor">Start LSP Server Request</a>

> *Since version 0.1.0*

The Start LSP Server request is sent from the server to the client when a standalone LSP server needs to be spawned.

*Client Capability*:

* property name (optional): `psp.lsp`

*Server Capability*:

* property name (optional): `psp.lsp`

*Request*:

* method: `psp/startLsp`
* params: `StartLSPParams` defined as follows:

<div class="anchorHolder"><a href="#startLSPParams" name="StartLSPParams" class="linkableAnchor"></a></div>

```typescript
export interface StartLSPParams {
    /**
     * URI of the binary LSP server to run.
     * The URI is a local file.
    */
    serverUri: URI;
    /**
     * Selection of all file types that the lsp will receive events about
    */
    documentSelector: DocumentSelector;

    /**
     * Args passed to the invoked LSP server
    */
    serverArgs: string[];

    /**
     * Plugin options
    */
    options: LSPAny;
}
```

*Response*:

* result: `null`
* error: code and message set in case an exception happens during the declaration request.

#### <a href="#stopLsp" name="stopLsp" class="anchor">Stop LSP Server Request</a>

> *Since version 0.1.0*

The Stop LSP Server request is sent from the server to the client when a standalone LSP server needs to be spawned.

*Client Capability*:

* property name (optional): `psp.lsp`

*Server Capability*:

* property name (optional): `psp.lsp`

*Request*:

* method: `psp/stopLsp`
* params: `StopLSPParams` defined as follows:

<div class="anchorHolder"><a href="#stopLSPParams" name="StopLSPParams" class="linkableAnchor"></a></div>

```typescript
export interface StopLSPParams {
    /**
     *  URI of the binary LSP server as specified in the startLSP request.
    */
    serverUri: URI;
}
```

*Response*:

* result: `null`
* error: code and message set in case an exception happens during the declaration request.
