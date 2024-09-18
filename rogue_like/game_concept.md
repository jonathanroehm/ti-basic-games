# Roguelike TI-84 plus CE Game:
## Strategic Vision
A top down dunegeon crawler where you have one life to live. Defeat all the dungeons and take on the main boss.

* Procedural generation of
  * Maps
  * Dungeons
    * Layout
    * Enemy placement
  * Won loot

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
 
