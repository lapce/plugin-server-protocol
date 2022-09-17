#### <a href="#register_command" name="register_command" class="anchor">Register new command</a>

> *Since version 0.1.0*

The Register Command request is sent from the server to the client when it wants to create a new integrated command. Such command can then be invoked by the user.

*Client capability*:

* property name (optional): `psp.RegisterCommand`

*Server capability*:

* property name (optional): `psp.RegisterCommand`

*Request*:

* method: `psp/registerCommand`
* params: `RegisterCommandParams`defined as follows:

<div class="anchorHolder"><a href="#registerCommandParams" name="RegisterCommandParams" class="linkableAnchor"></a></div>

```ts
export interface RegisterCommandParams {
  // Commands to register.
  commands: RegisterCommand[];
}
```

where `RegisterCommand` defined as follows:

<div class="anchorHolder"><a href="#registerCommand" name="RegisterCommand" class="linkableAnchor"></a></div>

```ts
export interface RegisterCommand {
    // Id of the command.
    label: string;
    // Description of the command.
    description: string;
}
```

*Response*:

* result `null`
* error: code and message set in case an exception happens during the declaration request.

a server can ask for user inputs based on the command invoked

```ts
export interface AskInputParams {
    // Id of the command related to this input.
    id: integer;
    // Title of the input.
    title: string;
    // Placeholder to be shown inside the input field.
    placeholder?: string;
    // Hints about the way to fill this data.
    hint?: string|URI;
}

export interface AskChoiceParams {
    // Id of the command related to this input.
    id: integer;
    // Title of the input.
    title: string;
    // Choices the user can choose.
    choices: string[];
    // Minimum number of choices the user can choose
    // Defaults to one
    minChoices?: integer;
    // Maximum number of choices the user can choose
    // Defaults to one
    // On unlimited number of choice, value is zero
    maxChoices?: integer;
    // Default selected choice index.
    defaultCHoices ?: integer[]
    // Hints about the way to fill this data.
    hint?: string|URI;
}

export interface AskForInputResponse {
    // Id of the command related to this input.
    id: Number;
    // Response of the user
    response: string[];
}
```

where `` defined as follows:
<div class="anchorHolder"><a href="#registerCommandParams" name="RegisterCommandParams" class="linkableAnchor"></a></div>
