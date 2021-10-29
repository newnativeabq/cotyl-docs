# TimeSheet More Invoicing POC with Cotyl
We continue building the Cotyl proof of concept system.  The title may be false advertising and we're really building a dectralized invoicing and payments system, of which a timesheet is just one type of invoice.

Today we'll focus on the DAO Network.  An issue that arises with monorepo -> multimachine is network and service discovery, routing, and more that occurs when you can't be sure which nodes are deployed on which machines in who knows what kind of network.  While this POC can't answer all the edge cases, we can say that a DAO defined network and router is a decent option.  Ideally, if any node is deployed the implicit DAO network node provided by Cotyl be a good starting point to more complicated deployments as all the internode, internetwork, can be handled centrally (not centrally like a central server, but by the framework itself) via Connection metadata.

And here's where we stop.

Looking at [Gnosis Safe](https://gnosis-safe.io/), an amazing amount of infrastructure can be built on top of a few oracles and a multi-signature wallet.  

Running a DAO from such a a single or set of multi signature wallets is possible, though limited.  This is the basis, however, of treasuries, a central bank, or payroll initiative.  The network is not secured, nor is it P2P.  Having the ability to download the application standalone or have it hosted is a massive boon, though network denial of service, bandwith rate limiting, and other issues may arise.  

We've already demonstrated that at the network level, if applications (nodes) are configured properly, traffic can be assured.  Data management and communication, running DAO-specific side chains, and more is possible if a VPN can be accessed by members of the DAO.

And here's the pivot. From a monolithic application framework to a P2P VPN with wallet integration services capable of running arbitrary docker containers bound to a proxy where all traffic can be monitored by the Cotyl platform and DAO participants.  Whether a DAO has external internet access or all entities are entirely hosted within, which nodes can see WAN traffic, and which are limited to VPN internal traffic should be possible with a proxy service and application manager or similar. Further, edge connection between nodes can be defined up front as firewall rules and confirmed in traffic logs.  No need to express complicated connection metadata if that's handled at the deployment infrastructure level.

Back to the DAO Network, only this time as a platform for applications to connect to each other.