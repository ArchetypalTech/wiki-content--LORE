## Lesson 4. Create The Player And Starting Sword

  
Use `New Player` while `Mountain Pass` is the spawn area.
  
Then create a child entity under the player called `Sword`.
  

Add:

- `InventoryItem`
- `Reactable`
- `DescriptionText`

Suggested values:


- `Entity.alt_names = sword, blade`
- `InventoryItem.can_be_picked_up = true`
- `InventoryItem.owner_id = Player`
- `InventoryItem.multiple_use = true`
- description:

  `A worn but reliable sword.`


### Teaching Note


This step teaches two things:


- a carried item is still a normal entity with components
- where an item is located is represented by hierarchy, not only by a property field


Because the sword is a child of the player, it begins in the player's possession.


### Checkpoint

You should now understand that inventory is represented through `InventoryItem` plus parent-child placement.