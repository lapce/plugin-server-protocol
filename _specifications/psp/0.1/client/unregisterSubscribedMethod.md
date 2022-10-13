#### <a href="#unregister_subscribed_method" name="unregister_subscribed_method" class="anchor">Unregister Method (:arrow_right_hook:)</a>

> *Since version 0.1.0*

The `methodclient/unregister_subscribed_method` request is sent from the server to the client to unregister a previously registered method.

*Client Capability*:

* property name (optional): `psp.dynamicMethodRegistration`

*[Server] Capability*:

* property name (optional): `psp.dynamicMethodRegistration`

*Request*:

* method: 'methodclient/unregisterSubscribedMethod'
* params: `MethodUnregistrationParams`

Where `MethodUnregistrationParams` are defined as follows:

<div class="anchorHolder"><a href="#methodUnregistrationParams" name="MethodUnregistrationParams" class="linkableAnchor"></a></div>

```typescript
/**
 * General parameters to unregister a method.
 */

export interface MethodUnregistrationParams {
    /**
     * The id used to unregister the request or notification. Usually an id
     * provided during the register request.
     * An id can be shared across multiple registered methods
     */
    id: string;

    /**
     * The method / methods to unregister for.
     */
    method: string[];
}
```

*Response*:

* result: void.
* error: code and message set in case an exception happens during the request.
