Tracks sync 23.09.2019
=======

## Core Track (Anton, Viktor,Janos)
- Preparation for 0.5 release, biggest blocker is push syncing

## Communication Track (Louis)
- Several PSS stuff has been merged, some of it is being rolled back

## Adaptive Node Track (Louis)
- PRs has been merged, capabilities in kademlia and PSS
- new SWIP about how to request connectivity with peers based on capabilities, both in review

## Specifications Track (Louis)
- 

## Ethereum state on Swarm Track (Viktor)

- bzzeth phase 1 in progress
    - PR https://github.com/ethersphere/swarm/pull/1685
    - User Story https://github.com/ethersphere/user-stories/issues/54

## Incentives Track (Fabio, Vojtech)
- Priority is to generate deployments, we'll have demonstration how to do this on kubernetes later today
- We'll create SWAP enabled network
- Issue: currently when we deploy chequebook, it is not prefunded -> needed for Devcon, probably will not make it until next release
- 

## Ethereum state on Swarm (Viktor)
- reviewed PR for phase 1
- preparing for our talk with Piper and Zahoor: 

## Research (Daniel)
- specification for the [Postage Stamps](https://github.com/nagydani/SWIPs/blob/postage/SWIPs/swip-postage.md) is ready for implementation, probably impementation after devcon, Dani would like to participate in implementation
- Call for developers to read the specifications

## Network Testing Framework (Rafael)
- Integration of the ganache (eth blockchain for testing) helm chart with the swarm helm chart finished.
- Call with the incentives track to demo a SWAP enabled swarm cluster on kubernetes.

## Business 
- Last phase of porting contracts from Dani's company to new structure. Burn rate too high, Dani and Victor cannot take salary. Business talk next Thrusday with a partner who can chip in, Consensys might help as well, talks planned with strategic partners on Devcon.
- Remark: Victor would like to have a sprint for Devcon to realize 0.5 release. All track leads: decide on what must be in the code before Devcon. - Request for features which will be in the code after Devcon and their oder of importance.

## Feedback
- Elad: There was no onboarding for the SWIPs, it is not clear what the process is. We should introduce it into the team. Elad will schedule a call with Louis, Dani and everyone who is interested on Friday.
- There will be no release tomorrow because of the performance issues, we take a time until the end of the week 
