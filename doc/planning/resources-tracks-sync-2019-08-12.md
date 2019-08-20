Tracks sync  12.08.2019
=======
Please provide your written feedback to give an update about the current status of the track as well as writing down blockers and risks which need to be addressed from other dependent tracks.

Epics / User Stories
General Updates of the Track
Blockers and Resource planning

## Core Track (Anton, Viktor, update given by Janos)

- New stream memory leak fix
- HTTP API support for pinning contents - bzz-pin scheme handlers https://github.com/ethersphere/swarm/pull/1658
- Progress bar HTTP API - bzz-tag scheme handlers https://github.com/ethersphere/swarm/pull/1649
- Go Modules, vendoring https://github.com/ethersphere/swarm/pull/1532 and linting https://github.com/ethersphere/swarm/pull/1661

## Communication Track (Louis, Vojtech)

- Epic Labs started working on task pss send queue optimization https://github.com/ethersphere/swarm/issues/1654  
  * work will be coordinated here https://beehive.ethswarm.org/swarm/channels/pss
- Waiting for feedback from IOVLabs on existing pss spec/documentation
- Updated pss prox test to use distance as success metric - branch here: https://github.com/nolash/swarm/tree/pss-prox-distance-test which depends on https://github.com/ethersphere/swarm/pull/1621
  * The test can and should now be simplified (all of them actually need a [refactor](https://github.com/ethersphere/swarm/issues/1652)), but should be done after we implement [kademlia as-a-service](https://github.com/ethersphere/swarm/issues/1656) 

## Adaptive Node Track (Louis)

- Progress divided in three sequentially dependent branches. They are currently working and tests passing. However, the first PR was amended after comments to use bool arrays instead of bitflags for storing capabilities, but this is inefficient when comparing caps to each other, so this change should be reverted. Conceptually it need not change.
  * [adaptive capabilities protocol](https://github.com/ethersphere/swarm/pull/1619)
  * [adaptive capabilities API](https://github.com/nolash/swarm/tree/adaptive-capabilities-api-short)
  * [adaptive capabilities kademlia integration](https://github.com/nolash/swarm/tree/adaptive-kademlia)
- Adaptive SWIP must be rewritten as platform independent spec.
  * Handshake and pss spec will depend on this SWIP.
- Since noone in the team responded to my request for adding status as reviewers in the SWIP repo, the preliminary discourse is now happening on my own fork https://github.com/nolash/SWIPs/pulls - this is pretty silly, and it's annoying that such a simple little thing needs to be chased so much.

## Incentive Track (Fabio, Vojtech)
- We still have the [big PR open](https://github.com/ethersphere/swarm/pull/1554), Elad did another review today, there is only a few comments, hopefully will be resolved today
- Reduced the 5 to 3 [SWIPs](https://github.com/Eknir/SWIPs), in internal review now

## Network Testing Framework (Rafael)
- No change. Nothing to update.
- SWAP testing on kubernetes: Rafael to discuss requirements with Fabio.

## Ethereum state on Swarm (Viktor)
- Done with Phase 1 (integrations tests to be done)
- Zahoor will hopefully help this week
- This week continue to work on Phase 2
- Track sync call with Piper this Thursday
- Funding secured through Giveth platform

## Research (Viktor)

## Business (Viktor)
- The big kick off call for the legal entities
    - Short term Swarm Foundation, possibly also service company
    - Long term possibly consortium
    - Maybe DAO as well

## Feedback
- Reaction to Status team not being added to the Swarm repo
    - Suggestion from Viktor: We should dedicate someone who is responsible for this admin stuff and devops
- Question about Adaptive notes: There is a need in the Incentive team to negotiate things like prefered payment solutions at handshake - should this be reflected in the adaptive nodes SWIP?
- There has not been updates from the Network Testing Framework, what is the status?
  * (lash) **Q:** would like to know eg can I with CURRENT state of framework create a remote node test with pss nodes sending and receiving messages?
    * (rafael) **A:** Yes, any exposed RPC calls (also the ones for PSS) can be executed. See this [example](https://github.com/ethersphere/swarm/blob/master/simulation/examples/cluster/cluster_test.go).
- Milestone for Ethereum foundation: How important it is? With Rafael & Anton on holidays leading to the delivery, 
    - (vik) let's push for the delivery by the end of August 
    - (lash) when we define milestones there should be some degree of "celebration" on reaching them. otherwise it feels more like a "hurry up and wait" trap, which is anti-climactic and can easily be detrimental to morale
- New developer for incentives
- SWIP workflow - can we work on the branch of SWIP repo rather than creating fork and working there? Because if not we need to replicate the access rights to the repo.
    - (viktor) Encourages working directly in the ethersphere repo on a separate branch
