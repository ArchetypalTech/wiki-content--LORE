## Lesson 2. Connect The Mountain And The Cave

Create two exit entities for allowing movement between locations.  


### Cave Entrance 

Create `Cave Entrance` under  `Mountain Pass`.
  
Add:

- `Exit`
- `Reactable`

Set:

- `Entity.name`: *Cave Entrance*
- `Entity.alt_names`: *entrance*
- `Exit.leads_to`: *Dragon Cave*
- `Exit.is_enterable`: *true*
- `Exit.direction_type`: *North*
- `Reactable.new_entry`: *a cave ENTRANCE*
- `Description 0`: *a cave ENTRANCE*
- `Description 1`: *the size of it is enormous. The color of the rock is mixture of black and blue. Fire marks can be seen on the rock.*


### Mountain Path

Create `Mountain Path` under `Dragon Cave`.

Add:
  
- `Exit`
- `Reactable`

Set:

- `Entity.name`: *Mountain PATH*
- `Entity.alt_names`: *path*
- `Exit.leads_to`: *Mountain Pass*
- `Exit.is_enterable`: *true*
- `Exit.direction_type`: *South*
- `Reactable.new_entry`: *a  mountain PAHT*
- `Description 0`: *a mountain PATH*
- `Description 1`: *the path that leads back to the Mountain Pass from the Dragon Cave. Rests of bones, weapons and armors can be seen along the way*


### Teaching Note

This teaches that movement is not built into the room itself. It is authored as separate exit entities that point from one area to another.


### Checkpoint

You should now be able to move between two spaces using authored exits.

  


  

