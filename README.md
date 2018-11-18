I got alot of the information from [fuzziqersoftware](https://github.com/fuzziqersoftware/realmz_dasm). I have expanded on this and organized the definitions.

Filename | Contains
 ------ | ------ 
*scenario name* | Scenario metadata. Recomended levels, starting pos
Data BD | Battle data. Position of monster og battle start and what kind of monsters.
Data CI | Contact info.
Data CS | This seems to be the same as *scenario name* ??
Data Custom 1 BD | Custom land tileset definitions.
Data DD | Land action point codes
Data DDD | Dungeon action point codes
Data DES | Monster descriptions
Data DL | Dungeon levels
Data ED | Simple encounters
Data ED2 | [Complex encounters](#data-ed2)
Data ED3 | Extra action points
Data EDCD | Extra codes
Data LD | Level data (tile map)
Data MD | Monster data (including NPCs)
Data MD1 | Almost the same as MD, but some values are changed
Data MD-1 | Almost the same as MD, but some values are changed
Data MD2 | Map data (includes descriptions)
Data MENU | This file contains info used to construct the Beastiary Menu
Data NI | ??? Probably something to do with custom items. (200 * 100 bytes)
Data OD | Yes/no encounter (option) answer strings
Data Race | Custom race config
Data Caste | Custom caste config
Data RD | land map metadata incuding random rectangles
Data RDD | Dungeon random rectangles
Data SD | Shop data
Data SD2 | Strings
Data Solids | Solid special tiles.
Data TD | Treasure data
Data TD2 | [Rogue encounters](#data-td2)
Data TD3 | Time encounters
Global | Global macros
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
int16 | ???

One of the unknown is probably battle macro id.

# Data CI
18 x 256 bytes strings with information on the creater of the scenraio.

# Data Custom 1 BD
This has the same structure as the main tilset definitions in main data: Data <landname> BD.

Zero tile is not used, so we have 200 tiles.
 
bytes | value
---|---
Tile[201] | tiles
int16 | Base tile id

rest of file is unknown bytes

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
int16 | Forrest type
int16 | ???
int16 [9] | Battle expansion
int16 | ???

one of the unknown is "Indoor Tile Set"
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
Same format as LD, but transposed.
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
  int8 | Speak_result
  int8 [8] | actions_selected
  int16 [10] | Spell codes
  int8 [10] | Spell result codes
  int16 [5] | Item codes
  int8 [5] | Item result codes
  int8 | Can backout
  int8 | Has rogue encounter
  int8 | Maxtimes
  int16 | Rogue encounter id
  int8 | Rogue reset flag
  int8 | unknown
  int16 | prompt
  Text [8] | Action text
  Text [8] | Speak text
  
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

# Data LD

bytes | value
---|---
int16 [90][90] | Tile id

# Data MD
# Data MD1
# Data MD-1
# Data MD2
# Data MENU
# Data NI
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
int8 [20] | Unknown. Bool values. This rect only?
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

# Data TD2
bytes | value
---|---
int8 [8] | actions_available
int8 | trap_affects_rogue_only
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
