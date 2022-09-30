#### <a href="#initialize" name="initialize" class="anchor">Initialize Request (:leftwards_arrow_with_hook:)</a>

The initialize request follows the same rules as the initialize request from the [LSP specification](https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/#initialize). Additions to this request are the new capabilities, and the subscribed events: A server can choose to dynamically or at startup subscribe to PSP/LSP events. The client will only send the subscribed events to the server.

_Request_:

* method: 'initialize'
* params: `InitializeParams` defined as follows:

<div class="anchorHolder"><a href="#initializeParams" name="initializeParams" class="linkableAnchor"></a></div>

```typescript
    /**
     * LSP fields are ignored, unless they are needed to represent PSP fields.
     */
interface InitializeParams extends WorkDoneProgressParams {
    capabilities: ClientCapabilities;
}
```

<div class="anchorHolder"><a href="#clientCapabilities" name="clientCapabilities" class="linkableAnchor"></a></div>

```typescript
interface ClientCapabilities {
    psp?: {
        /**
         * The client can start LSP servers on behalf of the server
         * @since 0.1.0
         */
        lsp?: boolean;
        /**
         * The client can start DAP servers on behalf of the server
         * @since 0.1.0
         */
        dap?: boolean;
        /**
         * The client can handle HttpRequest server methods
         * @since 0.1.0
         */
        httpRequests?: boolean;

        /**
         * The Client can do dynamic Method registration
         * @since 0.1.0
         */
        dynamicMethodRegistration?: boolean;

        /**
         * The client can handle PSP plugins
         * This allows servers to dynamically know whether the client
         * is an lsp client or a psp client.
         * A use case would be:
         * - server knows that PSP is being used and uses PSP methods
         * - server knows that PSP is not being used and falls back to LSP methods only
         * @since 0.1.0
         */
        handlePsp?: boolean;
    }
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
    psp?: {
        /**
         * The Server is interested in starting LSP servers.
         * @since 0.1.0
         * default: false
         */
        dap?: boolean;
        /**
         * The Server is interested in starting DAP servers.
         * @since 0.1.0
         * default: false
         */
        dap?: boolean;
        /**
         * The Server is interested in executing http requests.
         * @since 0.1.0
         * default: false
         */
        httpRequests?: boolean;

        /**
         * The Server can do dynamic Method registration
         * @since 0.1.0
         */
        hynamicMethodRegistration?: boolean;

        /**
         * The methods the server would like to subscribe to
         * Defaults to all if empty.
         * Can also be a MethodGroup.
         * @since 0.1.0
         */
        subscribedMethods?: MethodGroup[] | string[];
    }
}
```

* MethodGroup:

<div class="anchorHolder"><a href="#methodGroup" name="methodGroup" class="linkableAnchor"></a></div>

Groups can be used to represent a set of multiple methods:

```typescript

/**
 * @since 0.1.0
 */
export enum MethodGroup {
    // All LSP methods
    lsp = 'lsp',
    // All PSP methods, excluding LSP
    lsp = 'psp',
    // All methods, PSP and LSP
    all = 'all',
    // No methods
    none = 'none',
}
```
