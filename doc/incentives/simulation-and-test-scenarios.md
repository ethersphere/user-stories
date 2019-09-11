# Simulation and test scenarios #

For incentives, we need to set up a series of new testing scenarios. Running smoke tests alone is not enough. Apart from tests to verify the correct execution of the code, we will need to experiment, observe and analyze the behavior of nodes and network with different prices and thresholds. Due to the nature of such behavior as an emergent property of the network as a whole and of the interaction between nodes, such tests will only be meaningul if executed on a deployed network/cluster.

Also, some of the tests will need the presence of a simulated blockchain. The network testing track is already setting up the framework which will allow such testing by providing infrastructure accordingly (e.g. Ganache as a blockchain backend).

We can thus roughly distinguish between:
* Simulations
* Integration tests
* Experimentation tests

This document aims to collect the specification for the set of needed testing.

## Simulations
Simulations run as part of the go unit testing suite. They spawn a configurable number of nodes in a single process and then can run individual interactions. They are mostly useful to verify that a change in the code does not break the integrity or correctness of the system, and thus should be run every time the code changes. They are not of much use for experimentation nor for integration, as they should be focused on running quickly so as not to significantly extend the running time of the complete test suite.

### Accounting correctness
This is a test well suited for a simulation. At no point after a change should the correctness of accounting be broken.

**Description**: Launch _x_ nodes, upload a file, sync, then download from different nodes, and check balances.  
**Expectation**: All balances should be symmetric with each other (`balanceA == -balanceB && balanceB == -balanceA`) and at least _some_ of them should be non-zero.  
**Restriction**: All nodes should have SWAP enabled and a valid chequebook smart contract deployed. All thresholds should be equal and all nodes must be on the same network. Balances should be kept below the payment threshold so no cheques are emitted.  

### Cheques correctness
Trigger multiple threshold crossings (and thus multiple cheque emissions).

**Description**: Launch _x_ nodes, upload a file, sync, then download from different nodes.  
**Expectation**: An expected set of nodes has (multiple) cheques. The cumulative amount of cheque values and balances match. For every pair of nodes _A_ & _B_ the last received cheque to node _B_ from node _A_ should match the last sent cheque from node _A_ to node _B_.  
**Restriction**: All nodes should have SWAP enabled and a valid chequebook smart contract deployed. File size should be big enough to trigger cheque emissions, so fixed (non random) data and size should be used. Use snapshot.  

## Integration tests
Integration tests are tests that need to run as much as possible with all needed system elements, such as:
* Backends (blockchain)
* Oracles

Still, they are used mainly for making sure that everything works correctly, and less so for experimentation. They should be able to run with a predefined configuration and setup and produce predictable results for verification of correctness. They should run as part of smoke test suite in the future. If they fail, they signal a problem with the code.

### Happy-day scenario
This is the minimal integration test. It runs with a blockchain and a fixed oracle. It makes sure that with a fixed set of values, all is OK.  

**Description**: Deploy x nodes, a blockchain and oracles. Upload a file, sync, then download from different nodes.  
**Expectation**: No errors (no need to check for values, the *Accounting correctness* simulation already did this)  
**Restriction**: All nodes should have SWAP enabled and a valid chequebook smart contract deployed.

### Failure test
Test for error scenarios in relation to blockchain and/or oracles.

**Description**: Deploy x nodes. Test different error scenarios: no blockchain and/or no oracle, , wrong addresses, malfunctioning oracles (if makes sense), etc.  
**Expectation**: All error scenarios are handled in predictable and expected ways.  
**Restriction**: None.

### Existing chequebook
Test that an existing chequebook is indeed loaded if provided.

**Description**: Deploy x (small amount) nodes. Deploy chequebooks. Upload file, sync, download. Shut down one node. Restart it with deployed chequebook.  
**Expectation**: The deployed chequebook is loaded. Check integrity of the chequebook.  
**Restriction**: This test may make more sense if there has been some interaction on the chequebook which is being reloaded (a/some cheque, cashing in, etc.)

## Experimentation tests
These tests should be able to experiment with values and observe/analyze the behavior of nodes. They should only be triggered manually. They may add instrumentation (Grafana boards, tracing, etc.) in order for better observability. They may well be a special set of the same integration tests but with a different configuration, but we conceptually separate them for better identification of the testing tasks needed.

### Change MessageToHoney price
Change this price and observe network.  

**Description**: Deploy x nodes, blockchain and oracles. Set a specific price for messages. Manually upload files, sync, observe.

### Change HoneyToMoney price
Change this price and observe network.

**Description**: Deploy x nodes, blockchain and oracles. Set a specific price in ETH. Manually upload files, sync, observe.

### Change prices on the fly 
This is probably just the same as the above tests (which may be interesting to be run individually though). Change prices on a running network and observe.  

**Description**: Deploy x nodes, blockchain and oracles with an initial value. Manually upload files, sync, observe, but also change prices on the fly.
