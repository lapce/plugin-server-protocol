#### <a href="#startDap" name="startDap" class="anchor">Start DAP Server Request</a>

> *Since version 0.1.0*

The Start DAP Server request is sent from the server to the client when a standalone DAP server needs to be spawned.

*Client Capability*:

* property name (optional): `psp.dap`

*Server Capability*:

* property name (optional): `psp.dap`

*Request*:

* method: `psp/startDap`
* params: `StartDAPParams` defined as follows:

<div class="anchorHolder"><a href="#StartDAPParams" name="StartDAPParams" class="linkableAnchor"></a></div>

```typescript
export interface StartDAPParams {
    /**
     * URI of the binary LSP server to run.
     * The URI is a local file.
    */
    serverUri: URI;
    /**
     * Selection of all file types where the lsp will be in use.
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

#### <a href="#stopDap" name="stopDap" class="anchor">Stop DAP Server Request</a>

> *Since version 0.1.0*

The Stop DAP Server request is sent from the server to the client when a standalone DAP server needs to be spawned.

*Client Capability*:

* property name (optional): `psp.dap`

*Server Capability*:

* property name (optional): `psp.dap`

*Request*:

* method: `psp/stopDap`
* params: `StopDAPParams` defined as follows:

<div class="anchorHolder"><a href="#stopDAPParams" name="StopDAPParams" class="linkableAnchor"></a></div>

```typescript
export interface StopDAPParams {
    /**
     *  URI of the binary DAP server as specified in the startDAP request.
    */
    serverUri: URI;
}
```

*Response*:

* result: `null`
* error: code and message set in case an exception happens during the declaration request.
