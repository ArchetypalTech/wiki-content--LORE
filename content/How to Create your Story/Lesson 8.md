# Lesson 8. Your choice now

You have reached almost the end of this journey. So lets add a couple more objects that will allow you to end this journey and embark into new ones.

## Last Entities
### Pegasus Carriages

Create an entity called `Pegasus Carriages` under **City Plaza**. 

Add:
- Reactable
- Description Texts
- Exit

Suggested values:

- **Entity.name**: *Pegasus Carriages*
- **Entity.alt_names**: *carriage*, *carriages*
- **Description 0**: *some pegasus CARRIAGES*
- **Description 1**: *The finnest carriages of the continent lead by pegasus. They will take you to the Flying Ship*
- **Reactable.new_entry**: *some pegasus CARRIAGES*
- **Reactable.actions**:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |
- **Exit.is_enterable**: *true*
- **Exit.leads_to**: *Flying Ship*
- **Exit.direction**: *Up*


### Flying Ship

Create an entity called `Flying Ship` under **City Plaza**. 

Add:
- Area
- Reactable
- Description Texts
- Exit
- Hub

Suggested values:

- **Entity.name**: *Flying Ship*
- **Entity.alt_names**: *ship*
- **Area.is_spawn**: *false*
- **Area_percentage**: *100*
-
- **Description 0**: *a flying SHIP*
- **Description 1**: *This magic ship will take you to more adventures. If you are not ready, you can just EXIT the SHIP and be back at the City Plaza. Otherwise, good luck in your new adventures!*
- **Reactable.new_entry**: *a flying SHIP*
- **Reactable.actions**:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |
- **Exit.is_enterable**: *true*
- **Exit.leads_to**: *Flying Ship*
- **Exit.direction**: *Up*
- **Hub.is_enabled**: *true*
- **Hub.grants_editor_access**: *false*

## Add More

There is always more content that can be added:
- Triggers using:
	- `OnEnter`
	- `OnExit`
- Condition:
	- `AddValue`
	- `ReduceValue`
	- `GreaterThan`
	- `LessThan`

But you can also have your unique system like having an entity parent that stores other entities for controling variables like: stealth, strengh, stamina, mana, qi, you mention. The point is:

**DESIGN AND CREATE YOUR OWN STORIES**
	
## The End

Thanks for following up with this guide on how to create your own stories using O'RuggEd. By the where you learned that:

- `Area` defines playable spaces.
- `Exit` defines movement between spaces.
- `InventoryItem` defines carried and pickable objects.
- `Reactable` and `DescriptionText` define what the player can perceive.
- `Action`, `Trigger`, `Condition`, and `Effect` define how the story changes state.
- Parent-child hierarchy defines where entities live in the world.

This is the main teaching outcome of the lesson:

O'RuggEd stories are assembled from reusable world objects and interaction rules. Once a learner understands this example, they can reuse the same patterns for doors, keys, offerings, enemies, switches, ritual objects, and larger quest chains.