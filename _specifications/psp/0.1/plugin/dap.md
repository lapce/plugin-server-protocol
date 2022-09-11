#### <a href="#start_dap" name="start_dap" class="anchor">Start DAP Server Request</a>

> *Since version 0.1.0*

The Start DAP Server request is sent from the server to the client when a standalone DAP server needs to be spawned.

_Client Capability_:
* property name (optional): `general.DAP`

_Server Capability_:
* property name (optional): `general.DAP`


_Request_:
* method: `start_dap`
* params: `StartDAPParams` defined as follows:

<div class="anchorHolder"><a href="#StartDAPParams" name="StartDAPParams" class="linkableAnchor"></a></div>

```typescript
export interface StartDAPParams {
    serverUri: URI;
    languageID: String[];

    /**
     * args passed to the invoked DAP server
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
