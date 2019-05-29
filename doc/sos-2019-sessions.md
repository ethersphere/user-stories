# Swarm Orange Summit 2019 team sessions #

## Context ##
The official summit ran from 23rd to 25th of May at Epic Labs in Madrid, Spain. 
The team ran follow up sessions from 27th to 29th of May to delve into detailed discussions
and planning of specific issues.

## Rationale ##
This document is a write up of the sessions which have been running, to document and share its outcomes.

## Monday 26.05.2019 ##
### What ###
Timeboxing of the day and planning
### When ###
10:00am - 10:30am
### Who ###
Swarm core team
Piper Merriam - ethereum python team
### Results ###
Detailed timeboxed planning for the day

### What ###
Chunker refactoring
### When ###
10:30am - 1pm
### Who ###
Swarm core team
Vero Estrada - entanglement codes
[Vero's mate] - entanglement codes
### Results ###
When a file is submitted to the system, the input data stream is then transformed into chunks, encrypted, then hashed and stored. This results in a single root chunk reference of the data.

Another requirement is to have append functionality.

An important design consideration is that the different components that handle the data streams should have symmetric and standardized APIs that would allow the different components to be daisy-chained.
Example: the application of encryption and erasure coding are not necessarily mandatory and could be opted-in by the user. 
Note that this is not the case with the current implementation which is at its current condition unmaintainable.

[Chunker diagram](img/chunker.png)

 * Erasure coding:
Using reed solomon codes, the rationale is that we ask for all chunks, also the erasure code ones to ensure that all data stays alive (due to it being requested -> higher populatiry reduces chance for being GC-d) and to get better QoS by racing the erasure coding alongside the data

 * Entanglement codes
https://t.co/FZY2cCiPW8 - Vero Estrada's thesis
https://www.crss.ucsc.edu/media/pubs/971bbc7371ecf14b158d27cff50523eb025e7148.pdf - Entanglement codes paper

* Use cases
1. Download a file in full, use storage friendly solution -> robust chainable erasure coding

2. Random access -> embedded, entanglement codes, visible to users

3. Traverse separate files separately -> conceal entanglement chain

All three use cases are valid and need implementation. 3.) might be delayed

Reader needs strategy for disambiguation.
The API needs to offer a parameter to be able to choose the strategy.

Create tests to integrate the entanglement package. Simplest is to have simple tests where a file is fed into the stream of components and the result should always be the same (the original file) after any or all components have processed it.

Create a user story (“Recover files”)


### What ###
Push syncing
### When ###
2pm - 3:30pm
### Who ###
Swarm core team
### Results ###
Push and pull syncing work together to get chunks to where they are supposed to be stored (to the local neighbourhood where they belong).
Push syncing verifiably sends the chunk to the NN.

User story:
As an uploader I want to know when my data is retrievable from the network (without me).

Retrievabiliy is assessed by a statistical sampling of the receipts.

Using PSS, we can guarantee that *at least* the **most proximate node** will receive the chunks, **maybe** neighboring ones too.
Popularity is not prioritized for syncing since this is not reliable information.
Push sync is meant to be a kind of interactive process that can signal to the user when the upload was done and is retrievable and that the node can now be safely shut down (safe upload and disappear)

Chunks are being sent directly on top of a pss message to the NN, there’s no Offered/Wanted msg exchange.

Push sync attack vectors - **todo**

Push sync protocol:
Uploader node chunks a file, new chunks gets put into the push sync index in the localstore.
The push sync module picks up chunk from the push sync index and sends the chunk on a pss prox message WITH the uploader node address (leak), and the PSS message destination address is the actual chunk address.
The message handler will pick up the chunk and store it when the chunk is ‘close enough’ to the forwarding node address. It is a node's responsibility to decide if it is itself close enough.
Each node on the way that qualifies stores the chunk and sends back a receipt.
When the uploader node gets the receipt(s) for the sent chunk, it removes the corresponding entry from the push-sync index and inserts it in the GC index.

Difference between pull-sync and push-sync:
Push-sync addresses the use case of a user **upload** of a file, ensuring that its chunks get efficiently distributed to the storing nodes.

Pull-sync tackles chunk syncing from a network point of view: distribute chunks which are relevant to a node based on network topology. This is essential for example for new nodes coming online.

### What ###
Ethereum state on swarm
### When ###
3:30pm - 5pm
### Who ###
Piper Merriam - ethereum python team
Swarm core team
### Results ###
Piper describes his proposal about how to bring ethereum state on swarm.

To minimize risks and maximally explore potential, a multi-stage approach is proposed:

1. Make ethereum **headers** accessible on swarm
2. If this is successful, in a later stage we can think of how to store the actual ethereum **state** on swarm

Swarm can accommodate the needs for these use cases by defining custom hash types and appropriate endpoints for efficient retrieval of the data.

Starting with headers offers a great advantage over immediately tackle the state:
* Low data size
* Less mission critical - the data is available from many places already
* It would be very convenient for ethereum clients to access header data from swarm even if not ALL of the data can be retrieved from Swarm.

It is important to **define clear acceptance criteria**. These acceptance criteria should be very specific and explicit, e.g.
* 60% of header requests succeed
* 80% of the requests should return in x seconds. 

This project could be structured like this:

* Phase 0
Mutual devp2p connection: Just establish a plain devp2p connection between a ethereum node and a swarm node. The protocol could be defined as "bzzeth"

* Phase 1
ETH ----> Swarm:  Send header information onto Swarm

* Phase 2
ETH <------> Swarm: Add query capability on Swarm so that the information can be returned from a Swarm node to an ethereum node.

A very first draft of the API:

* NewHeaders(hash, number),...
* GetHeaders - reqID [hash, ....]
* Headers [reqID, [rlp-header,...]]
* Announce - servesheaders: True/False

Project planning:
* Plan
* ETH reqs
* Swarm reqs
* Future Data
* Future API

This looks like a **very important** use case which can dramatically boost Swarm's visibility and spark widespread interest into the project, let alone create huge potential for attracting substantial funding. Efficient and simple handling of sync data for ethereum clients is an expressed and urgent need of the ethereum eco-systems community. If even the holy grail of storing ethereum's state data on Swarm, an important option and potential solution for the major scalability and usability bottleneck in the ethereum eco-system can be offered.

### What ###
Swarm admin planning
### When ###
5pm - 6pm
### Who ###
Swarm core team
### Results ###
We did some issue cleanup and board grooming.

## Tuesday 27.05.2019 ##
### What ###
Timeboxing of the day and planning
### When ###
10:00am - 10:30am
### Who ###
Swarm core team
### Results ###
Detailed timeboxed planning for the day

### What ###
Pinned content
### When ###
10:30am - 11:30am
### Who ###
Gregor - Datafund
Daniel - Datafund
Zahoor - Datafund
Swarm core team
### Results ###
Specific indexes for pinned content will be created. This allows chunks to be marked as pinned inside Swarm's localstore.

This approach adds pinned content to a Swarm node while integrating it nicely into the existing infrastructure and actually provides pinned content as a permanent feature for the Swarm network. This should be a major improvement in usability as Swarm node operators can rely on the availability of data which they upload locally. Specifically for dApp development this is an important support.

New admin endpoints ("bzz-admin") will be added so that pinned content can be uploaded and managed (un-pin).

Due to the limited availability of the Swarm team, Datafund will provide resources to implement this functionality (Zahoor).

### What ###
Communications and website
### When ###
11:30am - 12:00pm
### Who ###
Datafund team
Swarm core team

### Results ###
Datafund to help provide external support for the redesign of Swarm's webpage.


### What ###
Pull syncing
### When ###
12:00pm - 1pm
### Who ###
Swarm core team
### Results ###
Pull syncing is currently over-complex and difficult to maintain, debug and extend. It should be refactored.

The protocol itself also suffers from unnecessary complexity and design flaws (server driven, intervals dictated by server).

The protocol should be redesigned, a client-driven model where conceptually a client requests the data it wants seems best suited.
However, this client-driven model creates new challenges: The network can be easily spammed by just continuosly requesting the same data. It opens a potential attack vector for malicious nodes which could be trying to take away traffic from storer nodes and serve it themselves by just retrieving data via syncing, caching it and serving it themselves.

Daniel Nagy presents the solution to this dilemma: **Syncing is subject to SWAP**. By having to pay even for syncing, spamming is essentially inhibited. As pull-syncing specifically is about distributing chunks based on the network topology, statistically content-addressed chunks should be synced uniformally to all nodes so the SWAP balances through syncing should cancel each other out; asymmetric loads and balance skews should not occur. However, it would be good to actually create metrics and/or simulations to observe with real data that this is indeed going to happen, in order to not heavily distort and disincentivize nodes to participate if syncing resulted in economical penalty.

This important decision fundamentally changes current thinking about incentivization and at the same time resolves many problems in the context of pull-syncing. Fundamentally it allows any design on top of it. A client-driven model thus seems most appropriate.

This new model will be designed in detail in a further session (Wednesday 29.05.2019).

### What ###
Infrastructure for dApps
### When ###
2pm - 3pm
### Who ###
Dimitry - BeeFree
Swarm core team
### Results ###
Dimitry outlines what seems to be the outcome of multiple conversations among different projects using Swarm from a dApp development point of view.
He describes a general usage pattern where user data is basically stored under a ENS name (e.g. "myname.eth").
Then, the technical stack could look like:

1. Invitation layer - Service Contract, Authorized and reviewed. Static hash libs on Swarm
2. Erebos - Javascript app specific application layer (BeeFree scripts) - e.g. chat core libs, chat DB
3. Multimedia DB
   * Posts
   * Data
   * [not legible from picture of board]
4. Frontend (React code + JS)

    user.beefree.ens
          |
      mutable hash
          | 
      static hash

User data:
         user.ens
     Data structure:
       |-  BeeFree DB
       |-  Chat DB
       |-  Datafund DB
       |-  YourApp Data



The Swarm team recognizes the great potential of such an architecture: it essentially constitutes a promise to get rid of data silos of the current web architecture and allow to put users in control of their data.

Users would maintain all their data in their own namespace, while different applications can access this data. For this vision to be most successful, privacy aspects must be consideredas well as technical challenges about how to access data. Speficically, the user should be able to selectively grant and revoke access to portions of data for each individual application, while applications should be integrated into a workflow where they need to request permission(s) to the user for accessing their data. This is a major usability and technical challenge which requires extensive work and multilateral collaboration. Therefore, such a vision can only be interpreted as a long-term undertaking which needs dedicated thinking, research and implementation.

The Swarm team fully embraces this vision as Swarm can be a major enabler for it. Nevertheless, the most it can contribute to this vision in the short-term is to mature as a platform and provide stability and reliability for its most basic and imminently required use-cases, which is storage and basic messaging.

The Swarm team asked Dimitry how it best could help in the short-term to support projects. Dimitry explains that at the moment a javascript developer would be most needed from their side to contribute to this architecture.

The Swarm team concludes by stating that it currently can not contribute this resource, clarifying that it doesn't and probably shouldn't take on responsibility for the implementation of javascript upper level library - at least not for now. Nevertheless the team emphasizes its willingness to support projects building on Swarm in any way possible in the current scope and capabilities of the organization.

### What ###
Release planning
### When ###
3pm - 4pm
### Who ###
Swarm core team
### Results ###
The release should have a couple of days of "freeze" so that we don't cram last-minute code into a release.
1 week looks like ideal but we envision 1 day strictly and possibly 3 days realistically for now.

* Repo split - 3rd of June - Needs 2 days of work
* Release testing (1d)
* Update repo in docs
* Revise repo split document (CI / CD)
* Fix p2p + from-is + duplicate deliveries
* Update sync subscriptions
* @MainFrame about bootnode and ask enode address
* Follow up on results of pure retrieval tests
* Sufficient documentation for our target audience

Ambitions
=========
* Add implementation for lookahead in the HTTP downloader 

### What ###
Board grooming and issue cleanup
### When ###
4pm - 5pm 
### Who ###
Swarm core team
### Results ###
Updated board and issues.

### What ###
Module documentation
### When ###
5pm - 7pm 
### Who ###
Swarm core team
### Results ###
Documentation at https://hackmd.io/SypHYi42T4CuCwIuJB86qQ?both
