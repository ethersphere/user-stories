Tracks sync 16.09.2019
=======

## Core Track (Anton, Viktor,Janos)
- Work on push syncing continues
- porting incentivization into retrieval
    - Open question whether there must be a price for syncing
   - there is a PR for this (https://github.com/ethersphere/swarm/pull/1758) - must be checked by someone from incentives


## Communication Track (Louis)

- Modular crypto first step completed
  * remove whisper
  * replace with modular crypto backend, temporary api
- Epic Labs propose removing crypto from node, leaving crypto at discretion of higher layer + extract all pss component in separate packages
  * add a header field encrypted with the pss public key that hints at crypto scheme used
  * will implement an example crypto API extension for presentation at devcon
  * more details on the proposal here https://swarm-gateways.net/bzz:/c2340d4557c4dddc8472763947e81785e4eaa8e1d5ccca247f7b4906e2ff6cfa/?content_type=application/pdf
- Remove the protocol, handshake, notify and client from pss
- Task roadmap being developed for adaptive, kademlia, pss
  * https://swarm-gateways.net/bzz:/c74ae046e6152ecb8267eb54085ba7035a83f0c9a4aa905df7358efeb53de3e9/
  * kademlia prioritization will be discussed at roundtable 17.9
- SWIP for initial kademlia load balancing proposed
  * https://github.com/ethersphere/SWIPs/pull/28
  * Epic Labs Álvaro will implement

## Adaptive Node Track (Louis)

- Kademlia capabilities integration PR submitted for review, approved by @zelig, reviewed by Álvaro
  * https://github.com/ethersphere/swarm/pull/1713
- Next step is enable live change of capabilities, preparation for demonstration at devcon

## Specifications Track (Louis)

- New SWIP first drafts added:
  * hive (connectivity engine) - https://github.com/ethersphere/SWIPs/pull/25
  * discovery protocol - https://github.com/ethersphere/SWIPs/pull/26
  * content hashing - https://github.com/ethersphere/SWIPs/pull/27
- SWIPs updated with dependencies for the above:
  * kademlia - https://github.com/ethersphere/SWIPs/pull/24
  * address fundamentals - https://github.com/ethersphere/SWIPs/pull/17

## Incentives Track (Fabio, Vojtech)
- Creating a series of PRs (improving SWAP code to be more robust)
- This week want to integrate retrieval protocol and deployment to test network

## Network Testing Framework (Rafael)
- Swarm-private helm chart: Possibility to provide configuration to specific swarm containers: [ethersphere/helm-charts#94](https://github.com/ethersphere/helm-charts/pull/94)
- Started integration of the ganache (eth blockchain for testing) helm chart with the swarm helm chart, so that we can start running deployments with incentives enabled.

## Ethereum state on Swarm (Viktor)
- Merged fix for phase0 PR (bug which didn't allow disconnected nodes to reconnect)
- Phase1 will be done by Thursday (probably)

## Research (Daniel)
- no updates

## Business (Victor)
- Last phase of porting contracts from Dani's company to new structure. Burn rate too high, Dani and Victor cannot take salary. Business talk next Thrusday with a partner who can chip in, Consensys might help as well, talks planned with strategic partners on Devcon.
- Remark: Victor would like to have a sprint for Devcon to realize 0.5 release. All track leads: decide on what must be in the code before Devcon. - Request for features which will be in the code after Devcon and their oder of importance.

## Feedback
- Confirmation on not paying for synching (question by Marcello)
- A: Postage stamp for spam protection, also paying via SWAP.
