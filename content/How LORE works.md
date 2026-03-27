# How LORE Works

LORE operates as a text-driven game system in which authored world data, player input, and persistent game state are connected through onchain logic.

## High-Level Flow

At a high level, LORE works through three connected layers:

1. World definition

2. Player interaction

3. Persistent progression

World definition provides the structure and authored content of a playable environment. Player interaction allows a user to issue text commands and receive responses. Persistent progression ensures that the results of play can be stored and reused across sessions.


## World Definition

A LORE world is made up of authored game data that describes places, objects, descriptions, relationships, and interaction rules. This data defines what exists in the world and how it can respond.

In the repository, this is primarily represented in the contract package through models and systems that store and manage world state.


## Player Interaction

Players interact with LORE through text commands. A command is submitted to the runtime, interpreted by the system, and resolved against the current game context.

This interaction loop generally involves:

1. receiving a player command

2. parsing or interpreting that command

3. checking the relevant game state

4. applying the result of the interaction

5. returning text output to the player

This makes LORE closer to a runtime for interactive fiction than to a static content viewer.
  

## Persistent Progression

LORE keeps track of play state across game instances. This allows different players, or different runs, to have their own evolving record of progression rather than a single shared snapshot of content.

Depending on the system being used, progression may include:

- current location

- story output history

- available interactions

- access and publishing state

- token-related gameplay state  


## Published Worlds and Discovery

The contract structure also supports the idea of published experiences and discoverable world groupings. In practice, this means LORE is not limited to a single isolated adventure. It can support a broader ecosystem of authored worlds and entry points.


## Summary
  
LORE works by connecting authored world data, text command processing, and persistent onchain state into a playable interactive fiction runtime.