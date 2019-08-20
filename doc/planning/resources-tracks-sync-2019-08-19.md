Tracks sync 19.08.2019
=======

## Core Track (Anton, Viktor, update given by Janos)

* New Stream fixes and performance improvements
* Continuing work on tags and pinning and documentation for the upcomming 0.5 release
* Benchmarking for bossible localstore improvements
* Adding multi chunk operations for localstore

## Communication Track (Louis)

* EPIC labs ready to submit PR on https://github.com/ethersphere/swarm/issues/1654 also well underway with https://github.com/ethersphere/swarm/issues/1652 will follow up with consolidating common test code in pss package
* Experimental code refactor to show how Kademlia can be provided as a service instead of embedding from outside constructors across modules https://github.com/ethersphere/swarm/pull/1676
  - also shows how hierarchical service tree in Swarm can be avoided)

## Adaptive Node Track (Louis)

* Felfele have refactored their POC build to use `go mobile` and built successfully. Need to define API for starting, stopping node etc.
  - Will keep API wrappers in separate repo for now.
  - Status will support them
* Adaptive capabilities intro PR merged https://github.com/ethersphere/swarm/pull/1619 followup PR introducing API currently in review https://github.com/ethersphere/swarm/pull/1675 then https://github.com/nolash/swarm/tree/adaptive-kademlia will follow
* Hacked the bzz handshake for `nim-eth`, successfully completes against `golang` node and entry found in kademlia https://github.com/oskarth/nim-eth/pull/2
* Had IRL meet with Status' Oskar and Dean, have consensus on data representation basics in spec authoring

## Incentive Track (Fabio, Vojtech)
* Viktor has made another review to the `incentives` PR, changes have been applied but there are still points to be resolved
* According to Fabio, we are expecting another review from Elad (this will be followed up on)
* 2 SWIPs will be pushed this week - msgHoney oracle and probably the multiple payments but as IOV
    * 2 more will be pushed next week
## Network Testing Framework (Rafael)
## Ethereum state on Swarm (Viktor)
## Research (Viktor)
## Business (Viktor)
## Feedback
