# Rules

## Initiation

I don't have a game built around this, but somehow two players enter into a battle. 
I imagine that they each have a facedown pile of about 5-10 unit cards, but any number will work.


## Unit Cards

A unit card is the basic, well, unit that will be used to conduct battle.
Each card has at least one symbol, but they can have multiple and theoretically in any combination.

### Symbols
#### Spear (|)
Weapon, attacks with speed 3
#### Sword (!)
Weapon, attacks twice with speed 1 and 2
#### Shield (@)
Defense, block one attack against this unit
#### Fortress (&)
Defense, block one attack against any unit in this coloumn or the two adjacent coloumns
#### Bow (-)
Support, subtract 1 from the speed of enemy units on this coloumn and the two adjacent coloumns
#### Crown (+)
Support, add 1 to the speed of your units on this coloumn and the two adjacent coloumns

ex.
```
[| ] <<< a unit with a spear
[!@] <<< a unit with a sword and a shield
[&& 
 & ] <<< a unit with three fortresses
```


## Setup

Each player secretly sets up thier army.
 - Unit cards can be set up in two lines, a front line and a back line.
 - Only one card can be placed in each column per line.
 - A card can only be placed in the back line if there is a front line card in the same column.
 - There cannot be any gaps in the front line.
 - There must be an equal number of front line units on either side of the center divide (+/- 1).
 - While it is often best to put weapon units in the front line and support units in the back,
 there are no rules about which units you put in which line.
 
ex. 
```
[! ][| ].[|@][! ][! ]  <<< Front Line
    [- ].[+ ]          <<< Back Line
        ^
        Center Divide
```
The armies are then revealed and placed facing eachother with the center divides lined up

ex., if both players built the army above:
```
        [+ ].[- ]
[! ][! ][|@].[| ][! ]
---------------------
    [! ][| ].[|@][! ][! ]
        [- ].[+ ]
```


## Combat

At this point all decisions are finished, and combat takes place deterministically.

Combat takes place over a number of rounds until one or both armies are eliminated,
or a round passes with no change (generally if neither player has a weapon in their front line)

As combat is entirely deterministic, it can be ended early once the outcome is clear.
For example, if only one player has weapons symbols left.

### Step One: Determine unit speeds

For each spear and sword on the front row, adjust their speed.
 - Increase the speed by 1 for each of your crowns in the unit's coloumn and adjacent coloumns
 - Decrease the speed by 1 for each enemy bow in the unit's coloumn and adjacent coloumns
 - Swords have two attacks, both of which will be adjusted (ie. 1&2 => 0&1 if one enemy bow is present)
 - If an attack's speed is reduced below zero, the attack does not happen
 - Mark each weapon's speed. 
 A weapon's speed will not change during a round even if the support units affecting it's speed are killed.
 - Weapons on a unit in the back row have no speed and will not be used this round.
 
ex.

```
        [&&].[- ]
[! ][! ][|@].[| ][! ]
---------------------
    [! ][| ].[|@][! ][! ]
     12  3    3   12  12    <<< mark initial speeds
        [+ ].
        
        [&&].[- ]
[! ][! ][|@].[| ][! ]
---------------------
    [! ][| ].[|@][! ][! ]
     23  4    4   12  12
     ^^  ^    ^             <<< add 1 to speeds for friendly crown (+)
        [+ ].
        
        [&&].[- ]
[! ][! ][|@].[| ][! ]
---------------------
    [! ][| ].[|@][! ][! ]
     23  3    3   01  12  
         ^    ^   ^^        <<< subtract 1 from speeds for enemy bow (-)
        [+ ].
```

### Step Two: Attacks
Attacks are carried out in order of speed.

Weapons with the highest speed attack first.

All weapos with the same speed attack simultaneously.

Only front line units attack or get attacked.

Starting with the highest speed of any weapons in the battle, 
each player does the following for each of their front line units with that speed.
 - Determine which unit to attack. 
   - If there is a front line unit directly across, that unit is attacked.
   - Otherwise if there is a front line unit to the right, that unit is attacked.
   - Otherwise if there is a front line unit to the left, that unit is attacked.
   - If there are no front line enemy units accross or diagonal, the attack does nothing.
 - Place an attack marker (*) on the targeted enemy unit.
   - An enemy unit may have multiple attack markers placed if multiple of your units attack at the same speed.
   or if one of your units has multiple of the same weapon.

Then each player resolves the attack markers on their units.
 - First, if a unit has an unbroken shield, mark the shield as broken (x) to discard an attack marker.
 - Then, if their is an unbroken fortress within one column, mark the fortress as broken (X) to discard an attack marker.
   - If multiple units would need the same fortress, priority is given to a unit on the same coloumn as the fortress, 
   then the column to the right, then the coloumn to the left.
 - If there is still at least one attack marker on a unit that unit is killed. Remove the unit card from the battle.
   
Repeat this process for all present attack speeds, down to 0. Any weapon with an attack speen less than zero does not attack.


ex.

```
        [&&].[- ]
 12  12  3    3   12       
[! ][! ][|@].[| ][! ]
---------------------
    [! ][| ].[|@][! ][! ]
     23  3    3   01  12  
        [+ ].

Speed 3:
Place attack markers:
        [&&].[- ]
 12  12  3    3   12       
[! ][! ][|@].[| ][! ]
     *   *    *           <<< each attacking unit has an enemy across from them to put an attack marker on
---------------------
         *    *
    [! ][| ].[|@][! ][! ]
     23  3    3   01  12  
        [+ ].
        
Resolve attack markers:
        [XX].[- ]         <<< the fortresses abosbs two attacks (note the unit remains despite having no symbols left)
 12  12  3    3   12       
[! ][! ][|x].[| ][! ]     <<< the shield absorbs one attack
---------------------
    [! ]    .[|x][! ][! ] <<< the shield absorbs one attack, but the other unit is killed and removed
     23  3    3   01  12  
        [+ ].
        
Speed 2:
Place attack markers:
        [XX].[- ]
 12  12  3    3   12       
[! ][! ][|x].[| ][! ]
     *            *       <<< because there is no unit across or diagonally to the right of the last sword unit, 
---------------------          it attacks the unit diagonally to its left
     **           *       <<< two weapon attacked the fist sword unit, so it has two attack markers on it
    [! ]    .[|x][! ][! ]
     23  3    3   01  12  
        [+ ].
        
Resolve attack markers:
        [XX].[- ]
 12  12  3    3   12       
[! ]    [|x].[| ]
---------------------
            .[|x]    [! ]
     23  3    3   01  12  
        [+ ].

Speeds 1 and 0:
Attacks aren't carried out if the unit was killed before they get the opportunity.

Each side has a sword with an attack at speed 1, but they have no targets within reach
 so their attacks have no effect.
```

### Step 3: Regroup

If neither side has been destroyed, the armies now regroup in preperation for the next round.

First, if any back row unit does not have a front row unit in front of it, move that unit to the front row.

Then, if their are any gaps in your front line, more units towards the center divide until there are no gaps.
Backrow units move with the fron row unit ahead of them, so that they always remain in the same coloumn.

If their are at least 2 more front line units on one side of the center divide than the other,
 move the center divide over until the two sides are even (+/-1)

Finally, set the two armies against eachother with the center divides lined up.

ex.
```
At this point in the example above, an experienced player could probably see that the lower army will lose,
 so they could concede defeat rather than play it out.

But if the player was at all unsure, they would regroup their armies for another round of combat.

Before regroup:
            .[|x]    [! ]
        [+ ].
First move up back line units with no units ahead of them:
        [+ ].[|x]    [! ]   <<< in this case the army no longer has a back line
Then fill all gaps by moving units towards the center divide:
        [+ ].[|x][! ]       <<< if they did have back line units they would move with the units ahead of them
There is only 1 more unit on the left than on the right, so no need to move the center divide.
Set back up against the enemy army:
        [XX].[- ]    
    [! ][|x].[| ]
---------------------
        [+ ].[|x][! ]
```

Destroyed shields and fortresses remain destroyed until the battle is over.

## End of battle

If one of the armies is completely destroyed, and the other still has at least one unit,
 the side that still has units wins

If both sides are completely destroyed, or unable to attack eachother (no weapons in the front line,
or some rare situations with many archers) then the battle is a tie.

Since I haven't built a game around this yet, I can't say what the effect of a win/lose/tie would be,
 or whether it would matter if units survive.
