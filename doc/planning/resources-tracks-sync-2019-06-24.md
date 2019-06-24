Resource planning 24.06.2019
======

Note: Session will be recorded.

Next Release: [0.4.2 Milestone](https://github.com/ethersphere/swarm/milestone/12) 
Lake Balaton July 7-14th

# Agenda Points (by each TracK-Lead):
- Epics / User Stories 
- General Updates relevant for all tracks.
- Blockers and Resource planning

# Updates structure
- Communication Track (Louis, Vojtech)
- Core Track (Elad, Viktor)
- Incentive Track (Fabio)
- Network  Testing Framework (Rafael)
- Research (Aron)

# Other
- Release Planning - milstone for `0.4.2`: https://github.com/ethersphere/swarm/milestone/12?closed=1


## Incentive Track (Fabio)
* Smart-Contract Devs start next week (01.07.2019)
* Check Exchange Protocol is ready in a basic implementation
* RISK: Branches - syncing is planned between Fabio and Marcelo

### Open Questions
* Incentive: Funding / Having a "own" Swarm Coin? 
* Are we considering any Swap coin? Not urgent, but would like to kick off this question
* Deployment of Swap enabled nodes? If thresholds implemented disconnects can occur, how do we deploy this into the main network? Separate network/separate branch?
* Migration and upgrades of swap contracts - how do we roll out upgrade if any bugs are found/new features implemented?

## Core Track (Elad)
- Writing on the pull-syncer (for more stability)
- focused on 100GB file MVP (LINK TO Datafund 100 GB MVP)
- Hiring process has been started to be defined https://docs.google.com/presentation/d/1yks7JiW4VTVJ-5uTRK1vipt35ExoJ14TRnDmnnCA1L0/edit?usp=sharing
- Janos (Core Member) will come back after a 2 month vacation leave on the 01.07.2019

### Open Questions:
- How we do retrievels is a tension point which needs rework to allow bigger files to be retrieved

## Communication Track (Louis)
- Goal of the comm-track is also having multiple client implementations
- All user-stories written and added to https://github.com/ethersphere/user-stories/issues?q=is%3Aissue+is%3Aopen+label%3Atrack%3Aadaptivenodes
- Two epics: One for adaptive nodes MVP which includes enabling pss and bzz on light mode operation. One for specifications allowing for alternative implementations of the Swarm node.
- Development schedule outline: https://github.com/nolash/swarm-adaptive-node/blob/master/schedule.md 
- Need input from Rafael and Elad on milestones from the schedule depending on features from their tracks, specifically:
  - Rafael: anything marked with `networktest`
  - Elad: Finished specs for stream and retrieve protocol by end of week 29 
  - Elad: Finished streaming protocol refactor and explicit retrieve protocol by the end of week 33
* Started writing specs, by now bzz handshake and (most of) pss ready for review. Found at https://github.com/ethersphere/node-implementer-spec
* Please let's use a "hackmd" which does NOT require login to edit.


### Open Questions:

## Research Track (Aron)
- Focus on research Proof of Burn for swarm

### Open Questions:
- Whats the current status of the Proof of Burn research? (Requested by Louis for the Comm-Track) is overdue as it was communicated that there will be some results

## Network  Testing Framework (Rafael)
- Initial [Docker Adapter PR](https://github.com/skylenet/go-ethereum/pull/1) for internal review/feedback

### Open Questions:
- Review of Work from Rafael (Review by Lewis and Louis)

### Discussion
- Ethereum State on Swarm (Update from Viktor)
    - Meeting with Piper this week
- Prototype of the downloader for buffer

- Louis Discussing the Milestones (Request by Louis to get input)
- Input Rafael and Elad required to confirm milestones

