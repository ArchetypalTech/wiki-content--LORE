# Description Text

The ECS model allows us to separate `this object is reactable` from `these are the text snippets it can show` therefore, the amount of texts that an object can have won't be limited.
## Purpose

The `Description Text` component stores the text content entries attached to an entity. This approach allows to supports multiple description records per entity.

## Model

The `DescriptionText` Dojo model is composed by:

```
#[dojo::model]
pub struct DescriptionText {
    /// Unique identifier from the Entity it is attached to
    #[key]
    pub inst: felt252,

    /// Unique identifier of the description
    #[key]
    pub key: u32,

    /// Description text
    pub text: ByteArray,
}
```

### Variables Characteristics

- `inst`: Is the unique ID of the entity/object to whom the component is attached to.

- `key`: Is the per-entity description id/key. Value is stored inside the [Reactable's `description`](Reactable.md#variables-characteristics) variable

- `text`: Stores the actual content.