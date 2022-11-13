#### <a href="#askInputChoice" name="askInputChoice" class="anchor"> Ask for inputs / choices requests</a>

a server can then ask for user inputs based on the command invoked. It can use two type of input request:

* `AskInput`: The user enters an arbitratry string
* `AskChoice`: The user selects one or more choices from a list

*Client capability*:

* property name (optional): `psp.registerCommand`

*Server capability*:

* property name (optional): `psp.registerCommand`

*Notification*:

* method: `psp/askInput`
* params: `askInput`defined as follows:

<div class="anchorHolder"><a href="#askInputChoice" name="AskInput" class="linkableAnchor"></a></div>

```ts
export interface AskInput {
    /**
     * Id of the command related to this input.
    */
    id: integer;
    /**
     * Title of the input.
    */
    title: string;
    /**
     * Placeholder to be shown inside the input field.
    */
    placeholder?: string;
    /**
     * Hints about the way to fill this data.
    */
    hint?: string | URI;
}
```

*Response*:

* result `AskInputResponse`
* error: code and message set in case an exception happens during the declaration request.

where `AskInputResponse` defined as follows:

<div class="anchorHolder"><a href="#askInputResponse" name="AskInputResponse" class="linkableAnchor"></a></div>

```ts
export interface AskInputResponse {
    /**
     * Id of the command related to this input.
    */
    id: integer;
    /**
     * Response of the user
    */
    response: string[];
}
```

*Client capability*:

* property name (optional): `psp.registerCommand`

*Server capability*:

* property name (optional): `psp.registerCommand`

*Request*:

* method: `psp/askChoice`
* params: `askInput`defined as follows:

<div class="anchorHolder"><a href="#askChoice" name="AskChoice" class="linkableAnchor"></a></div>

```ts
export interface AskChoice {
    /**
     * Id of the command related to this input.
    */
    id: integer;
    /**
     * Title of the input.
    */
    title: string;
    /**
     * Choices the user can choose.
    */
    choices: Choice[];
    /**
     * Minimum number of choices the user can choose
     * Defaults to one
    */
    minChoices?: integer;
    /**
     * Maximum number of choices the user can choose
     * Defaults to one
     * For unlimited number of choice, set to zero
    */
    maxChoices?: integer;
    /**
     * Default selected choices indices.
    */
    defaultChoices?: integer[]
    /**
     * Hints about the way to fill this data.
    */
    hint?: string|URI;
}
```

where `Choice` defined as follows:

<div class="anchorHolder"><a href="#choice" name="Choice" class="linkableAnchor"></a></div>

```ts
export interface Choice {
    /**
     *  The text that should be displayed for the choice
    */
    text: string,
    /**
     *  The icon that should be displayed for the choice
     *  The icon is a local only image.
    */
    icon?: Uri,
    /**
     *  Hint which gives a small amount of extra information about the choice
    */
    hint?: string,
}
```

*Response*:

* result `AskChoiceResponse`
* error: code and message set in case an exception happens during the declaration request.

where `AskChoiceResponse` defined as follows:

<div class="anchorHolder"><a href="#askChoiceResponse" name="AskChoiceResponse" class="linkableAnchor"></a></div>

```ts
export interface AskChoiceResponse {
    /**
     *  Response of the user
     *  This is a list of indices of choice chosen
    */
    response: integer[];
}
```
