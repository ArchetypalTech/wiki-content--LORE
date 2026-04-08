# Lesson 1.  Creating your Trail and the Three Rooms

Let's embark on the journey on how to create a small text adventure.

## Trail Creation

After having **gained access** to the editor and login in, what you want to do is to create your `trail`; your own story. For that click on `Create Trail`.

![[create_trail_button.png]]

This will create a trail section where you will be able to add the content. Feel free to create as many trails you want but we recommend to do one at the time.


### Trail set up

By default, your trail comes already with some components and some of their variables can be changed at your discretion.


#### Entity

The object that represents your story. Most of the variables are locked such as the `inst`, `trail_id` and `creator_address`. For this lesson we are going to change the name:

![[trail_entity.png|308]]

Inside `alt_names` you can introduce alternative names for your story. You can have as much as you want but keep it in mind that it only accepts one word words like `testing` and not `testing game`. 


#### Reactable

This component will allow to add the output when interacting with your trail object. We can use this to give it a description.

![[trail_reactable.png|298]]  ![[trail_desctext.png|349]]

Feel free to  add more description texts if you want. Also you can change the `Actions` to link the verb to the text you want to show.  In this case we changed `look` to return randomly between keys `0` and `1`.


#### Trail

The trail component allows to link your story to any object in the LORE universe that has a `Hub` component on any story. You can indicate to which one you want to connect to. For this guide we chose the `Crossroads` from `O'RUGGIN`.

![[trail_trail.png]]

With the trail connected we can now start to create the locations for our story.


## Locations creation

Create three entities:

1. Mountain Pass
2. Dragon Cave
3. City Plaza

![[locations.png]]

For each entity, add:

- Area
- Reactable
- Two DescriptionText
- Modify the `new entry` from the `reactable` as well the `actions_map`

Suggested setup:


### Mountain Pass

- **Entity.name**: Mountain Pass
- **Entity.alt_names**: *mountain*, *pass* 
- **Area.is_spawn_point**:  *false*
- **Area.progress_percentage**: *0*

![[mountain_ent_area.png|390]]

- **Description 0**:  *You stand high in MOUNTAIN PASS. A dormant teleport shrine rests nearby, and a cave entrance opens to the north. You can see:* 
- **Description 1**: *As you walk towards the edge of the pass, the wind starts howling. The views are amazing but the cold is starting to get you.* 
- **Reactable.new_entry**: *You stand high in MOUNTAIN PASS. You can see:*
- **Reactable.actions**:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |

![[mountain_react_desctxt.png|390]]


### Dragon Cave

- **Entity.name**: Dragon Cave
- **Entity.alt_names**: *cave* 
- **Area.is_spawn_point**:  *false*
- **Area.progress_percentage**: *50*

![[cave_ent_area.png|390]]

- **Description 0**:  *The cave is hot and smoky. You can feel a terrifying energy deeper within the darkness. You can see:* 
- **Description 1**: *You light your torch for a brief moment and what you see are only the rests of previous adventurers. You ask yourself if you will end like them or not before turning off your torch* 
- **Reactable.new_entry**: *An endless darkness within the cave. You can see:*
- **Reactable.actions**:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |

![[cave_react_desctxt.png|390]]


### City Plaza

- **Entity.name**: City Plaza
- **Entity.alt_names**: *plaza* 
- **Area.is_spawn_point**:  *false*
- **Area.progress_percentage**: *100*

![[plaza_ent_area.png|390]]

- **Description 0**:  *The city PLAZA. It's busting with people of different races. The water fountain, the cathedral, the guild building have a lot of traffic as always. Its good to be here. You can see:* 
- **Description 1`**: *The weather today is comfortable. A nice sunny day but not hot, the smell of the fresh bread and other products entice you. Many adventurers go around, somo solo others in parties* 
- **Reactable.new_entry**: *The city PLAZA is busiest as ever with people of different races. You can see:*
- **Reactable.actions:

| Action  | Type                    | Idx 1 | Idx 2 |
| ------- | ----------------------- | ----- | ----- |
| look    | ReadSpecificDescription | 0     | 0     |
| examine | ReadSpecificDescription | 1     | 1     |
| check   | ReadSpecificDescription | 1     | 1     |


![[plaza_react_desctxt.png|390]]


### Teaching Note
  
This is the basic room pattern in LORE:

- `Area` makes it a playable space
- `Reactable` makes it describable
- `DescriptionText` provides authored text

  
### Checkpoint

At this point, you should understand that rooms are regular entities with room-specific capabilities added by components.


### Next Step

Now that you have created the trail and the locations, lets connect them at [[Lesson 2]].
