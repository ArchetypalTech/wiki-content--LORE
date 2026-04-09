
LORE is a fully onchain interactive multiplayer fiction engine inspired by classic text adventures, MUDs, and games like Zork.
  
It gives creators a way to build playable story worlds where players interact through text commands such as moving, inspecting, using objects, or triggering story events. Unlike a traditional game backend, LORE keeps the important game logic and world state onchain, making the world persistent, shared, and programmable.

## Overview

At its core, LORE is a system for building and playing text-first worlds.

Creators can author places, objects, descriptions, interactions, and story paths. Players can then enter those worlds, type commands, and progress through them as the system updates their game state. Because the runtime lives onchain, the world is not just content hosted by a server. It is part of a persistent onchain game system.

LORE is built with Dojo and Cairo for Starknet, which makes it part game engine, part world framework, and part smart contract infrastructure.

## What Makes LORE Different

Most text adventures are single-player games that run locally or on a centralized server. LORE takes a different approach.  

- It is onchain, so world state and progression can be stored and enforced by smart contracts.

- It is multiplayer by design, so many players can participate in the same broader ecosystem of worlds.

- It is creator-friendly, with tools for building and publishing interactive fiction worlds.

- It is modular, allowing story spaces, interactions, and progression systems to be composed into larger experiences.

- It is text-native, meaning language and command input are central to how players experience the world.
 

## How LORE Works

In simple terms, LORE connects three layers:

1. A world creation layer for authors and designers.

2. A runtime layer that interprets player commands and updates the world.

3. A progression layer that tracks play sessions, access, and game-related rewards or tokens.

This allows a creator to publish a world, a player to enter it, and the engine to respond to their actions while preserving the state of that journey.

Please check [[How LORE works]] for further detail.

## For Players

For players, LORE feels like stepping into a living text world. You explore by typing commands, reading responses, and uncovering paths, objects, and story moments. Your progress is not just a temporary local save file. It can be part of a persistent onchain record of play.


## For Creators

For creators, LORE is a framework for publishing interactive fiction in a more systemic way. Instead of writing only linear passages, creators can build explorable spaces, define how the world responds, and shape how players progress through a shared environment.

This makes LORE useful for:

- interactive fiction

- adventure games

- collaborative or community-authored worlds

- onchain storytelling experiments

- game systems that mix narrative and programmable logic

A small summary can be check at [[Creating Worlds in LORE]]
## In One Sentence

LORE is an onchain engine for creating and playing multiplayer text-based story worlds.