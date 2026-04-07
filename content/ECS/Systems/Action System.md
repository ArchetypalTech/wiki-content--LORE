# Action System

The LORE action system defines how the world responds to player activity.

At a high level, an action is a structured unit of gameplay logic. It can be attached to an entity, checked against runtime conditions, and used to change the state of the world. Currently, the action system is primarily composed by four related components:

- `Action`

- `Trigger`

- `Condition`

- `Effect`

Together, these models define when something can happen, whether it is allowed to happen, and what changes when it does.

  
## Overview

An action in LORE is not just a single command handler. It is a composed rule made up of smaller parts.

- The `Action` container is the main elemente.

- `Trigger` define when the action is considered eligible to run.

- `Condition` define what must be true for the action to succeed.

- `Effect` define what changes in the world when the action is applied.

  
This structure makes the system declarative. Instead of hardcoding every interaction as a custom flow, LORE can represent many interactions as data-driven combinations of triggers, conditions, and effects.

## Components
### Action

The `Action` component is the central unit of the system. It contains:

- identity fields (`inst` and `key`)
- a name 
- description (can be used as a hint)
- an `executor` field that identifies which entity is allowed to invoke the action
- lists of linked triggers, conditions, and effects
- tags for filtering or discovery
- success and failure response text

An action is attached to the entity which is the target of the action and registered into that entity's `actions_keys` list. This means actions are associated with world objects or locations rather than existing only as global commands.


### Trigger

Triggers define the circumstances in which an action becomes valid to evaluate. Each trigger includes:

- an owning entity and key
- a name
- a `trigger_type`
- an enabled flag
- an `is_once` flag


The implementation in `trigger.cairo` explicitly evaluates several trigger types, including:

- `OnEnter`
- `OnExit`
- `OnUse`  

These are checked against the current game state. For example: 

- `OnEnter` checks whether a player is present among an area's children
- `OnExit` checks whether a player is no longer present
- `OnUse` checks inventory-item usage state


Triggers can also be indexed by trigger type, which supports lookup and grouping at the system level.


### Condition

Conditions define the state requirements that must hold before an action can succeed. Each condition identifies:  

- a target entity
- a component type
- a property name
- a comparison operator
- a value to compare against

In practice, a condition reads a property from a component on the target entity and compares it to the expected value. The comparison operators in `condition.cairo` include equality and inequality checks as well as greater-than and less-than comparisons.

This makes conditions the gatekeeping layer of the action system. A trigger may say that an action is being attempted in the right context, while a condition answers whether the state of the world actually permits the action to proceed.
  
The `value` input field accepts is of type `felt252` but when setting up on the `Editor Tool` you can insert the value as `string`, `int`,  and`number`  without worring about the conversion as we handle that ourself.  Yet you can always use **[Stark-utils](https://www.stark-utils.xyz/converter)** to get the corresponding value. For the case of `boolean` you can refer them as `string` *false* or *true* that correspond to `0n` and `1n`.


### Effect

Effects define the state changes produced by a successful action. Each effect identifies:

- a target entity
- an effect type
- a component type
- a property to change
- the value to apply

Effects are responsible for mutating the world. Depending on the targeted component and property, an effect may change text, ownership, visibility, inventory state, container state, player state, or other registered component properties.

Two details from the current implementation are especially important:

- If an effect's `target` is `0`, it falls back to the runtime `TriggerContext` target.
- Effects only apply when the source entity and target are in the same trail.

This helps keep effects contextual and scoped to the relevant part of the world.


## Execution Flow

The action execution flow in `action.cairo` follows a consistent order:
  
1. Check whether the action has already been executed for the current game instance.

2. Check whether the action is being called by the correct executor.

3. Evaluate all linked triggers.

4. Evaluate all linked conditions.

5. Apply all linked effects if triggers and conditions succeeded.

6. Mark the action as executed and emit success responses, or emit failure responses.

This sequence is important because the action system separates validation from mutation. Triggers and conditions are evaluated first, and only then are effects applied.


## Per-Game Execution State
  
Actions and triggers track execution state per `game_id`.

This means an action that has already fired in one game instance does not automatically count as executed in every other game instance. The action system therefore supports persistent but instance-specific progression, which matches LORE's broader model of per-game state.

For actions marked by state as one-time interactions, this per-game execution record is what prevents repeated use within the same run.


## Responses And Player Feedback

The `Action` model stores both success and failure responses.

This is an important part of the design. An action does not only change state. It also provides authored feedback to the player, allowing interaction logic and narrative output to stay closely connected.


## Why The System Matters

The action system is one of the main ways LORE turns authored world data into gameplay.

Rather than treating interactions as isolated scripts, it organizes them into reusable parts:

- triggers describe when an interaction is active

- conditions describe what must be true

- effects describe what changes

- actions bind those pieces together and provide player-facing responses

This makes the system suitable for text adventure interactions, reactive environments, gated progression, and stateful story events.


## Summary

The LORE action system is a data-driven interaction framework in which actions coordinate triggers, conditions, and effects to decide when world interactions can occur and how they change persistent game state.

Please review the HOW TO CREATE YOUR STORY GUIDE for a pratical example of how to add an Action System in your story.