# Cake of Doom simulation
## Functional and Technical Specification

Pearl Ho

----

## Abstract

The goal of this repo is to help design Cake of Doom, a tabletop game. 

It will complement real life playtests by simulating playthroughs in large numbers, so the designers can better understand edge cases.

## Assumptions

This will be ran locally by technical user(s).

This is for use specifically with Cake of Doom and does not need to generalise to other games.

Cake of Doom's core game flow will remain:
1. Player gain cards.
2. Player uses cards and attempt to gain region(s).
3. Other players may sabotage.
4. Next player.

Though setup, rules and victory condition(s) will have tweaks.

## Requirements 

The tool should be usable via command line.

**Execution options**

Configurable via (optional) cli arguments:
 - number of players
 - number of playthroughs to simulate

Configurable via env or config files such as yamls:
 - number of regions, their min value and their control bonus
 - which regional specialties are applicable for the winning move (inc. randomised)
 - size and mix of the cake deck
 - size and mix of the disasters/actions deck
 - size and mix of players' starting hands (inc. randomised)
 - mix of player styles (pre-defined in code)
 
 **Player Styles** 
 
 These will be defined in code and should include at least:
 - _logical_: plays maximising chances of winning
 - _casual_: some randomness in decisions, but behaves logically for critical decisions
 - _saboteur_: enjoys playing disasters and taking from others, plays to revenge
 - _cake hog_: focuses on cakes and 'saving up', instead of interactions
 
 **Output** 

Simulation outputs will be timestamped and stored locally as csv file(s), since this is simple and accommodates less technical users downstream.

Key summaries will be created automatically:
 - Confirmation of config ran
 - Distribution of game duration (by rounds)
 - Distribution of bribes attempted and successful
 - Distribution of disasters played
 - Distribution of winner by player position
 - Distribution of total cake cards required
 - Distribution of total action/disaster cards required

The outputs should be structured and allow analysis of/by:
 - game duration (number of rounds)
 - player position
 - player style
 - number of players
 - control of specific regions (historically and at endgame)
 - win/lost
 - frequency and intensity of disasters
 - frequency of actions
 - frequency of bribe attempts
 - frequency of game-winning attempts
 - 'safety margin' of bribe attempts
 - stealing regions vs targeting neutral regions
 - whether the Cake Monster was played (or drawn)

## Technical Requirements

The tool should warn/refuse to run if the user attempts something too demanding.

Technical logs can be saved locally. This should include:
- full config of the run
- each step in the simulation
- duration and timestamps
- any errors/warnings
- outputs created, timestamp, and destinations

## Future features

Ideas for improvements:
- Hooks for checks and tests on PR/commit to main
- UI for running and/or configuring
- Hosted and usable via a web interface
- Config of decision making (e.g. whether to play disaster, what region to bribe)
- Automation of graphs/analysis post simulation
- Automatic flagging of spikes / unusual / undesirable cases
- Behaviour when there are no more cards?
