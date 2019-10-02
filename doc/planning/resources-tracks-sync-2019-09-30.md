Tracks sync 30.09.2019
=======

## Core Track (Anton, Viktor, Janos)
- tomorrow test of the workshop for Devcon (2 PM CEST)
- 0.5 release
- push syncing merged, outstanding:
    - push/pull sync together  
        - session option -> runtime option
        - anonymous upload https://github.com/ethersphere/swarm/pull/1828
    - progress bar 
        - cli https://github.com/ethersphere/swarm/pull/1814
        - http ui : dan, elad, rafael work on simple js
    - pss indefinite reenqueue issue 
        - mitigated by disconnecting the bootnode from cluster - to be fixed

## Incentives (Vojtech)
- We need PR with the exposed 

## Communication Track (Louis)
- Forward cache refactor created problems for push sync stability, needs investigating
- Asynchronous message handling added to improve performance may need improvements

## Adaptive Node Track (Louis)
- SWIP about how to request connectivity with peers based on capabilities and PSS capabilities both still in review

## Specifications Track (Louis)
- Oskar has reviewed the current pending spec SWIPs. Will attend to comments this week.

## Ethereum state on Swarm Track (Viktor)

- bzzeth phase 1 merged
    - PR https://github.com/ethersphere/swarm/pull/1685
    - User Story https://github.com/ethersphere/user-stories/issues/54
- bzzeth phase 2
- agree on simulations
    - in proc sim with 2 types of mock eth clients
    - k8s network test using trinity clients (Rafael)
- devcon talk preparation: https://notes.ethereum.org/To2w7YhwS0yqUMqjYiuWMw

## Research (Daniel)
- Postage stamps SWIP ready for implementation
- what needs to be implemented:
    - SC that will accept on chain payments
    - handle (Go module)
    - forwarding part of the node should be updated
- second part of the postage stamps SWIP (about privacy) is being prepared 

## Network Testing Framework (Rafael)
- no major updates, help with set ups

