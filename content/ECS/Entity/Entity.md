
# Entity

## What is an Entity?

An entity represents an specific object. It possess an unique ID that will be reused by the components that forms it (like an exit component. Therefore, is the foundation of the ECS architecture.

![[object_entity_component.png]]
## Model

The `Entity` Dojo model, as mentioned previously; is the foundation of the ECS architecture. It's composed by:

```
#[dojo::model]
pub struct Entity {
    #[key]
    pub inst: felt252,
    pub is_entity: bool,

    /// Properties ///
    /// the trail this Entity belongs to, or MAIN_TRAIL_ID (zero)
    pub trail_id: u128,

    /// Name of the entity
    pub name: ByteArray,

    /// Creator
    pub creator_address: ContractAddress,

    /// Alternative names of the entity
    pub alt_names: Array<ByteArray>,

    /// Holds the keys of the actions that are attached to this entity
    pub actions_keys: Array<felt252>,

}
```
## Variables Characteristics

- `inst`: Is the unique ID of the entity that will serve for indetification and interaction of it at the contract side (backend). Every component attached to this object reuses this same key.
  
- `trail_id`: Indicates to which trail the object belongs to. If it is the main trail (original one) will be ZERO.
  
- `name`: The name of the object in the world.
  
- `alt_names`: The alternative names of the object that will be used for interacting with it.
  
- `creator_address`: The public address that belongs to the person that created the object.
  
- `actions_keys`: The array of the actions keys  that links the object to action records that can be triggered after interactions.

## Attachable Components

Currrently O'RuggEd provides the following components that can be added to the entity/object:

- [[Area]]
- [[Reactable]]
- [[Description Text]]
- [[Container]]
- [[Inventory Item]]
- [[Exit]]
- rest of components


With these components some non-modifiable systems are automatically created but players can modify others such as:

- Action System
- Trail System
