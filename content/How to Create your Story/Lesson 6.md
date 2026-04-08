# Lesson 6. Build The Dragon Defeat Logic

As you know,  the `Action System` defines how the world responds to player activity. In this lesson we want to change the behaviour of the dragon  and its children objectes (the heart) after having defeated it. 

The question will be which object then calls the execution of the system? The answer: the jump of the trigger. In this case will be when the player uses the sword against the dragon.


## Sword 

So first, on the **Ebony Sword** entity add:

- one Trigger
- one Condition


###  Sword Trigger 

Set:

- **Trigger.name**: *use of sword*
- **Trigger.trigger_type**: *OnUse*
- **Trigger.is_enabled**: *true*
- **Trigger.was_triggered**: *false*
- **Trigger.is_once**: *false*

![[sword_trigger.png|390]]

The reason we set `Trigger.is_once` as `false` is that this allows to reuse the `OnUse` against other objects in case we want. For instance : if you 're fighting multiple enemies in the same location you can use the sword on all of them: *use sword on enemy-#*


### Sword Condition

The first condition is that the **PLAYER** must be in posession of the **Ebony Sword**.

- **Condition.name**: *Sword Equipped*
- **Condition.entity_target**: *Ebony Sword*
- **Condition.component**: *InventoryItem*
- **Condition.property**: *owner_id*
- **Condition.operator**: *Equals*
- **Condition.value**: *Player*

![[sword_condition.png]]

***Note:*** If `Condition.value` no longer shows `Player` don't worry as the internal convertor has changed from `string` to `felt252`. You can always click at the end of the entry value and it will show back as a `string`.

![[sword_cond_change.png]]


## Red Dragon

On the **Red Dragon** entity, add:

- one Condition
- three Effects
- one Action

And we add them to the **Red Dragon** as he is the target entity and to have the `Action elements` grouped as much as possible for easy setup.


### Dragon Condition

The first is that the dragon has not been defeated yet. The variable `Container.can_be_opened` can be used for checking.

- **Condition.name**: *Dragon Alive*
- **Condition.entity_target**: *Red Dragon*
- **Condition.component**: *Container*
- **Condition.property**: *can_be_opened*
- **Condition.operator**: *Equals*
- **Condition.value**: *false* or *0* that is *(0n)*

![[dragon_condition.png|390]]

### Dragon Defeat Effects

Create these effects:

#### Effect 1. Change the dragon's container state

Lets change the option of looting the dragon by changing the state of the container component of the red dragon:

- **Effect.name**: *Loot Dragon*
- **Effect.entity_target**: *Red Dragon*
- **Effect.effectType**: *ModifyProperty*
- **Effect.component**: *Container*
- **Effect.property**: *can_be_opened*
- **Effect.text_value**: 
	- **Value**: *true*
	- **Idx**: *0* or you can leave empty 

![[dragon_effect.png|390]]


#### Effect 2. Change the dragon's description text

As the dragon has been defeated, one of its description texts needs to be changed:

- **Effect.name**: *Defeated Dragon*
- **Effect.entity_target**: *Red Dragon*
- **Effect.effectType**: *ModifyProperty*
- **Effect.component**: *Reactabe*
- **Effect.property**: *description*
- **Effect.text_value**: 
	- **Value**: *Legends are still legends. This dead dragon was defeated but it will be remembered as the one that reigned the skies*
	- **Idx**: *1* 

The dragon has been defeated. How about we touch it now? To add a `new description text` we simply click on `add_text_value` and lets add:
- **Value**: *Its scales are almost impregnable. It's a miracle that this dragon has been defeated* 
- **Idx**: `2`

![[dragon_effect2.png|390]]

**Note**: If you try to `touch the dragon` before defeating it, you will get an `error text`. But after defeating it you can try doing so again and it will display the new `description_text`.


#### Effect 3. Change the dragon's heart reactable state

Lets change the display of the dragon's heart by changing its reactable component. This effect is placed on the **Red Dragon**:

- **Effect.name**: *Display Dragon Heart*
- **Effect.entity_target**: *Dragon Heart*
- **Effect.effectType**: *ModifyProperty*
- **Effect.component**: *Reactable*
- **Effect.property**: *is_visible*
- **Effect.text_value**: 
	- **Value**: *true*
	- **Idx**: *0* or you can leave empty 

![[dragon_effect3.png|390]]


#### Effect 4. Change the dragon's heart Inventory Item state

Lets change the ability of storing and taking out the dragon's heart by chaging the state of its inventory item component. This effect is placed on the **Red Dragon**:

- **Effect.name**: *Dragon Heart Interaction*
- **Effect.entity_target**: *Dragon Heart*
- **Effect.effectType**: *ModifyProperty*
- **Effect.component**: *InventoryItem*
- **Effect.property**: *can_be_picked_up*
- **Effect.text_value**: 
	- **Value**: *true*
	- **Idx**: *0* or you can leave empty 

![[dragon_effect4.png|390]]


### Action

The last step on the `Action System` is to unite the **Trigger, Condition/s and Effect/s**. Add an `Action` to the **Red Dragon**

Set:

- **Action.name**: *Defeat the Legend*
-  **Action.description**: *Using a special weapon, defeat the legend and obtain its most precious treasure*
- **Action.is_enabled**: *true*
- **Action.executor**: *Ebony Sword*
- **Action.triggers**:  

| Trigger Entity | Trigger Key |
| -------------- | ----------- |
| Ebony Sword    | Use Sword   |
- **Action.conditions**:  

| Condition Entity | Conditioni Key |
| ---------------- | -------------- |
| Ebony Sword      | Sword equipped |
| Red Dragon       | Dragon Alive   |
- **Action.effects**:  

| Effect Entity | Effect Key               |
| ------------- | ------------------------ |
| Red Dragon    | Defeated Dragon          |
| Red Dragon    | Loot Dragon              |
| Red Dragon    | Display Dragon Heart     |
| Red Dragon    | Dragon Heart Interaction |

![[dragon_action_elements.png|390]]

- **Action.failing_response**: 
	- *You can't defeat the dragon if:*
	- *You haven't equipped the ebony sword*
	- *Or*
	- *The dragon has already been defeated*
- **Action.success_response**:
	- The fight with the dragon is intense and long
	- As you evade a powerful flame, you drive your sword into the dragon's skull he collapses with a final roar. 
	- After catching your breath, it's time to reap the rewards

![[dragon_action_elements2.png|390]]


### Teaching Note

This is the central lesson of `Action System`. You should now  see that:

- the action lives on the target
- the triggering item is the executor and lives on the item that calls the action. On other words the `subject`.
- effects are responsible for visible world changes or add new description texts.


This same pattern can be reused for switches, doors, rituals, offerings, keys, and puzzle objects.


### Checkpoint

After publishing and testing:

- use the sword on the dragon should defeat it, allowing: 
	- the dragon can be checked and looted
	- the dragon can now be touched
	- the dragon heart should become visible 
	- the dragon heart can be picked up now.


### Next Step

The legend has been defeated and you now have the loot. It is time to return to the city and get some good rest. Let's build the action system for returning to the city at [[Lesson 7]].