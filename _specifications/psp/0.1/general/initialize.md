#### <a href="#initialize" name="initialize" class="anchor">Initialize Request (:leftwards_arrow_with_hook:)</a>

The initialize request Follows the same rule as the initialize request from LSP. Additions to this request are the new capabilities, and the subscribed events: A server can choose to dynamically or at startup subscribe to PSP/LSP events. The client will only send the subscribed events to the server.

_Request_:

* method: 'initialize'
* params: `InitializeParams` defined as follows:

<div class="anchorHolder"><a href="#initializeParams" name="initializeParams" class="linkableAnchor"></a></div>

```typescript
interface InitializeParams extends WorkDoneProgressParams {
    /**
     * LSP fields are ignored, unless they are needed to represent PSP fields.
     */

    capabilities: ClientCapabilities;
}
```

<div class="anchorHolder"><a href="#clientCapabilities" name="clientCapabilities" class="linkableAnchor"></a></div>

```typescript
interface ClientCapabilities {
    workspace?: {
        fileOperations?: {
            /**
             * Whether the client supports dynamic registration for
             * subscribed methods.
             */
            dynamicSubscribedRegistration?: boolean;
        }
    }

general?: {
        /**
         * The client can handle LSP server methods
         * @since PSP 0.1.0
         */
        LSP ?: boolean;
        /**
         * The client can handle DAP server methods
         * @since PSP 0.1.0
         */
        DAP ?: boolean;
        /**
         * The client can handle HttpRequest server methods
         * @since PSP 0.1.0
         */
        HttpRequest ?: boolean;
    };
}
```

_Response_:

* result: `InitializeResult` defined as follows:

<div class="anchorHolder"><a href="#initializeResult" name="initializeResult" class="linkableAnchor"></a></div>

```typescript
interface InitializeResult {
    /**
     * The capabilities the language server provides.
     */
    capabilities: ServerCapabilities;
}
```

The server can signal the following capabilities:

<div class="anchorHolder"><a href="#serverCapabilities" name="serverCapabilities" class="linkableAnchor"></a></div>

```typescript
interface ServerCapabilities {
    /**
     * General server capabilities
     */
    general?: {
        /**
         * The Server is interested in starting LSP servers.
         * @since PSP 0.1
         */
        LSP ?: boolean;
        /**
         * The Server is interested in starting DAP servers.
         * @since PSP 0.1
         */
        DAP ?: boolean;
        /**
         * The client is interested in executin http requests.
         * @since PSP 0.1.0
         */
        HttpRequests ?: boolean;
};

    /**
     * The methods the server would like to subscribe to
     * Defaults to all if empty.
     * Can also be a MethodGroup.
     * @since PSP 0.1
     */
    subscribedMethods ?: MethodGroup[]|String[];
}
```

* MethodGroup:

<div class="anchorHolder"><a href="#methodGroup" name="methodGroup" class="linkableAnchor"></a></div>

Groups can be used to represent a set of multiple methods:

```typescript

/**
 * @since PSP 0.1
 */
export enum MethodGroup {
    // All LSP methods
    LSP = 'lsp',
    // All PSP methods, excluding LSP
    PSP = 'psp',
    // All methods, PSP and LSP
    ALL = 'all',
    // No methods
    NONE = 'none',
}
```
