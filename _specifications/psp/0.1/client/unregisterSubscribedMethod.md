#### <a href="#client_unregisterSubscribedMethod" name="client_unregisterSubscribedMethod" class="anchor">Unregister Capability (:arrow_right_hook:)</a>

The `methodclient/unregister_subscribed_method` request is sent from the server to the client to unregister a previously registered method.

_Request_:
* method: 'methodclient/unregisterSubscribedMethod'
* params: `UnregistrationParams`

Where `UnregistrationParams` are defined as follows:

<div class="anchorHolder"><a href="#unregistration" name="unregistration" class="linkableAnchor"></a></div>

```typescript
/**
 * General parameters to unregister a method.
 */
export interface Unregistration {
    /**
     * The id used to unregister the request or notification. Usually an id
     * provided during the register request.
     */
    id: string;

    /**
     * The method / method to unregister for.
     */
    method: string;
}
```

<div class="anchorHolder"><a href="#unregistrationParams" name="unregistrationParams" class="linkableAnchor"></a></div>

```typescript
export interface UnregistrationParams {
    // This should correctly be named `unregistrations`. However changing this
    // is a breaking change and needs to wait until we deliver a 4.x version
    // of the specification.
    unregistrations: Unregistration[];
}
```

An example JSON-RPC message to unregister the above registered `textDocument/willSaveWaitUntil` feature looks like this:

```json
{
    "method": "client/unregister_subscribed_method",
    "params": {
        "unregisterations": [
            {
                "id": "79eee87c-c409-4664-8102-e03263673f6f",
                "method": "textDocument/willSaveWaitUntil"
            }
        ]
    }
}
```
_Response_:
* result: void.
* error: code and message set in case an exception happens during the request.
