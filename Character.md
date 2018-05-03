# Not complete


bytes | value
---|---
INT8[4] | ??? 
INT16 | Chance to hit
INT16 | Dodge missile
INT16 | Missile adjust
INT8[4] | ???
INT16 | Attacks per round ? (divide by 2)
10:

16:
INT16 | Number of items (max 30)

28:
INT16 | Magic resistance
INT16 | ???
INT16 | Armor rating
INT16 | Damage
30:
INT16 | Race
INT16 | Caste
INT16 | ???
INT16 | Gender
INT16 | Skill level
INT16 | ???
INT16 | Movement

4e:
INT16 | Current stamina (hit points)
50:
INT16 | Max stamina (hit points)
INT16 | Portrait ID
INT16 | Battle image ID
INT16 | Current spell Points
INT16 | Max spell Points
INT16 | ???
INT16 | ???
INT16 | ???


60:
INT16 | Bare hand damage
conditions:
INT16 | 
tilogmed 020

be:
INT16 | Remaining spell selection points

f6:
INT16 | Cause major wound
INT16 | Acrobatic act
INT16 | Force lock

110:
Demage reduction vs:
INT16 | Charm
INT16 | Heat
INT16 | Cold
INT16 | Electric
INT16 | Chemical
INT16 | Mental
INT16 | Magic
INT16 | Special

124:
items[]
INT16 | Item ID
INT8 | Equiped
INT8 | Identified
INT16 | Number of uses | Infinite = FFFF

1ec:
INT32 | Age in days
INT32 | Victory points
INT16 | Load
INT16 | Max load
INT16 | Gold
INT16 | Gems
INT16 | Jewelry

205:
INT8 | Brawn
INT8 | Knowledge
INT8 | Judgment
INT8 | Agility
INT8 | Vitality
INT8 | Luck

280:
INT32 | Damage taken
INT32 | Damage given
INT32 | Enemies killed
INT32 | Hits taken
INT32 | Missed attacks
INT32 | Dodged attacks
INT32 | Hits given
