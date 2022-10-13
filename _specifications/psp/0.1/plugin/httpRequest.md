#### <a href="#httpRequest" name="httpRequest" class="anchor">Make an Http Request</a>

> *Since version 0.1.0*

The `HttpRequest` request is sent from the server to the client when it needs to access a resource over the network.

*Client Capability*:

* property name (optional): `psp.httpRequest`

*Server Capability*:

* property name (optional): `psp.httpRequest`

*Request*:

* method: `psp/httpRequest`
* params: `HttpRequestParams` defined as follows:

<div class="anchorHolder"><a href="#httpRequestParams" name="HttpRequestParams" class="linkableAnchor"></a></div>

```typescript
export interface HttpRequestParams {
    /**
     * The HTTP method
    */
    method: "GET" | "POST" | "PUT" | "DELETE";
    /**
     * The URL to send the request to.
    */
    url: URI;
    /**
     * The output file where response data should be written.
     * If "response", data is sent in the response of the request.
    */
    output: URI | "response";
    /**
     * List of all headers of the response.
     * Strings should be of format NAME: VALUE where NAME is the header name, and VALUE is the header value
     * Headers disallowed: Content-Length
    */
    headers: string[];
    /**
     * Follow redirects.
     * Integer is the number of max hops.
     * True allows unlimited hops
     * False allows no hops
     * 'default' means the http client gets to decide.
    */
    redirects: boolean | integer | 'default';
    /**
     * Body contents.
    */
    body: string | Uint8Array;
}
```

*Response*:

* result: `HttpRequestResponse`
* error: code and message as `HttpRequestResponse` or string set in case an exception happens during the declaration request.

where `HttpRequestResponse` defined as follows:

<div class="anchorHolder"><a href="#httpRequestResponse" name="HttpRequestResponse" class="linkableAnchor"></a></div>

```typescript
export interface HttpRequestResponse {
    /**
     * Status code of the response.
    */
    statusCode: integer;
    /**
     * List of all headers of the response.
     * Strings should be of format NAME: VALUE where NAME is the header name, and VALUE is the header value
    */
    headers: string[];
    /**
     * Body of the response
    */
    body: string | Uint8Array;

    /**
     * URI of the downloaded data.
    */
   location: URI;
}
```
