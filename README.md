# SC2-Replay-Engagements

Logic applied to unit positional data (parsed from replays) to classify/break down engagement types.

## About this Project

This project is a collaboration between Firnafth and myself (Mina) primarily for sharing within the SC2 community for fun/educational purposes. The end result is likely to be published onto the ROOTGaming website.

## Sourcing the Data

Firnafth parses replays using SC2API to obtain positional data. Otherwise s2protocol (the more commonly used method to obtain positional data) is flawed (as indicated in official documentation).

### Engagements Thus Far

Originally when Firnafth manually recorded engagements, she only recorded three types of engagements: push, defense, harass. These engagement records were also primarily focused on army to army engagements.

In parsing/attaching information from replays, currently I am adding in more of a breakdown with the engagements, in part so that I can ascertain that the engagements are being correctly classified. After I am happy with the classifications on a detailed level, it is much easier to bucket back up to a higher level or create an exclusion list of which detailed engagement types do not really qualify as engagements.

### Engagement Logic (as used in Alteryx)

Engagement Type | Logic
------------ | -------------
*Base Requirement | Is engaged with enemy army (taking or dealing damange, units within range of enemy army) OR Is engaged with enemy economy (dealing damage to economic units/buildings)
Killing Overlords/Nydus/Creep |  Is engaged with enemy economy AND NOT Killing Overlords
Economic Damage - Town Hall/Workers/Buildings | Is engaged with enemy economy AND NOT Harass 
Economic Harass - Town Hall/Workers/Buildings | Is engaged with enemy economy AND Harass
Army Engagement | No base within distance threshold (20)
Push | Unit Group Closer to Enemy Base AND NOT Harass (30% of Army supply or greater in engagement group)
Harass | Unit Group Closer to Enemy Base
Defense | Unit Group Not Closer to Enemy Base

## Contributors

* **Mina Ozgen/datapluslogic** - Engagement and Alteryx Logic
* **Firnafth** - Parsing Data and Engagement Logic

