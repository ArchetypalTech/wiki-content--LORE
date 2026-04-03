## Lesson 5. Create The Dragon And The Hidden Reward


## Dragon

Create `Dragon` under `Dragon Cave`.
![[dragon.png|390]]

Add:

- `Reactable`
- `DescriptionText`
- `Container`

Suggested values:

- `Entity.name`: *Red Dragon*
- `Entity.alt_names`: *dragon*
- `Container.can_be_opened`: *false*
- `Container.is_opne`: *false*
- `Container.num_of_slots`: *1*
- `Container.actions`:

| Action | Type  |
| ------ | ----- |
| open   | Open  |
| close  | Close |
| check  | Check |
- `Description 0`: *a great red DRAGON*
- `Description 1`: *There is no words to describe this legendary creature. Your only advantage is that its sleeping*
- `Reactable.new_entry`: *a great read DRAGON*
- `Reactable.actions:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |

## Dragon Heart

Now create `Dragon Heart` under `Dragon`.


Add:

- `InventoryItem`
- `Reactable`
- `DescriptionText`

Set:

- `Entity.name`: * Dragon Hear* 
- `Entity.alt_names`:  *heart*
- `InventoryItem.can_be_picked_up`: *false*
- `InventoryItem.owner_id`: *Red Dragon*
- `InventoryItem.multiple_use`: *True*
- `InventoryItem.actions`:

| Action | Type        |
| ------ | ----------- |
| pick   | PickupItem  |
| drop   | DropItem    |
| put    | PutItem     |
| take   | TakeItemOut |
| use    | UseItem     |

- `Reactable.is_visible = false`
- `Description 0`: *a dragon HEART*
- `Description 1`: *The heart of a legenday creature. You can feel the overwhelming mana from it. It can be used for many things.*
- `Reactable.new_entry`: *a dragon HEART*
- `Reactable.actions:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |

  
### Teaching Note

This is the setup for a classic reveal pattern:


- an obstacle is visible at first
- a reward exists in the world already
- the reward is hidden until another interaction changes state

  
### Checkpoint

The dragon should be visible in the cave. The dragon heart should exist in the cave but remain hidden and cannot be stolen, picked, taken, or interacted with.

### Next Step

Locations? ready! Weapon? ready! Enemy? ready! Next? Let's build the action system for confronting the dragon at [[Lesson 6]].
