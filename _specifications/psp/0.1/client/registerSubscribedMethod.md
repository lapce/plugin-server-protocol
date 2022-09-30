#### <a href="#register_subscribed_method" name="register_subscribed_method" class="anchor">Register Methods (:arrow_right_hook:)</a>

> *Since version 0.1.0*

The `methodclient/registerSubscribedMethod` request is sent from the server to the client to register for a new subscribed method on the client side. Not all clients need to support dynamic method registration. A client and server opts in via the `DynamicMethodRegistration` property on the specific client capabilities.

Server must not register the same subscribed methods both statically through the initialize result and dynamically. If a server wants to support both static and dynamic registration it needs to check the client capability in the initialize request and only register the capability statically if the client doesn't support dynamic registration for that capability.

*Client Capability*:

* property name (optional): `psp.DynamicMethodRegistration`

*Server Capability*:

* property name (optional): `psp.DynamicMethodRegistration`

*Request*:

* method: 'methodclient/registerSubscribedMethod'
* params: `MethodRegistrationParams`

Where `MethodRegistrationParams` are defined as follows:

<div class="anchorHolder"><a href="#methodRegistrationParams" name="methodRegistrationParams" class="linkableAnchor"></a></div>

```typescript
/**
 * General parameters to register for a capability.
 */
export interface MethodRegistrationParams {
    /**
     * The id used to register the request. The id can be used to deregister
     * the request again.
     */
    id: string;

    /**
     * The methods to register for.
     * All the LSP and PSP methods can be used as methods
     * Note that Registration is an LSP type.
     * empty array defaults to no method registered
     */
    methods: Registration[];
}
```

*Response*:

* result: void.
* error: code and message set in case an exception happens during the request.
