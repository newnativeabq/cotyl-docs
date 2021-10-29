# Timesheet Proof of Contract
More of a decentralized psuedo-anonymous escrow service than anything.

So, there I was, building the first pass, unsexy, Cotyl framework and this app, and I hit a wall.  An important one.  We need to deploy the smart contract and confirm the transactions and API calls needed to interact with it. Else, the architecture may have to change considerably.  

Building a stateless dApp requires that the user brings everything they need with them. We'll assume the user has:

* A cardano wallet
* An email address or discord to communicate with the counter party

That's it.  Right away, we start seeing that actually signing any of the transactions is going to be tricky.  Also, the DAO needs to be able to build a smart contract and deploy it - which may or may not require the DAO itself to have a wallet.  But, first thing's first, let's deploy a smart contract on Cardano...

## The Cardano Node, CLI, and Dandelion
The cardano node is a beast.  A memory hog, takes a ton of space, and syncing is a constant, brutal, thing.  To this end, we'll deploy the node and CLI on a remote instance.  This should be a good test for the framework too, since we don't want to assume that all the nodes will be deployed on the same machine.  MonoRepo -> MultiMachine. Why not.  We're pre alpha alpha here.

**Step 1** On a fresh Ubuntu Server install, setup the Cardano Node (Follow Along with the plutus pioneers program notes).

**Step 2** Get some tADA (test ADA) from the [faucet](https://testnets.cardano.org/en/testnets/cardano/tools/faucet/).

**Step 3** Deploy the contract.

Delayed for the PAB release.  There are some issues with smart contract endpoints and design that are being flushed out.  Marlowe compilation steps also need some work.  We'll revisit later 2021.

References:
[Plutus Pioneer Program Lecture Notes](https://plutus-pioneer-program.readthedocs.io/en/latest/alonzo/aws_node_setup.html)
[VS Code Remote Development](https://code.visualstudio.com/docs/remote/remote-overview)