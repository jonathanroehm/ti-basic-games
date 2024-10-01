## Super Awesome Amazing Game Hook: Time Travel
* You can stop time enyware
* Unsure but interested in exploring:
  * Upgrading Time Travel Abilities:
  * Having more points to use
  * Having new abilities to apply (e.g. back stab)
* Pts
  * start with 3 pts / low points
  * spend a point to make a move

* Execution of time travel plan:
  * Press a button (maybe Enter) to begin time travel mode / stops time
  * Draft out your sequence
  * Sequence is shown to player (eg move move attack attack)
  * Enter to commit / execute
  * Clear to reset
  * Mode to exit (or something similar)
 
---

## What's risky about time travel:
"Does it work?"
"Is it fun?"

**Strategy: Make a sample program**

**Questions we want to answer:**
* Is time travel code performant?
* Will aura point spending work
* Does it feel fun and cool?
* Can we utilize a draft movement plan and then have the game execute it on our behalf.

**Test Concept:**
1. One screen, player spawns and enemy spawns
2. Enemy does move (enemy has hitpoints and can be killed)- at death, restart test.
4. Tick System
5. Aura - 5 points
6. Map boundary (very simple map)
7. Show draft movement plan while time traveling
8. Abilities: dash (aka: jump), slash (standard attack)

---

## Test Concept

### Loop Structure
Movement -> Time Travel Planning -> Time Travel Execution 

Movement Loop:
* You move
* mobs moves
* tick increment
* check for player inputs

Time Travel Planning Loop:
* mobs stop
* enter planning
* actions take aura
* show TT plan
* cmommit, reset or exit

Time Travel Execution Process
* execute plan (animated)
  * see the planned movements occur
  * see aura spent on a per point basis
  * if attacking, damage done is shown

```
Room Loop

  Start Movement Loop
    Enemy and player are moving
  End Movement Loop
  
  Start Time Travel Planning Loop
    Enemy stops
    Player drafts TT plan
  End Time Travel Planning Loop
  
  Start Time Travel Execution Process
    TT plan is executed
  End Time Travel Execution Process

  (Restart room loop at "Start Movement Loop")
End Room Loop
```

#### Movement Loop
```
Room Loop (Main Loop)

* Movement Loop
** Tick Increments
** Player Movement
*** Check for [<] [^] [>] [v] and [Enter] (time travel)
*** D-pad movements move character
    Character can't move through walls or mobs.
*** [Enter] Ends Movement Loop, Begins Time Travel Planning Loop 

** Mob Movement
*** When movement tick happens (5th tick?)
**** Move in random (up,down,left,right) direction one cell
     Mob can't move through character or walls.
```

#### Time Travel Planning Loop
Sent to time travel loop after pressing `[Enter]` in movement loop
**Starting Aura Points: 10 for test**
Data to track: 
* Aura point usage
* Movements made (movement tracker)

```
Time Travel Planning Loop
Changes: Mobs stop moving, ticks pause, player movement now uses aura points
* Movements & Abilities
** Walking (1 cell) - up, down, left, right
*** "TT Ghost" moves to new location
*** 1 Aura point subtracted
*** Move is added to move tracker
*** update aura tracker

** Dash (2 cells) - Alpha + up, down, left, right
*** "TT Ghost" Moves 2 cells, can hop over traps
**** Can go through mobs to end up behind them, but not through walls.
*** 2 Aura point subtracted
*** Move is added to move tracker
*** Upate aura tracker

# do not calculate damage in planning stage
** Slash (standard attack)
*** Attack 1 sq in front - no modifiers for position
*** 2 aura points subtracted
*** Move is added to move tracker
*** update aura tracker


# Note: stab performed from behind the mob
# results in an instant-kill
# stabs performed from anywhere besides behind: normal stab
** Stab (back stab, normal stab)
*** 4 aura subtracted
*** Move is added to move tracker
*** Update aura tracker
```

#### Time Travel Execution Loop
Data Available:
* Movement Tracker
* Aura

```
# Goals: execute on the move tracker
# Do damage when attacking
# Want the world to absorb the changes made during time travel
#   when time travel is over

* Read the movement tracker
** Execute each movement in the tracker
*** If movement (not attack)
**** Go from original Y,X position to new Y,X position
**** Subtract Aura points for real
*** If attack
**** Is it a position based attack (e.g. backstab)?
**** if it is a position based attack:
***** check for position modifier
***** Do damage based on true/false position-modifier modifier (e.g insta-kill)
**** if not a position based attack
***** do damage

* Mob response
** when receiving damage:
*** subtract damage done from hitpoints
*** if hitpoints ≤ 0
**** death
*** if hitpoints > 0
**** show damage done
```

