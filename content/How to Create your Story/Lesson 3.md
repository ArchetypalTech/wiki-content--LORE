# Lesson 3. Create The Teleport Shrine

## Teleport Shrine

Create `Teleport Shrine` under **Mountain Pass**.

![[teleport_location.png]]

Add:

- Exit
- Reactable
- DescriptionText

Set:

- **Exit.is_enterable**: *false*
- **Exit.leads_to**: *City Plaza*
- **Exit.direction**: *Down*

![[teleport_exit.png|390]]

- **Description 0**: *a TELEPORT shrine*
- **Description 1**: *A ring of ancient stone surrounds a sleeping teleport gate. A hollow socket is at its center*
- **Reactable.actions**:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |


### Teaching Note

The teleport is authored as an exit that exists before it becomes usable. This is a useful lesson:

- visibility and existence are not the same as usability
- a destination can exist while access remains gated 


### Checkpoint

You should now see the teleport shrine in the mountains but should not be able to use it yet.


### Next Step

With the connection between locations you can now travel between them. Now lets focus on the Player and the Sword at [[Lesson 4]].

