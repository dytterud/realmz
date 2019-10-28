# Data Race
30 races of 408 bytes

bytes | value
---|---
short[8] | + / - to hit
short | Sneak attack
short | Hide in shadows (unused)
short | Resurrect (unused)
short | Cause major wound
short | Detect secret area
short | Acrobatic act
short | Detect trap
short | Disarm trap
short | Hear noise (unused)
short | Force lock
short | Move silently (unused)
short | Pick lock
short | Read scroll (unused)
short | Turn undead
short | Vs. Charm
short | Vs. Heat
short | Vs. Cold
short | Vs. Electrical
short | Vs. Chemical
short | Vs. Mental
short | Vs. Magical
short | Vs. Special?
short | Attr bonus Brawn
short | Attr bonus Knowledge
short | Attr bonus Judgement
short | Attr bonus Agility
short | Attr bonus Vitality
short | Attr bonus Luck
short | Brawn from
short | Brawn to
short | Knowledge from
short | Knowledge to
short | Judgement from
short | Judgement to
short | Agility from
short | Agility to
short | Vitality from
short | Vitality to
short | Luck from
short | Luck to
short[8] | (0x60) Capable of this caste ????
short[40] | Conditions
short | Max age
short | Regeneration
short | Base movement points
short | Magic resistance
short | Two handed weapon modifier
short | Missile weapon modifier
short | Base attacks per 2 rounds
short | Max attacks per round
byte[30] | Capable of this caste
short | Youth from
short | Youth to
short | Young from
short | Young to
short | Prime from
short | Prime to
short | Adult from
short | Adult to
short | Senior from
short | Senior to
AgeGroup[5] | Age group modifiers
byte | ?
short | default portrait set?
int64 | useable items
short | race properties
short[31] | ?

**AgeGroup**

bytes | value
---|---
byte | Brawn
byte | Knowledge
byte | Judgment
byte | Agility
byte | Vitality
byte | Luck
byte | Magic resist
byte | Movement
byte | DR Vs Charm
byte | DR Vs Heat
byte | DR Vs Cold
byte | DR Vs Electrical
byte | DR Vs Chemical
byte | DR Vs Mental
byte | DR Vs Magical

# Data Caste

bytes | value
---|---
short | Start Sneak attack
short | Start Hide in shadows (unused)
short | Start Resurrect (unused)
short | Start Cause major wound
short | Start Detect secret area
short | Start Acrobatic act
short | Start Detect trap
short | Start Disarm trap
short | Start Hear noise (unused)
short | Start Force lock
short | Start Move silently (unused)
short | Start Pick lock
short | Start Read scroll (unused)
short | Start Turn undead
short | Levelup Sneak attack
short | Levelup Hide in shadows (unused)
short | Levelup Resurrect (unused)
short | Levelup Cause major wound
short | Levelup Detect secret area
short | Levelup Acrobatic act
short | Levelup Detect trap
short | Levelup Disarm trap
short | Levelup Hear noise (unused)
short | Levelup Force lock
short | Levelup Move silently (unused)
short | Levelup Pick lock
short | Levelup Read scroll (unused)
short | Levelup Turn undead
short | DR Vs Charm
short | DR Vs Heat
short | DR Vs Cold
short | DR Vs Electrical
short | DR Vs Chemical
short | DR Vs Mental
short | DR Vs Magical
short | DR Vs Special?
short | Brawn bonus
short | Knowledge bonus
short | Judgment bonus
short | Agility bonus
short | Vitality bonus
short | Luck bonus
short | Has sorceror spells
short | start level
short | max level
short | Has priest spells
short | start level
short | max level
short | Has enchanter spells
short | start level
short | max level
short | ?
short | ?
short | ?
short | Brawn min
short | Brawn max
short | Knowledge min
short | Knowledge max
short | Judgment min
short | Judgment max
short | Agility min
short | Agility max
short | Vitality min
short | Vitality max
short | Luck min
short | Luck max
short[40] | condition starting levels
short | Can use missile weapons
short | Missile bonus damage
short | Stamina base
short | Stamina levelup
short | Strength damage bonus start
short | Strength damage bonus max
short | Dodge missile bonus
short | Dodge missile per level
short | Melee tohit base
short | Melee tohit per level
short | Missile tohit base
short | Missile tohit per level
short | Hand to hand damage base
short | Hand to hand damage per level
short[4] | ? 
short | Caste category
short | Min age group
short | Movement
short | Magic resist multiplier
short | Two-handed weapon modifier
short | Max stamina bonus
short | Bonus attacks per 2 rounds
short | Max attacks per round
int[30] | Exp required per level
short | Starting gold
short[20] | Starting items
byte[10] | Bonus attack levels
int64 | Useable items
short | Icon?
byte[130] | ?

# Data S

spell definitions

bytes | value
---|---
int8 | fixed range
int8 | power range
int8 | queue icon
int8 | to hit modifier
int8 | DR modifier
int8 | number of attacks
int8 | can rotate
int8 | DR modifier/power level
int8 | resist type
int8 | DR/power level
int8 | SP cost
int8 | fixed damage min
int8 | fixed damage max
int8 | power damage min
int8 | power damage max
int8 | fixed duration min
int8 | fixed duration max
int8 | power duration min
int8 | power duration max
int8 | cast icon
int8 | resolution icon
int8 | cast sound
int8 | resolution sound
int8 | target type
int8 | spell size
int8 | spell effect
int8 | spell class
int8 | damage type
int8 | combat
int8 | camp

