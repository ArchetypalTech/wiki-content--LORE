# Creating Worlds In LORE

Creating a world in LORE means defining a playable text-based environment that players can enter, explore, and interact with through commands.


## General Process  

At a high level, creating a world in LORE involves:

1. defining the structure of the world

2. authoring descriptions and interaction content

3. configuring how the world responds to player input

4. publishing or exposing that world for play

The exact implementation details can vary, but the overall workflow is oriented around turning authored content into a playable runtime experience.

For a detailed guide plese check [[GUIDE FOR CREATING YOUR WORLD]]


## What A Creator Defines

A creator typically defines:

- spaces or locations

- objects or entities within those spaces

- descriptive text shown to players

- pathways or navigation between spaces

- interactions and responses

- rules that determine how the world changes during play

These pieces together form the playable structure of a LORE world.
  

## Authoring Model

LORE is designed for authored interactive worlds rather than only procedural or sandbox-style environments. This means creators shape how players move through the experience, what they can discover, and how the world responds to their actions.

Because LORE is text-first, writing is a major part of world creation. Descriptions, responses, and interaction phrasing are not secondary interface details. They are part of the core design of the experience.


## Editor And Contract Roles
  
In this repository, world creation is supported by both client-side and contract-side systems.

- The client package provides an editor-facing interface for building and managing worlds.

- The contracts package provides the underlying systems that store and enforce the authored world data.

This separation allows creators to work through editing tools while relying on the contract layer as the persistent runtime.


## Publishing

Once authored, a world can be made available for players to enter and interact with. In LORE, publication is part of the broader system of organizing and exposing playable experiences rather than only exporting static content.


## Summary

Creating a world in LORE means authoring a text-based interactive environment and preparing it to run as part of LORE's persistent onchain play system.