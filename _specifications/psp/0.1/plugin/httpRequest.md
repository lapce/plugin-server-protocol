#### <a href="#http_request" name="http_request" class="anchor">Make an Http Request</a>

> *Since version 0.1.0*

The `HttpRequest` request is sent from the server to the client when it needs to access a resource over the network.

*Client Capability*:

* property name (optional): `general.HttpRequest`

*Server Capability*:

* property name (optional): `general.HttpRequest`

*Request*:

* method: `general/httpRequest`
* params: `HttpRequestParams` defined as follows:

<div class="anchorHolder"><a href="#HttpRequestParams" name="HttpRequestParams" class="linkableAnchor"></a></div>

```typescript
export interface HttpRequestParams {
     method: "GET"|"POST"|"PUT"|"DELETE";
    // The URL to send the request to.
    url: URI;
    // The output file where response data should be written.
    // If "response", data is sent in the response of the request.
    output: URI|"response";
    // Header fields.
    headers: String[];
    // Follow redirects. Number is the number of max hops.
    redirects: boolean|Number;
    // Body contents.
    body: Uint8Array;
}
```

*Response*:

* result: `HttpRequestResponse`
* error: code and message as `HttpRequestResponse` or string set in case an exception happens during the declaration request.

where `HttpRequestResponse` defined as follows:

<div class="anchorHolder"><a href="#HttpRequestParams" name="HttpRequestParams" class="linkableAnchor"></a></div>

```typescript
export interface HttpRequestResponse {
    // Status code of the response.
    statusCode: int,
    // List of all headers of the response.
    headers: String[],
    // Body of the response, or URI of the downloaded data.
    body: Uint8Array,
}
```
