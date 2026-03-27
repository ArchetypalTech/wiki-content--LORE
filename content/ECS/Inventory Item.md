# Inventory Item

## Purpose

The `InventoryItem` component marks an entity as an item that can belong to a player, room, or container. It handles item-use command execution.

## Model

The `InventoryItem` Dojo model is composed by:

```
#[dojo::model]
pub struct InventoryItem {
    #[key]
    pub inst: felt252,
    pub is_inventory_item: bool,

    /// Properties ///
    /// The owner of the inventory item
    pub owner_id: felt252,

    /// If the inventory item can be picked up
    pub can_be_picked_up: bool,

    /// If the inventory item can go in a container
    pub can_go_in_container: bool,

    /// The quantity of the inventory item
    pub quantity: u32,

    /// Array of action maps for the inventory item
    pub action_map: Array<ActionMapInventoryItem>,

    /// If the inventory item has already been used
    pub already_used: bool,

    /// If the inventory item can be used multiple times
    pub multiple_use: bool,
}
```

### Variables Characteristics

- `inst`: Is the unique ID of the entity/object to whom the component is attached to.
- `is_inventory_item`: Indicates existence marker if the object is an inventory Item or not.

- `owner_id`: Indicates the current owning entity id (player, container, room/location).

- `can_be_picked_up`: Indicates whether the item is portable.

- `can_go_in_container`: Indicates whether the item can be stored.

- `quantity`: Indicates the  stack count. 

- `action_map`: Links verb-to-item-function mapping.

- `already_used`: Indicates if the item has already been used.

- `multiple_use`: Indicates whether repeated use is allowed.


```
pub struct ActionMapInventoryItem {
    /// The action verb
    pub action: ByteArray,

    /// The inst of the component that the action is attached to
    pub inst: felt252,

    ///  The types of actions
    pub action_fn: InventoryItemActions,
}

pub enum InventoryItemActions {
    #[default]
    UseItem,
    PickupItem,
    DropItem,
    PutItem,
    TakeOutItem,
}
```

- `action`: The verb that can be used to interact with the object.
  
- `inst`: The `inst` of the inventory item component.
  
- `action_fn`:  The type of action to be executed when interacting with the objec through the verb:
	- **UseItem**:  Use the item to trigger an action.
		- Example: *throw a rock to the window*
		  
	- **PickupItem**: Picks up an object and store it on the player personal inventory (container). 
		- Example: *pick up the ring*.
		  
	- **DropItem**: Drops an object and place it on the room/location. 
		- Example: *drop the ring*.
		  
	- **PutItem**: Put an object inside an specific container. 
		- Example: *put the sword inside the sheath*.
		  
	- **TakeItemOut**: Take an object from a specif container and place it in the room/location.
		- Example: *take the orb from the chest*.