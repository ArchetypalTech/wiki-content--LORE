# Lesson 7. Build The Teleport Activation Logic
  
With the Dragon Heart in posession the player can now use it on the Teleport and then travel to the City Plaza


## Dragon Heart

On the **Dragon Heart** now, add:  

- one Trigger


#### Dragon Heart Trigger 

Set:

- **Trigger.name**: *Transfer dragon's mana*
- **Trigger.trigger_type**: *OnUse*
- **Trigger.is_enabled**: *true*
- **Trigger.was_triggered**: *false*
- **Trigger.is_once**: *false*


## Shrine Teleport

On the **Teleport Shrine** now, add:

- two Condition
- two Effects
- one Action
  

### Teleport's Conditions

#### Condition 1. Teleport Shrine Deactivated

The first condition is that the **Teleport Shrine** can't be used.

- **Condition.name**: *Deactivated Teleport*
- **Condition.entity_target**: *Teleport Shrine*
- **Condition.component**: *Exit*
- **Condition.property**: *is_enterable*
- **Condition.operator**: *Equals*
- **Condition.value**: *false*

#### Condition 2. Own the Dragon Heart

The second condition is that the **PLAYER** must be in posession of the **Dragon Heart**.

- **Condition.name**: *Own Dragon Heart*
- **Condition.entity_target**: *Dragon Heart*
- **Condition.component**: *InventoryItem*
- **Condition.property**: *owner_id*
- **Condition.operator**: *Equals*
- **Condition.value**: *Player*


### Teleport's Effects

#### Effect 1. Change the Teleport's exit state

Lets enable the use of the teleport:

- **Effect.name**: *Activate Teleport*
- **Effect.entity_target**: *Teleport Shrine*
- **Effect.effectType**: *ModifyProperty*
- **Effect.component**: *Exit*
- **Effect.property**: *is_enterable*
- **Effect.text_value**: 
	- **Value**: *true*
	- **Idx**: *0* or you can leave empty 


#### Effect 2. Change the Teleport's description

Lets enable the use of the teleport:

- **Effect.name**: *Teleport New Text*
- **Effect.entity_target**: *Teleport Shrine*
- **Effect.effectType**: *ModifyProperty*
- **Effect.component**: *Reactable*
- **Effect.property**: *description*
- **Effect.text_value**: 
	- **Value**: *A ring of ancient stone surrounds a sleeping teleport gate. At its center a red orb of mana rotates with power*
	- **Idx**: *1* 


### Teleport's Action

  Now,  the only step left is to connect every element through the `Action`.

Set:

- **Action.name**: *Activate Teleport*
-  **Action.description**: *A huge amount of mana is missing. Maybe something can enable it.*
- **Action.is_enabled**: *true*
- **Action.executor**: *Dragon Heart*
- **Action.triggers**:  

| Trigger Entity | Trigger Key            |
| -------------- | ---------------------- |
| Dragon Heart   | Transfer dragon's mana |
- **Action.conditions**:  

| Condition Entity | Conditioni Key       |
| ---------------- | -------------------- |
| Teleport Shrine  | Deactivated Teleport |
| Teleport Shrine  | Own Dragon Heart     |
- **Action.effects**:  

| Effect Entity   | Effect Key        |
| --------------- | ----------------- |
| Teleport Shrine | Activate Teleport |
| Teleport Shrine | Teleport New Text |
- **Action.failing_response**: 
	- *You can't activate the teleport if:*
	- *It is already activated*
	- *Or*
	- *You don't have the dragon heart*
- **Action.success_response**:
	- You took the dragon heart and placed in front of the socket
	- Suddently, red thin streams started to converge on the center of the socket 
	- After a bit of time, a red orb of mana can be seen on the socket while glowing brightly. 
	- Exhausted, you press your hand on the orb so that you can teleport to the new destination


## Teaching Note


This implementation repeats the same logic model from the dragon encounter: have an object, use it on a target and trigger an action.

As a general rule:

- item-on-target interactions are authored consistently across very different story situations
- you can adjust the setup of the action system as you see fit.

  
### Checkpoint

After testing:

- the dragon heart should activate the teleport
- the teleport should become enterable
- the player should then be able to use the shrine as an exit


### Next Step

Returning to the city is now possible. Just use the dragon heart on the teleport to enable it and then use it. As you are reaching the end of the journey, there is a thing or two still need to be done. So, here we go at [[Lesson 8]].