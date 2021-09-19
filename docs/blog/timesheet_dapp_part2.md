# Timesheet Proof of Concept
Vincent Brandon
2021-09-18

A picture is worth some number of words.  So we'll look at a picture of the pre-alpha node architecture.  We'll go through its main components, structure, and design considerations.  Then we'll get the DAO set up.  Much of the Cotyl framework won't be shown.  

See the full repository [here](https://github.com/newnativeabq/cotyl-demo-timesheetdapp)

## A Dual Interface Single Message-Route Node
For this pass, we'll design our nodes as router with transform procedures and an ingress and egress interface set.  Data comes in through the in interfaces and goes out the out interfaces.  The interfaces need not be the same, or in sync.  

![Node Architecture IRE](https://github.com/newnativeabq/cotyl-docs/blob/main/docs/examples/images/early_node_arch_ire.png)

The set of ingress and egress interfaces need not be equivalent. This should allow for interfaces to be domain specific in messaging/response patterns.

For example:
* Ingress Asynchronous Web
* Egress Synchronous CLI

In this model, a Route through a node then is defined:

egress(transform(ingress message))

The entry point to the node routes can be at the ingress interface level.  If we define a router R with a set of routes r.T, then the ingress interface call is simplified:

if message valid: R(m)

Where R understands message context and routes accordingly.  This works in practice IFF messages are distinct on every route in every node. This is a considerable constraint, but makes things much cleaner as any given message type can ONLY have one route through a node.

## OK, What's it look like in the framework?
Framework Directory Structure:
Root
main.py
-- contracts
-- nodes
-- templates

In nodes, we define our nodes:

-- nodes
--      node_<nodename>.py

e.g.
```python
# Query Chain Node
# Interfaces with exterior Dandelion API services
from cotyl.node.node import Node
querychain = Node(
    name='node_querychain'
)
```

Then we register the node with the dApp DAO

```python
# Building the TimeSheet DAO
from cotyl.dao.dao import DAO
from nodes.node_querychain import querychain

dao = DAO(
    nodes = [
        querychain,
        ]
)
```

### Why Register?
The DAO class is more than an orchestrator.  It will calls setup methods and generate unique IDs for each node.  We can get really crazy with validation (hashing the source code of the node since it's in its own file).  Having a unique ID is also nice for host allow/deny instantiation down the line.  We won't be building that in this time, but once we are thinking in the 'code has a signature' mindset, we can do some interesting things to protect DAOs from tampering.

### Visualization
The whole point of a Visual DAO framework like Cotyl is to 'see' the graph of these nodes.  We haven't introduced the interfaces or any routes yet, so there won't be edges buuut:

```yaml
digraph  {
8760012912836;
8760011668378;
8760011668390;
8760012219052;
}
# 4 unique IDs, one for each node, in DOT format.
```

No pretty visuals just yet.  Graphing four equally spaced dots is great, but we'll leave the pretty picture for when things are wired up.

## Next Steps
Part Two Done!  We have a node architecture to work with and some very onerous interfaces to abstract away from the framework user.  In part 3 we'll build the interfaces and see what a route looks like!