#### <a href="#start_lsp" name="start_lsp" class="anchor">Start LSP Server Request</a>

> *Since version 0.1.0*

The Start LSP Server request is sent from the server to the client when a standalone LSP server needs to be spawned.

_Client Capability_:
* property name (optional): `general.LSP`

_Server Capability_:
* property name (optional): `general.LSP`


_Request_:
* method: `general/startLsp`
* params: `StartLSPParams` defined as follows:

<div class="anchorHolder"><a href="#StartLSPParams" name="StartLSPParams" class="linkableAnchor"></a></div>

```typescript
export interface StartLSPParams {
    serverUri: URI;
    languageID: String[];

    /**
     * args passed to the invoked LSP server
    serverArgs: any;

    /**
     * Plugin options
     */
    Options: any;
    /**
     * Leave the resolving of the binary path to be handled by the client
     */
    resolvePath: boolean;
}
```

_Response_:
* result: `null`
* error: code and message set in case an exception happens during the declaration request.
