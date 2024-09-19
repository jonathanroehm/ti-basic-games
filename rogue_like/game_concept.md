# Roguelike TI-84 plus CE Game:
## Strategic Vision
A top down dunegeon crawler where you have one life to live. Defeat all the dungeons and take on the main boss.

* Procedural generation of
  * Dungeons
    * Layout
    * Enemy placement
  * Won loot
  * Witch Hut Potion Cost is randomly assigned within a band / range.

## The Game Story Overview
Our hero starts in a town, dungeon access is inside the town (aka: the overworld), via "wells". One can visit all the wells except the main boss dungeon.

You are our hero, here to save your town from encroaching evil. The main evil force are "shadow walkers". Shadow walkers look like people but are made of shadows. They are super powerful and are the main force to defeat. They control evil minions; re-animated dead (skeletons, rock monsters, zombies, poison spiky balls, etc).

## Game Structure

### Town
* Hero Progression
  * No Experience
  * Use Gold as Experience "curency"
    * Gold is collected upon exiting the dungeon (either via winning or exiting)

* Hero
  * Attributes:
     * Health: Hitpoints
     * Speed: How fast you can move around
     * Aura: Points allocated for special moves (currently: time travel)
     * Damage: How much damage you do per strike (base modifier)

* Shops
  * Alchemist: Upgrades base attributes
    * Compounding costs (more expensive the more you buy)
    * All attributes can be upgraded
  * Witch Hut: Temporary (one dungeon enter + exit cycle) buffs - format: potions
    * Increase specific attributes based on how much you're willing to pay
    * WIll be cheaper than going to the alchemist.
   
### Game Intro (first moments)
Player is guided to a specific dungeon that only exists at game start. Player is given a starting weapon (sharpened stick or something similar) and must complete the first dungeon to collect the starting weapon (sword or something).
* Starting Dungeon: "Warrior Trial"
  * Intro to the game
  * Little bit of story
  * Learn game mechanics
  * Don't die - impossible to die
  * Upon completion, see the actual game title screen.

After the warrior trial: Learn of worth of defeating the shadow walkers. Sent on your way 
* Game intro
* Tutorial for shops

### Dungeon Design
* Dungeon generation
  * Difficulty rating (easy, medium, hard)
    * Impacts: enemy count
    * Floor count
    * Loot Quality
    * Damage scale
    * Enemy Health
    * Traps: quantity, damage dealt, consequences.
  * Level / Floor of Dungeon
    * Entrance to the next floor down via stairs
    * Entrance to a nearby room via a door (same level).
    * Enemy death is non-permanent
      * Permanent death only occurs when the shadow walker is defeated
      * Enemy respawn upon re-entering the room
      * Every time you defeat an enemy you expand the gold (farming is possible)
  * Dungeon Boss
    * Each dungeon has a boss, that boss is the dungeon's "Shadow Walker"
    * Upon defeat, enemies are zeroed out in the dungeon
    * Gain access to dungeon loot
   
### Player System

#### Inventory Management
* Accessing inventory
  * Cannot access inventory inside dungeon
  * Can access in "overworld" / town
  * Equipables
    * Name
    * Stat modifiers
    * Equip / Exit option
* Won Loot
  * Will be able to see stats at a glance, when picked up, even if you can't equip it.

#### Gold Management
* Seeing gold
  * Gold count always available (e.g. built into UI)
  * Gold acts as spendable experience points
* How to use gold
  * Buy things at the shops / upgrade attributes at shop

#### Stats and Attributes
* Seeing your stats
  * When / Where
    * Health: always available (like gold)
    * All other stats are visible from inventory screen - accessible in the overworld

#### Maleffects
* Types
  * Poison
  * Fire
  * Etc...
  * Potential Durations:
    * Tick-based wear off over time
    * or: Until dungeon exit
 
### Enemy System

#### Enemy Attributes
* Hitpoints
* Damage
* Speed
* Potential to deliver maleffects

#### Enemy Maleffects
* Dungeon Permanent Maleffects (last until dungeon exit)
* Temporary Maleffects (tick based)

#### Enemy Intelligence / Aggro
* Enemies move on the screen
  * Movement Patterns are mostly random
* Aggro:
  * Within unspecified range: move towards you and begin combat when in melee range

### Bosses
TBD

### Super Awesome Amazing Game Hook: Time Travel
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
  * `Enter` to commit / execute
  * `Clear` to reset
  * `Mode` to exit (or something similar)

---

## Risky Code Bets
1. Aggro (Risk Level: 2/3)
  * monsters will sense you and come to you
3. Stats (Risk Level: 3/3)
   * Tracking stats and making them have an impact (more strength = more damage; attacking removes hit points)
4. Performant code (it's snappy and fun to play) (Risk Level: 2/3)
5. Time travel being fun and intuitive (Risk Level: 3/3)
6. Procedural generation (Risk Level 3/3)
  * Essence of a roguelike to us
  * Dungeons
    * Layout
    * Enemy placement
  * Won loot
7. System storage of items and loot tables that reliably recall item names, stats, and then can be applied to the player when equipped (Risk 2/3)
8. Tick-based maleffects / debuffs (things that wear off) (Risk level: 2/3)
