Tracks sync 15.07.2019 (Written Feedback)
==========================================
Please provide your written feedback to give an update about the current status of the track as well as writing down blockers and risks which need to be addressed from other dependent tracks.

Epics / User Stories
General Updates of the Track
Blockers and Resource planning

Updates structure
Communication Track (Louis, Vojtech)
Core Track (Elad, Viktor)
Incentive Track (Fabio)
Network  Testing Framework (Rafael)
Research (Daniel)

Other
Network-Testing 
Release Planning
Documentation

## Network testing (Rafael)

- Initial PoC with Exec/Docker/Kubernetes adapters is working: [Draft PR](https://github.com/ethersphere/swarm/pull/1555)
- Written a discovery test using the new framework. Works on all 3 adapters.
- I will create a list of remaining tasks for the implementation of missing features and attach it to the [epic#33](https://github.com/ethersphere/user-stories/issues/33)

## Incentive track (extraordinarilly by Vojtech)
###  Hack week achievements:
- Implemented simple SWAP happy path only (=not handling edgecases, blockchain errors etc). 
![Happy path SWAP](https://i.imgur.com/c7pxy4J.png)
- In terms of the [metrics document](https://docs.google.com/document/d/1yAjCDbjXKJ3uZYOAQT0lAtq2rq1NvjGx12twhm5gRj4/edit) (~~strikethrough~~ items were planned but not achieved):
    - Admins can query node’s balances book through API
    - Nodes deploy SWAP smart contract and deposit as they go online ~~(if not already) and this is stored in persistent storage~~
    - ~~(ideally) Nodes replenish the SC with hardcoded value…~~
    - Nodes issue cheques to each other including the SWAP SC address
    - Cheques are cashed out immediately as they arrive, these are 2 calls
        - Submit cheque
        - Cash out cheque (after delay allowing challenge)
    - (ideally) ~~automated~~ (local) testing which deploys 2+ nodes and ~~simulates~~ manual traffic
    - ~~Integration with the new syncer~~
- You can try it on incentive branch (with custom network) by running: `swarm -swap -swap-api=https://rinkeby.infura.io` but make sure you have some rinkeby eth
- [List of assumptions and decisions](https://hackmd.io/5457QI8SRf-Byhp6xY-jEg?view) made
- Increase a familiarity with a go code and reponsibles/experts for individual parts
- Established communication with the Swarm team
- 3 new epics/user-stories
- End-do-end test contract test with simulated backend

### Lessons:
- It is difficult to coordinate with track lead who is not physically present and it creates delays and tensions. For the next time we should make a separate branch for the hack week that is then merged.

### TODO: 
- Number of [new issues](https://github.com/ethersphere/swarm/issues?q=is%3Aissue+is%3Aopen+label%3Aincentives) to tackle
- Polish the `incentives` branch and prepare merge to `master` (this includes a bigger discussion and implementing things like [#1550](https://github.com/ethersphere/swarm/issues/1550))

### Blockers:
- Still unclear how will research decisions be finalised


## Eth on swarm
- successful handshake between trinity and swarm  
phase 0 of the [epic](https://github.com/ethersphere/user-stories/issues/9) is dev ready
- Elad and Viktor submit [first bzzeth PR](https://github.com/ethersphere/swarm/pull/1571)
- iteration on epic
- to write up incentive aligned strategy to handle newblock header hashes 
- start work on phase 1

### Blockers

protocols.go message wrapping causes incompatibility 
https://github.com/ethersphere/swarm/issues/1575

## Core track

1. Push sync / PSS
- added tracing to Push sync
- added PSS timers and dashboard
- fixed blocking calls between Push sync and PSS
- attempt to profile PSS and to increase performance - https://github.com/ethersphere/swarm/issues/1574

2. Pull sync

- improved existing tests
- added live and combined live and history test cases
- added benchmarks (which turn out to be not so reliable)
- defined more test vectors
- integrated new retrieval and streamer onto swarm.go and started running integration tests

3. Efficient download
- no progress

4. Kademlia improvements
- no-hive-discovery flag, as preparation for integration tests - https://github.com/ethersphere/swarm/pull/1576
