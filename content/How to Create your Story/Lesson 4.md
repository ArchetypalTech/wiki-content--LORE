## Lesson 4. The Player And Starting Sword


## Player 

As you know, in order to have access to the editor you need to **Crossroads** in **O'RUGGIN**. So obviously, you will be playinig with the `PLAYER / CHARACTER` that you have there. 

Now, LORE allows you to transition from one story to another through **`hubs`**. So basically you don't need to create a new `PLAYER` entity for your story as you will be able to continue to play with existing one.

## Sword

Create the `Sword` under `Mountain Pass`.


![[ebony sword.png|390]]

Add:

- `InventoryItem`
- `Reactable`
- `DescriptionText`

Suggested values:

- `Entity.name`: *Ebony Sword* 
- `Entity.alt_names`:  *sword*
- `InventoryItem.can_be_picked_up`: *true*
- `InventoryItem.owner_id`: *Mountain Pass*
- `InventoryItem.multiple_use`: *True*
- `InventoryItem.actions`:

| Action | Type        |
| ------ | ----------- |
| pick   | PickupItem  |
| drop   | DropItem    |
| put    | PutItem     |
| take   | TakeItemOut |
| use    | UseItem     |

![[sword_invItem.png|390]]

- `Description 0`: *an ebony SWORD*
- `Description 1`: *A deep dark two handed sword. A cracked ruby sits on its handle and you can feel a great power from it*
- `Reactable.new_entry`: *an ebony SWORD*
- `Reactable.actions:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |


### Teaching Note

This step teaches two things:

- a carried item is still a normal entity with components
- where an item is located is represented by hierarchy, not only by a property field

As you will be *"bringing* your player from **O'RUGGIN** you will have to `**pick**` the sword and not `**put**` it in the `bag`.


### Checkpoint

You should now understand that inventory is represented through `InventoryItem` plus parent-child placement.

### Next Step

Now with the weapon ready, it is time to create our enemy at [[Lesson 5]].
