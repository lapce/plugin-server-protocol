#### <a href="#registerCommand" name="registerCommand" class="anchor">Register new command Request</a>

> *Since version 0.1.0*

The Register Command request is sent from the server to the client when it wants to create a new integrated command. Such command can then be invoked by the user.

*Client capability*:

* property name (optional): `psp.registerCommand`

*Server capability*:

* property name (optional): `psp.registerCommand`

*Request*:

* method: `psp/registerCommand`
* params: `RegisterCommandParams`defined as follows:

<div class="anchorHolder"><a href="#registerCommandParams" name="RegisterCommandParams" class="linkableAnchor"></a></div>

```ts
export interface RegisterCommandParams {
  /**
     * Commands to register.
    */
  commands: RegisterCommand[];
}
```

where `RegisterCommand` defined as follows:

<div class="anchorHolder"><a href="#registerCommand" name="RegisterCommand" class="linkableAnchor"></a></div>

```ts
export interface RegisterCommand {
    /**
     * Id of the command.
    */
    label: string;
    /**
     * Description of the command.
    */
    description: string;
}
```

*Response*:

* result `null`
* error: code and message set in case an exception happens during the declaration request.

#### <a href="#triggerCommand" name="triggerCommand" class="anchor">Trigger command Notification</a>

When a user Executes a command, a notification is sent from the client to the server:

*Client capability*:

* property name (optional): `psp.registerCommand`

*Server capability*:

* property name (optional): `psp.registerCommand`

*Notification*:

* method: `psp/triggerCommand`
* params: `TriggerCommandParams`defined as follows:

<div class="anchorHolder"><a href="#triggerCommand" name="TriggerCommand" class="linkableAnchor"></a></div>

```ts
export interface TriggerCommandParams {
    /**
     * The name of the triggered command.
    */
    command: string;
}
```

#### <a href="#unregisterCommand" name="unregisterCommand" class="anchor">Unregister command Request</a>

> *Since version 0.1.0*

The Unregister Command request is sent from the server to the client when it wants to delete an previously created command.

*Client capability*:

* property name (optional): `psp.registerCommand`

*Server capability*:

* property name (optional): `psp.registerCommand`

*Request*:

* method: `psp/unregisterCommand`
* params: `RegisterCommandParams`defined as follows:

<div class="anchorHolder"><a href="#unregisterCommandParams" name="UnrgisterCommandParams" class="linkableAnchor"></a></div>

```ts
export interface UnregisterCommandParams {
  /**
     * Commands to unregister.
    */
  commands: RegisterCommand[];
}
```

*Response*:

* result `null`
* error: code and message set in case an exception happens during the declaration request.
