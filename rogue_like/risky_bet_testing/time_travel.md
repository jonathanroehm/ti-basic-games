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
