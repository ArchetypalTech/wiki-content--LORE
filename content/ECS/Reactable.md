# Reactable

A`Reactable` component is the presentation/interactions layer for many world objects. It stays decoupled from the actual text storage, which is why authoring can add or remove descriptions independently.

## Purpose

The `Reactable` component gives an entity inspect/read-style interactions. It connects command verbs to text output or visibility changes.

## Model

The `Reactable` Dojo model is composed by:

```
#[dojo::model]
pub struct Reactable {
    #[key]
    pub inst: felt252,
    pub is_reactable: bool,

    /// Properties ///
    /// If the reactable is visible
    pub is_visible: bool,

    /// Array of descriptions for the reactable
    pub description: Array<u32>,

    /// Array of action maps for the reactable
    pub action_map: Array<ActionMapReactable>,

    /// For the first description, if we want to show a different one
    pub already_shown: bool,

    /// New first description
    pub new_entry: ByteArray,
}
```

### Variables Characteristics

- `inst`: Is the unique ID of the entity/object to whom the component is attached to.
-  `is_reactable`:  Indicates the existence marker.

- `is_visible`: Indicates whether the object should currently be visible when checking the location context.

- `description`: An array that stores the `key` variable of [[Description Text]]  component from which the corresponding descriptions texts can be linked  through the `action_map`.

- `already_shown`: Is the state flag for first-time text behavior and if true then display the `new_entry`.

- `new_entry`: Stores the replacement text in case the first`description` has already been show.
  
- `action_map`: Links the verb-to-reactable-function mapping.

```
pub struct ActionMapReactable {
    /// The action verb
    pub action: ByteArray,

    /// The inst of the component that the action is attached to
    pub inst: felt252,

    ///  The types of actions
    pub action_fn: ReactableActions,

    /// The entrypoint to match the action with the description index
    pub entrypoints: (u32, u32),
}

pub enum ReactableActions {
    #[default]
    SetVisible,
    ReadRandomDescription,
    ReadFirstDescription,
    ReadSpecificDescription,
}
```

- `action`: The verb that can be used to interact with the object.
  
- `inst`: The `inst` of the exit component.
  
- `action_fn`:  The type of action to be executed when interacting with the objec through the verb.
  
	- **SetVisible**: Toggles the boolean value that indicates if the object is `is_visible` when checking the context of the location. 
		- Example: *hide the gem*.
		  
	- **ReadRandomDescription**: Returns a random description text using the range values from `entrypoints` against the key values stored inside the `description` variable . 
		- Example: *talk to the driver*.
		  
	- **ReadFirstDescritpion**: Returns the first description text. 
		- Example: *read the news*.
		  
	- **ReadSpecificDescrition**: Returns an specific description text specified in the `entrypoints` variable. 
		- Example: *inspect the bag*.
		  
- `entrypoints`: stores the unique ID key of the description/s text/s that is desired to link the verb-action with.