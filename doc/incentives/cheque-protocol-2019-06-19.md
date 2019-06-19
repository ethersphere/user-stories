Swap exchange protocol
=======================

Meeting 19th June 2019

Attendees:
* Viktor Tron
* Fabio Barone
* Diego Masini

Goals:
* Initial swap exchange protocol design
* Identify touch points between go-code and smart contracts


We will have to work iteratively on the development of the protocol and the integration of the smart contracts.
First, to reduce complexity, and also to advance peacemeal in order to cover future functionality which is not yet implemented (e.g. Waivers, see SW3 paper).

## Basic protocol ##
The first iteration of the protocol can be very simple.
There will be a devp2p with a simple message exchange:

* The creditor sends a `ChequeRequestMsg` when it detects that a remote peer has crossed the payment threshold.
* The debitor responds with a `SendChequeMsg` which contains the actual cheque
* The creditor cashes in the cheque right away

![Simple Swap exchange protocol](../img/cheque-exchange-protocol-simple.jpg?raw=true "Simple Swap exchange protocol")

In future iterations the cheque may not need to be cashed in immediately, but these alternative flows are not specified yet and we will address them later.

Both participants store their **last cheque** to each other respectively. See *cumulative total* in chapter 2.1 of the SW3 paper.

The connection point to the smart contracts is on the creditor side:
When the cheque arrives, it calls `submitCheque` from the `SimpleSwap` contract.

So we need to generate the `go bindings` from the smart contracts with `AbiGen`, and then call the appropriate method in these bindings.

When the creditor sends the `ChequeRequestMsg`, after accounting detected the crossing of the payment threshold, it does **not yet** reset the balance to zero. When it receives the `SendChequeMsg`, it will reset the balance to zero.

This allows to still exchange services with the debitor node until the disconnect or ignore threshold. If no cheque arrives and that threshold is reached, the peer will be dropped/ignored. In the first iteration, simplest is to just drop. We can elaborate on what is the most appropriate strategy later.


## Other considerations ##

* We need to setup the automatic chequebook deployment, so that on node boot the contract is deployed. Check legacy chequebook code on how this is done.
* Possibly enable that via flag
* Also check that when deployed:
  * check it exists
  * check checksum


Some terms from the legacy code:
* Autodeposit:  Rules for topping up
* Autocaching:  Rules for cashing out
