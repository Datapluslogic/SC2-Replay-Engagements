# SC2-Replay-Engagements

Logic applied to unit positional data (parsed from replays) to classify/break down engagement types.

## About this Project

This project is a collaboration between Firnafth and myself (Mina) primarily for sharing within the SC2 community for fun/educational purposes. The end result is likely to be published onto the ROOTGaming website.

## Sourcing the Data

Firnafth parses replays using [SC2API](https://blizzard.github.io/s2client-api/) to obtain positional data. Otherwise [s2protocol](https://github.com/Blizzard/s2protocol) (the more commonly used method to obtain positional data) is flawed (as indicated in official documentation).

### Engagements Thus Far

Originally when Firnafth manually recorded engagements during tournament analysis, she recorded three types of engagements: push, defense, harass. These engagement records were also primarily focused on army to army engagements.

In parsing/attaching information from replays, currently I am adding more of a breakdown with these engagements, in part so that I can ascertain that the engagements are being correctly classified, in part to add the ability for more accurate analysis. After I am happy with the classifications on a detailed level, it is much easier to bucket back up to a higher level or create an exclusion list of which detailed engagement types do not really qualify as engagements.

### Engagement Logic (as used in Alteryx)

Engagement Type | Logic
------------ | -------------
***Base Requirement for Engagement** | Is engaged with enemy army (taking or dealing damange, units within range of enemy army (<7)) OR Is engaged with enemy economy (dealing damage to economic units/building, units within range of enemy base (<7))
*Harass (Boolean) | <30% of Army supply in engagement group
Killing Overlords/Nydus/Creep |  Is engaged with enemy economy AND Killing Overlords/Nydus/Creep
Economic Damage - Town Hall/Workers/Buildings | Is engaged with enemy economy AND NOT Harass (Boolean)
Economic Harass - Town Hall/Workers/Buildings | Is engaged with enemy economy AND Harass (Boolean)
Army Engagement | No base within distance threshold (>30)
Push | Unit Group Closer to Enemy Base AND NOT Harass (Boolean)
Harass (Engagement Type) | Unit Group Closer to Enemy Base AND Harass (Boolean)
Defense | Unit Group Not Closer to Enemy Base

### Unit Groups
Unit per game, gameloop and player, is within range (<6) of another unit for the same game, gameloop and player.
If A is in range of B 
And B is in range of C
but A, B and C are not in range of any other units, then:

GroupID | UnitId
------------ | -------------
1 | A
1 | B
1 | C

### Unit Groups Over Time/Engagement ID
To be added.

## Contributors

* **Mina Ozgen/datapluslogic** - Engagement and Alteryx Logic
* **Firnafth** - Parsing Data and Engagement Logic

