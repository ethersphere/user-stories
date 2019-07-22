Tracks sync 22.07.2019
=======
Please provide your written feedback to give an update about the current status of the track as well as writing down blockers and risks which need to be addressed from other dependent tracks.

Epics / User Stories
General Updates of the Track
Blockers and Resource planning

Updates structure
Communication Track (Louis, Vojtech)
Core Track (Elad, Viktor)
Incentive Track (Fabio)
Network Testing Framework (Rafael)
Research (Daniel)

Other
Network-Testing 
Release Planning
Documentation


## Core Track (Anton, Viktor)
* Pull Sync should be finalised this week / early next week
* PSS is open Pull sync - louis will address open questions
    * Upload of 1 GB and Download was possible with 40 Swarm-Nodes (only with push sync, no pull sync)
* Small improvements have been done on API endpoints
    * Small improvments on testing
    * Structured output of Kademlia table per node
* Blocker: PSS (due to Push Sync being dependent on it)
* No update on Kademlia improvements
* No update on Download improvements

## Communication Track (Vojtech)
* Louis just came back from vacation
    * Brief update with Status - 
    * Short discussion Adaptive Node Track / Comm-Track
        * 
* Vojtech - IOV is commited to use to PSS and would like to support the adaptive node track with Status

## Incentive Track (Fabio, Vojtech)
* PR to master should be ready by EOW (ready or merged)
    * Open questions about details
* Idea to create a SWIP for the SWAP part
* OPEN QUESTION: L2 Smart-Contracts for Pinned conntent (with Zahoor) maybe Rinke and Rafael could start looking into that after completing the SWAP smart contracts? (Tim)

## Network Testing Framework (Rafael)
* Initial snapshot feature inside [PR#1555](https://github.com/ethersphere/swarm/pull/1555)
* Missing Tasks for the Framework
*  Louis Q: RPC Call which need to be included - whats the status on this?
    * "These" RPC Calls for Debugging or other purposes - are there any changes? Or is this future work? (Louis)
    * Anton answer: There is structured output on kadelmia. There are other ideas how to make simpler tests for the future. [PR#1586](https://github.com/ethersphere/swarm/pull/1586)
    * Rafael answer: That RPC call is also useful to test the snapshot feature
* Fabio question: Is this a proxy? What do I know to review the RPCs? 
    * Rafael: RPC via RPC call fuction. This is worked on. Some is already there for the BZZ client.
    * Fabio: How to check balance?

## Research (Viktor)
 * Session with Donni, Aron and Viktor
     * Worked on the open questions regarding the SWAP
     * https://swarmresear.ch/t/questions-on-incentive-development/37
 * Fabio: Useful input to fullfill the current needs of the incentive track. 
 * Viktor: How can we combine posted stamps + swap profitability - writeup TBD
 * Viktor: Fetcher timeout vs 404 if a chunker is not found - writeup TBD
     * Current Fetcher is not incentive compatible

## Business (Tim)
 * Ethereum Foundation supports the creation of a Swarm Foundation (Timeline aiming for Oktober / November to create the Swarm Foundation)

## Feedback
* Upfront summary written by tack-lead would be useful
* Review of the notes should also be done by the track-lead if not written by themselves
