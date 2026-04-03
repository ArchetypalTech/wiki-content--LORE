## Lesson 2. Connect The Mountain And The Cave

Create two exit entities for allowing movement between locations.  


### Cave Entrance 

Create `Cave Entrance` under  `Mountain Pass`.
![[cave_entrance.png|390]]  

Add:

- `Exit`
- `Reactable`
- `DescriptionText`

Set:

- `Entity.name`: *Cave Entrance*
- `Entity.alt_names`: *cave*
- `Exit.leads_to`: *Dragon Cave*
- `Exit.is_enterable`: *true*
- `Exit.direction_type`: *North*

![[cave_entr_exit.png|390]]

- `Reactable.new_entry`: *a CAVE entrance*
- `Description 0`: *a CAVE entrance*
- `Description 1`: *the size of it is enormous. The color of the rock is mixture of black and blue. Fire marks can be seen on the rock.*
- `Reactable.actions:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |


### Mountain Path

Create `Mountain Path` under `Dragon Cave`.
![[mountain_path.png|390]]

Add:
  
- `Exit`
- `Reactable`
- `DescriptionText`

Set:

- `Entity.name`: *Mountain PATH*
- `Entity.alt_names`: *path*
- `Exit.leads_to`: *Mountain Pass*
- `Exit.is_enterable`: *true*
- `Exit.direction_type`: *South*

![[path_exit.png|390]]

- `Reactable.new_entry`: *a  mountain PAHT*
- `Description 0`: *a mountain PATH*
- `Description 1`: *the path that leads back to the Mountain Pass from the Dragon Cave. Rests of bones, weapons and armors can be seen along the way*
- `Reactable.actions:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |


### Teaching Note

This teaches that movement is not built into the room itself. It is authored as separate exit entities that point from one area to another.


### Checkpoint

You should now be able to move between two spaces using authored exits.

### Next Step

Now that you connected the Mountain Pass and the Dragon Cave, lets prepare the connection to the City Plaza at  [[Lesson 3]].


  


  

