#### <a href="#client_registerSubscribedMethod" name="client_registerSubscribedMethod" class="anchor">Register Methods (:arrow_right_hook:)</a>

The `client/registerSubscribedMethod` request is sent from the server to the client to register for a new subscribed method on the client side. Not all clients need to support dynamic method registration. A client opts in via the `dynamicSubscribedRegistration` property on the specific client capabilities.

Server must not register the same subscribed methods both statically through the initialize result and dynamically for the same document selector. If a server wants to support both static and dynamic registration it needs to check the client capability in the initialize request and only register the capability statically if the client doesn't support dynamic registration for that capability.

_Request_:
* method: 'client/registerSubscribedMethod'
* params: `RegistrationParams`

Where `RegistrationParams` are defined as follows:

<div class="anchorHolder"><a href="#registration" name="registration" class="linkableAnchor"></a></div>

```typescript
/**
 * General parameters to register for a capability.
 */
export interface Registration {
    /**
     * The id used to register the request. The id can be used to deregister
     * the request again.
     */
    id: string;

    /**
     * The method / capability to register for.
     */
    method: string|string[];

    /**
     * Options necessary for the registration.
     */
    registerOptions?: LSPAny;
}
```

_Response_:
* result: void.
* error: code and message set in case an exception happens during the request.

`StaticRegistrationOptions` can be used to register a feature in the initialize result with a given server control ID to be able to un-register the feature later on.

<div class="anchorHolder"><a href="#staticRegistrationOptions" name="staticRegistrationOptions" class="linkableAnchor"></a></div>

```typescript
/**
 * Static registration options to be returned in the initialize request.
 */
export interface StaticRegistrationOptions {
    /**
     * The id used to register the request. The id can be used to deregister
     * the request again. See also Registration#id.
     */
    id?: string;
}
```