Tracks sync 09.09.2019
=======
Please all track leaders do a bit of issue grooming and assign good first issue labels to appropriate tasks. There is interest from potential contributors.


## Core Track (Anton, Viktor, update given by Janos)
- focus this week will be merging the new streamer
- also push syncing PR (to be merged this week or next one) 
- other non-crucial experiments going on

## Communication Track (Louis)
- PR for removing whisper from PSS in review https://github.com/ethersphere/swarm/pull/1731
   - estimated week or so before finished
- Cleanup PSS code ongoing, first step PR https://github.com/ethersphere/swarm/pull/1734
  - Will be done stepwise, first component (cache) working on, using a dated testing framework which is not used by other Swarm packages (might discuss during roundtable)
- First draft spec for kademlia forwarding (and prerequisites) PR https://github.com/ethersphere/SWIPs/pull/24
  - to be reviewed
- Submitted proposal 50% of devcon breakout slot about modular crypto in pss

## Adaptive Node Track (Louis)

- Still working on inclusion of capabilities in kademlia/discovery, experiencing trouble with RLP serializations in integration tests https://github.com/ethersphere/swarm/pull/1713
- Submitted proposal 50% of devcon breakout slot about adaptive modes of operations (API plus example involving PSS)

## Incentives Track (Fabio, Vojtech)
- working on tasks from `incentives` to `master` PR
- looking into in-process simulations
  - difficulties simulating w/swap due to back-end URL param, interaction with blockchain, etc.
  - current simulation alternative is not suitable with integration testing
- multiple PRs open
  - discuss review process during the roundtable

## Network Testing Framework (Rafael)
- skipped, Rafael not present

## Ethereum state on Swarm (Viktor)
- working on bug not caugh by unit tests
- tests for phase 1 went well

## Research (Daniel)
- Postage stamp SWIP https://github.com/ethersphere/SWIPs/pull/8
  - objective: produce and specification that can be implemented now (might share tomorrow)

## Business (Tim)
- need stable version of swarm to move ahead

## Feedback

