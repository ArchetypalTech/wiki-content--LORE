# Game And Trail Systems

The O'RuggEd game and trail systems define how individual playthroughs are tracked and how authored experiences are grouped, published, and progressed through.

These systems are closely related, but they are not the same thing.

- The game system is about a player's specific game instance.
- The trail system is about a published or identifiable path of content inside the wider world.  

Taken together, they allow O'RuggEd to support persistent runs, instance-specific state, and progress across both the main game path and optional or separate trails.

  
## Overview

In the contracts package, these ideas are primarily represented by:

- `game_instance.cairo`
- `game_token_info.cairo`
- `hub.cairo`
- `trail_token_info.cairo`

Each file handles a different part of the model:

- `game_instance.cairo` defines how authored world data can have game-specific versions
- `game_token_info.cairo` stores metadata and progress for a game instance
- `hub.cairo` defines hubs and trails as top-level world structures
- `trail_token_info.cairo` stores trail identity and per-game trail progress

## Game System

The game system represents a specific run or play session in O'RuggEd.

It is centered on `game_id`, which is used throughout the contracts package to separate one player's game state from another. This is what allows the same authored world to support multiple independent playthroughs.


### Game Instances

The main logic for game instances appears in `game_instance.cairo`. This file defines a mapping layer that allows a model to exist in two forms:

- the authored base version
- a game-specific instance version

For models keyed by `inst`, the system can generate a derived instance key from the original entity identifier plus a `game_id`. For models keyed by `(inst, key)`, it provides the same idea for keyed records.
  
This means a game instance does not need to duplicate the whole world up front. Instead, it can read the base model by default and only persist a game-specific version when a component changes.


### Game Instance Maps

`game_instance.cairo` defines:

- `GameInstanceMap`
- `GameInstanceKeyMap`

These models store the relationship between:

- the original authored instance
- the active `game_id`
- the derived game-specific instance key

This helps the client and runtime discover which world records have been overridden for a particular run.


### Game Token Metadata

The main metadata model for a game instance is `GameTokenInfo` in `game_token_info.cairo`. It stores:

- the `game_id`
- the minter address
- a seed
- the current room name
- the current act number

This is a compact summary of a game run. It does not replace the full per-game world state, but it provides the high-level status of a game instance in a form that can be surfaced externally.


### Game Progress

The game system also tracks progress as the player moves through the world. 
In `game_token_info.cairo`, entering a room can update:

- the displayed room name
- the player's progress in the main trail
- the current act number

The file treats the main game progression as a special trail with `MAIN_TRAIL_ID`, which means overall game progress is modeled as a specific kind of trail progress rather than as a completely separate mechanism.


## Trail System

The trail system represents authored paths or experiences within the larger O'RuggEd world.
A trail is not only a progress counter. It is also a world-level object with identity, publication state, and a relationship to hubs.

This is primarily defined in `hub.cairo` and `trail_token_info.cairo`.

  
### Hubs And Trails
  
`hub.cairo` defines two important models:

- `Hub`
- `Trail`

A `Hub` is a world structure that can contain multiple trails. It can be enabled or disabled, can list the trail instances it contains, and can optionally grant editor access when reached.
  
A `Trail` is a top-level trail entity that includes:

- its own instance id
- a `trail_id`
- a reference to its parent hub
- a publication flag

This means the trail system is partly about organization and discovery. Trails are grouped inside hubs, and hubs can expose published trails to players.


### Published Experiences

The hub model includes methods for working with published trails only. This indicates that trails are meant to be surfaced as discoverable experiences rather than as internal-only structures.

At the model level, a hub can return its published trail entities, which makes the hub a useful entry point for presenting available experiences within the world.


### Trail Identity And Metadata

`trail_token_info.cairo` defines `TrailTokenInfo`, which stores:

- the `trail_id`
- the minter address
- a seed
- the top-level trail entity instance

This provides a stable identity layer for trails, similar to how `GameTokenInfo` provides metadata for game instances.

The same file also exposes a helper for resolving a trail's human-readable name through its associated entity.

  
### Trail Progress

Progress within a trail is represented by the `TrailProgress` model in `trail_token_info.cairo`.

It is keyed by:

- `game_id`
- `trail_id`  

and stores:

- a percentage
- a completion flag

This is important because trail progress is tracked per game instance. A trail is a shared authored structure, but completion of that trail belongs to an individual game run.

The progress logic also behaves monotonically:

- percentage is clamped to `100`
- lower values do not overwrite higher recorded progress
- reaching `100` marks the trail as completed

  
## Relationship Between Games And Trails

The game and trail systems are designed to work together.

- A game instance represents a specific run.
- A trail represents a path or content grouping inside the world.
- Trail progress is recorded for each game instance.
- Overall game progress is derived from the main trail.

This means O'RuggEd can support both:

- a primary progression path for the game as a whole
- additional or separate trails that can be entered, tracked, and completed independently

## Why These Systems Matter

Together, the game and trail systems give O'RuggEd a way to separate authored content from player-specific progression. They allow the engine to:

- preserve independent playthroughs
- expose published world paths as named experiences
- track progress across the main story and side trails
- summarize game state in lightweight metadata models
- keep mutated state scoped to a specific game instance
  
Without these systems, O'RuggEd would have persistent world data, but it would be much harder to represent individual runs and structured progress through different narrative paths.

  
## Summary

The O'RuggEd game system tracks a specific playthrough through per-game instance state and metadata, while the trail system defines published world paths and records progress through those paths on a per-game basis.