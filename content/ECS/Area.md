# Area
## Purpose

The `Area` component marks an entity as a room/area in the world. It stores room-level state used by navigation and progression.

## Model

The `Area` Dojo model is composed by:

```
#[dojo::model]
pub struct Area {
    #[key]
    pub inst: felt252,
    pub is_area: bool,
    
    /// Properties ///
    /// If the area is a spawn point for players
    pub is_spawn_point: bool,
    
    /// progress percentage when entering this area
    pub progress_percentage: u8, // 0-100
    
    /// when entering, preserve original children (editors can add children to this area)
    pub preserve_children: bool,
}
```

### Variables Characteristics

- `inst`: Is the unique ID of the entity/object to whom the component is attached to.

- `is_spawn_point`: Indicates whether players start the game from this location.

- `progress_percentage`: Indicates the player progress in the story when reaching  location.
  
- `preserve_children`: Indicates whether editor/runtime logic should preserve room children.