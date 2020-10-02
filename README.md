I got alot of the information from [fuzziqersoftware](https://github.com/fuzziqersoftware/realmz_dasm). I have expanded on this and organized the definitions.

Filename | Contains
 ------ | ------ 
*scenario name* | Scenario metadata. Recomended levels, starting pos
Data BD | [Battle data](#data-bd). Position of monster og battle start and what kind of monsters.
Data CI | [Contact info](#data-ci)
Data CS | This seems to be the same as *scenario name* ??
Data Custom 1 BD | Custom land tileset definitions.
Data DD | [Land action point codes](#data-dd)
Data DDD | [Dungeon action point codes](#data-ddd)
Data DES | Monster descriptions
Data DL | Dungeon levels
Data ED | Simple encounters
Data ED2 | [Complex encounters](#data-ed2)
Data ED3 | Extra action points
Data EDCD | Extra codes
Data ID | Standard items
Data LD | [Level data (tile map)](#data-ld)
Data MD | [Monster data (including NPCs) - normal monsters](#Data-MD)
Data MD1 | Monster data - monster monsters
Data MD-1 | Monster data - mega monsters
Data MD2 | Map data (includes descriptions)
Data MENU | This file contains info used to construct the Beastiary Menu
Data NI | Custom items. (200 * 100 bytes)
Data OD | Yes/no encounter (option) answer strings
Data Race | Custom race config
Data Caste | Custom caste config
Data RD | land map metadata incuding random rectangles
Data RDD | Dungeon random rectangles
Data S | Spell data
Data SD | [Shop data](#data-sd)
Data SD2 | [Strings](#data-sd2)
Data Solids | Solid special tiles.
Data TD | Treasure data
Data TD2 | [Rogue encounters](#data-td2)
Data TD3 | Time encounters
Global | Global macros
Layout | Land layout
Scenario | ???
Scenario.rsf | Resources (images, sounds, etc.)

### All values in the files are big endian

# *scenario name*
 
bytes | value
---|---
int32 | Recomended starting level
int32 | ??
int32 | Start level
int32 | Start X
int32 | Start Y

Rest of file is unknown bytes

# Data BD
File contains 256 battles
#### Battle
346 bytes

bytes | value
---|---
int16[169] | Position of monster in 13x13 grid.
byte | Distance from party
byte | ???
int16 | Before battle string id
int16 | After battle string id (Displayed when collecting treasure)
int16 | Battle macro id

# Data CI
18 x 256 bytes strings with information on the creater of the scenraio.

# Data Custom 1 BD
This has the same structure as the main tilset definitions in main data: Data <landname> BD.

Zero tile is not used, so we have 200 tiles.
 
bytes | value
---|---
Tile[201] | tiles
int16 | Base tile id
int16 | Indoor tileset
int16 | Mountains low id - used for random tiles
int16 | Mountains high id
int16 | ???
int16 | Open ground low id
int16 | Open ground high id
int16 | ???
int16 | Rubble low id
int16 | Rubble high id
int16 | ???
int16 | Houses low id
int16 | Houses high id
int16[19] | ???

**Tile**

bytes | value
---|---
int16 | Sound id
int16 | Time per move
int16 | Solid type
int16 | Is shore
int16 | Is / need boat
int16 | Is path
int16 | Blocks line of sight
int16 | Need fly / float
int16 | Forest type
int16 | ???
int16 [9] | Battle expansion
int16 | ???

# Data DD

bytes | value
---|---
int32 | Location code
int8 | To level id
int8 | To X
int8 | To Y
int8 | Percent chance
int16 [8] | Command codes
int16 [8] | Argument codes

**Parse location code**
X = Location code % 100
Y = (Location code / 100) % 100
Level id = (Location code / 10000) % 100;

# Data DDD
Same format as DD

# Data DES

bytes | value
---|---
int8 | String length
int8 [255] | text

# Data DL

bytes | value
---|---
int16 [90][90] | Tile (reads across, then down)

**Dungeon tile**

bit | meaning
---|---
0x0001 | wall
0x0002 | door (horizontal)
0x0004 | door (vertical)
0x0008 | stairs
0x0010 | columns
0x0080 | unmapped
0x0100 | can move up
0x0200 | can move right
0x0400 | can move down
0x0800 | can move left
0x1000 | has AP
0x2000 | archway
0x4000 | no wall in battle

# Data ED

bytes | value
---|---
int8 [4][8] | Choice codes
int16 [4][8] | Choice args
int8 [4] | Choice result index
int8 | Can backout
int8 | Max times
int16 | unknown
int16 | Prompt
Text[4] | Option texts

**Text**

bytes | value
---|---
int8 | String length
int8 [79] | Text

# Data ED2
bytes | value
---|---
  int8 [4][8] | Choice codes
  int16 [4][8] | Choice args
  int8 | Action result
  int8 | Speak result
  int8 [8] | actions selected
  int16 [10] | Spell codes
  int8 [10] | Spell result codes
  int16 [5] | Item codes
  int8 [5] | Item result codes
  int8 | Can backout
  int8 | Has rogue encounter
  int8 | Max times
  int16 | Rogue encounter id
  int8 | Rogue reset flag
  int8 | unknown
  int16 | prompt
  Text [8] | Action text
  Text | Speak text
  
  **Text**

bytes | value
---|---
int8 | String length
int8 [39] | Text

# Data ED3
Same format as DD

# Data EDCD

bytes | value
---|---
int16 [5] | Codes

# Data ID
Same format as Data NI

# Data LD

bytes | value
---|---
int16 [90][90] | Tile id (reads down, then across)

Negative values indicate a sprite (building etc.) on plain open ground. Increase value by 1000 for AP, 3000 for secret AP.

# Data MD
bytes | value
---|---
int8 | Monster level
int8 | Stamina
int8 | Agility
int8 | Monster number
int8 | Movement
int8 | Armor rating
int8 | Magic resist
int8 | Weapon required to hit
int8 | Team
int8 | Size
int8[8] | Traits
int8 | Number of attacks
int8 | Number of magical attacks
int8[5][4] | Attack data
int8 | Attack plus
int8 | Spell chance
int8 | Run health
int8 | Surrender health
int8 | Missile chance
int8 | Summonable
int8[6] | Damage resistances
int8[6] | Damage immunities
int16 | gold
int16 | gems
int16 | jewelry
int16[10] | Known spells
int16[6] | Carried items
int16 | Equipped weapon
int16 | Icon
int16 | Spell points
int16 | Experience bonus
int8[14] | ???
int8 | Not in bestiary menu
int8[2] | ???
int8 | Magic plus needed
int8[40] | Statuses
int8[4] | ???
int16 | Death macro
int8[2] | ???
int8[40] | Name

 **Attacks**

 bytes | value
 ---|---
 int8 | min damage
 int8 | max damage
 int8 | attack form
 int8 | special attack

# Data MD1
Same format as Data MD

# Data MD-1
Same format as Data MD

# Data MD2

bytes | value
---|---
Icon[10] | Drawn icons
int16 | X position of top-left corner
int16 | Y position of top-left corner
int16 | land level
int16 | picture
int16 | tile size
int16 | text
int16 | dungeon level
int16 | ?
int16[4] | picture top, left, bottom, right
int8 | description length
int8[255] | description text

 **Icon**
 
 bytes | value
 ---|---
 int16 | icon ID
 int16 | X position
 int16 | Y position
 
# Data MENU

# Data NI

bytes | value
---|---
int16 | Strength bonus
int16 | ID
int16 | Icon
int16 | Item type
int16 | Bladed or blunt weapon
int16 | Number of hands
int16 | Luck bonus
int16 | Movement bonus
int16 | Armor rating
int16 | Magic resist
int16 | Magic plus
int16 | Spell points
int16 | Sound
int16 | Weight
int16 | Cost
int16 | Charges
int16 | Cursed item appearance
int16 | Is magical
int64 | Category
int32 | Not useable by
int16 | Race specific
int16 | Caste specific
int32 | Useable only by
int16[7] | ???
int16 | Damage
int16 | Damage vs large (no longer used)
int16 | Heat damage
int16 | Cold damage
int16 | Electric damage
int16 | Damage vs undead
int16 | Damage vs demons
int16 | Damage vs evil
int16 | Special 1
int16 | Special 2
int16 | Special 3
int16 | Special 4
int16 | Special 5

# Data OD

bytes | value
---|---
int8 | String length
int8 [24] | text

# Data Race
# Data Caste
# Data RD

bytes | value
---|---
RandomRectCoords [20] | Random rectangles coords
int16 [20] | TimesIn10k
RandomRectBattleRange [20] | BattleRange
int16 [20][3] |  XapNum
int16 [20][3] | XapChance
int8 | LandType
int8 | Dark
int8 | LOS (line of sight)
int8 [20] | This rect only
int8 [20] | PercentOption
int8 | unused;
int16 [20] | sound
int16 [20] | text

**RandomRectBattleRange**

bytes | value
---|---
int16 | Low
int16 | High

**RandomRectCoords**

bytes | value
---|---
int16 | Top
int16 | Left
int16 | Buttom
int16 | Right

**LandType**

0,  "outdoor"\
1,  "reserved1"\
2,  "reserved2"\
3,  "cave"\
4,  "indoor"\
5,  "desert"\
6,  "custom_1"\
7,  "custom_2"\
8,  "custom_3"\
9,  "abyss"\
10, "snow"

# Data RDD
Same format as Data RD

# Data SD
File contains 21 shops. Zero shop is not used. So we have 20 shops.

**Shop**

bytes | value
---|---
int16 [1000] | Item id per group. 5 groups x 200 items.
int8 [1000] | Item inventory count. 
int16 | Inflation (% of normal item price)

# Data SD2

bytes | value
---|---
int8 | String length
int8 [255] | text

# Data TD
bytes | value
---|---
int16[20] | Item id
int16 | experience
int16 | gold
int16 | gems
int16 | jewelry

# Data TD2
bytes | value
---|---
int8 [8] | Actions available
int8 | Trap affects rogue only
int8 | is_trapped
int8 [8] | percent_modify
int8 [8] | success_result_codes
int8 [8] | failure_result_codes
int16 [8] | success_string_ids
int16 [8] | failure_string_ids
int16 [8] | success_sound_ids
int16 [8] | failure_sound_ids
int16 | trap_spell
int16 | trap_damage_low
int16 | trap_damage_high
int16 | num_lock_tumblers
int16 | prompt_string
int16 | trap_sound
int16 | trap_spell_power_level
int16 | prompt_sound
int16 | percent_per_level_to_open
int16 | percent_per_level_to_disable

# Data TD3
bytes | value
---|---
int16 | Day
int16 | Increment
int16 | Chance
int16 | X-AP
int16 | Land level required
int16 | Random rectangle required
int16 | X location
int16 | Y location
int16 | Item required
int16 | Quest required
int16 | Land/dungeon
int16[9] | ???

# Layout
bytes | value
---|---
int16[16][8] | Land id

Uses -1 for land 0
