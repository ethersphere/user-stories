Tracks sync 01.07.2019
======

Note: Session will hopefully be recorded.

This is a holiday for some of the team. Participation is optional. Session will be recorded.

# Agenda:


General Updates of the Track
  * Epics / User Stories 
  * Blockers and Resource planning
General discussion


# Updates structure

Communication Track (Louis, Vojtech)
Core Track (Elad, Viktor)
Eth on Swarm (Vik)
Incentive Track (Fabio)
Network  Testing Framework (Rafael)
Research (Aron)


# Other

Network-Testing 
Release Planning
Documentation


## Communication Track (Louis, Vojtech)
[SWarm Improvement Proposal (SWIP)](https://github.com/ethersphere/swarm/issues/1514)
Currently no real blockers, did not hear from Status yet for both the proposal nor the specs.

## Core Track (Elad, Viktor)
Vik submit pr to push sync branch - problems sim framework
1. anton and vik disagree on implementation
2. fix bug which makes test pass

hopefully merge after next review
http download is reading in sync batch, but could do parallell req instead, creates unnecessary latency.
Elad making good progress on pull sync, anton helping reviewing
Janos is back, being assimilated
Hopefully with better traceability, if chunk is not synced, better understand where failed
Board is up to date

## Eth on swarm
telegram group set up, bridged to mattermost
epic finalized for header chain, 3 phases set up, will be made to user stories
upcoming task: come up with user stories for the epics/phases
https://github.com/ethersphere/user-stories/issues/9 

## Incentive Track (Fabio)
No much happened on board.
Rinke 100% and Ralph 40% are officially working
First done task: drop submitcheque...
Flow diagram how messages will be handled
Discussion and new questions:
https://github.com/ethersphere/swarm/issues/1506
more integrated process working with research, aron not on github how to poke, dani good session 1-2 weeks. need more than one session per week. Better to have official protocol - get attention and address research stuff
fabio worked on cheques exchange protocol - where get private key, there is legacy code, went through with vik to decide what to prune, => rabbit hole, addresses a lot of different interrelated things so may be a longer task.

3 SWIPs in work:
- Payment mechanism - proposal how multiple payment solutions could work together (own payment channel implementation, lumino/raiden...)
- how to handle advances ui that includes payment + upload (right now we have simple gateway to just download files)
- JS libraries with support for incentive

## Network  Testing Framework (Rafael)

- Tried using exec/docker adapters on existing tests and failed
- Comming up with an alternative approach
- Proposal to be done on tomorrow's Roundtable (02.07) 
- rafael will sync with janos

## Research (Aron)
- Had several discussions (Aron & Dani, or Aron, Dani & Viktor). Daniel is working on an exhaustive list of anticipated node interactions and their incentive compatibility. Key questions involved syncing and lottery and their relation to xor distance in most proximate nbhd.
Ideas discussed are payment-via-lottery to avoid the 'burn' in postage. Incentive compatibility of pay-for-sync. Future transition of postage to storage insurance. 
Dani will post his writeup to swarmresear.ch later today.

## Entanglement codes research collaboration

Had call Vik Aron
Submit talk to Devcon
Found some issues not covered
Will be writing EPIC (when?)
In order for it to be proper track, needs to tackle chunker, probably not be very soon


## Documentation
Is a separate track, but there is no lead yet.


### Discussion

- Sync with research. Was meeting set up thursday two weeks ago. Dont know why. had last thursday also, not all present.
  * research channel in mattermost for quick question - to draw attention to a need / topic
  * mattermost is emphemeral, gets lost if time passes. not for permanent decisions.
  * treatment, conclusion, decision -> swarmresear.ch
- Need a source-of-truth document! <- this is the most important, get this started.
- calls are a good medium to involve as many research ppl as possible, we need a way to document decisions we make
- more reliable way for back-and-forth
  * ex threshold handling, when should drop peers? also affects other protocols, should be agreement on when to drop peers and what are the repercussions.  
- when is should be elevated to the research group, what can be replied directly from single member. usually just post to research channel, if noone says something it.
- we seem to converge on:
  * mattermost for get attention
  * swarmresearch for discussion if question that needs treatment
  * stored in a "formal" document (where? need to decide) when finalize 



