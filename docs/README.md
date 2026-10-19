# Living Cryptography

> Research into adaptive authentication and encryption.

Living Cryptography investigates how authentication, computational work and changes to encryption state might cooperate in a distributed network. Its proposals need an explicit threat model and reproducible evaluation.

An open network must handle compromised credentials, hostile requests and ordinary mistakes while keeping legitimate access usable.

## The research question

The original proposal connects access to encrypted information with a unit of computational work, called **uPOW**. A smaller part of that work supports authentication; the larger part goes to the distributed system itself, so security is part of the network's computation rather than a service standing beside it, and under attack the network receives more work, not less. It also explores changing encryption state after a failed authentication.

In the design, a specialised AI authenticates each request, the scheme aims to resist quantum computation, and the network behaves like a hydra: a failed attempt reconfigures the encryption, an attack makes the network stronger, and the work spent on authentication also helps it process and move data.

The central question is whether these mechanisms can provide useful protection at an acceptable cost. A failed authentication may be an attack, a lost credential or a routine mistake. The design must distinguish the consequences of those cases and prevent an attacker from using the response itself to exhaust resources or deny access.

In the design, a failed or violating request leads back to the identity that made it, its [UID](https://uid.drayker.org): the holder is informed of what happened and given steps to resolve it, which is how a lost credential or a mistake is told apart from an attack. The network learns from attacks, removes compromised nodes and turns the computation an attacker spends into stronger encryption.

## What an evaluation should establish

A threat model should identify protected assets, attacker capabilities, trust assumptions and the limits of recovery. The evaluation should also treat compartmentalisation, operation with isolated parts, detection of anomalous behaviour and fault tolerance as requirements, and show how each holds under that threat model. A specification should then explain how uPOW is checked, when encryption state changes, how authorised users recover access and how much computation and coordination each step requires.

The threat model has to include adversaries that try to influence, infiltrate, capture, block, fragment or destroy parts of the network, and powerful actors that may treat encryption and distributed communication themselves as a threat. One target property comes from the design: an attacker holding a valid identity, even with quantum computation, should reach only what that identity's access level allows, and no Dk process should hold permanent access to everything. The evaluation also has a limit of its own: protection must not turn legitimate criticism, dissent or independent audit into suspects.

An experiment should measure attack cost alongside legitimate-user latency, availability and resource consumption. It should also examine compromised keys and information already disclosed: changing future access conditions cannot retract a copy an attacker already obtained.

The hydra names the intended behaviour: a failed attempt reconfigures the encryption, and an attack gives the network more work and stronger protection. Whether hostile traffic can produce useful work and improve protection is what the research has to establish, with failure cases reported alongside successful results.

## Where it fits

In the design, Living Cryptography is the first access layer of both networks of [Dk Network](https://dknetwork.drayker.org). A request is authenticated on the public interaction and testing network first; if it goes on to the main network, Dk authenticates it again, linked to that first approval. While a request is served, the requester's bandwidth relays other requests and its computation helps the network's work and the change of encryption state at the access layer, and each request also helps serve requests from two other nodes. Nodes store and relay what they carry while being authenticated continuously, so the whole works as a distributed secure channel. The same mechanism runs from the base of every module to every layer: a module that the network as a whole does not hold valid cannot take part.

[Dk Network](https://dknetwork.drayker.org) needs authentication and secure communication across different operators and computing tiers. It also requires data that leaves a device to circulate fragmented and encrypted, unreadable to whoever operates the machine that holds it; cryptography works as the skin of the network. The design also asks for protection where there is no direct connection to the wider network: a few nearby nodes should be able to validate what they relay, so a local mesh or a remote site stays trustworthy until it reconnects. [UID](https://uid.drayker.org) needs credential and delegation mechanisms, [OSDK](https://osdk.drayker.org) needs a way for devices to join within explicit permissions, and the [veto chain](https://uid.drayker.org/#the-veto-chain) needs the channels between the nodes that verify and relay its entries to be authenticated end to end. These relationships define requirements for the research; they do not establish the security of a proposed mechanism.

## First contributions

A useful starting contribution is a threat model for one access flow, followed by a small reproducible experiment comparing legitimate access, accidental failure and hostile requests. The public documentation currently describes the idea in prose; uPOW, recovery behaviour and the response to load still need specifications and analysis.

The design already sketches the uPOW, and that sketch is the specification's starting point. At each connection port, functions wait to be executed. An identity runs one and receives a key that entitles it to a single request, and receiving the answer requires a further computation several times larger than the resources the answer uses. The work combines a Boolean calculation with a specialised AI that authenticates the request. Every function carries a verifiable hash and history, so a connection built from altered base modules cannot produce valid keys. A specification has to state these inputs, the cost ratio and how each step is verified.

## Participation and sources

This repository develops a proposal through public documentation and review. Read the [contribution guide](https://github.com/draykerdk/.github/blob/master/CONTRIBUTING.md) and [current governance](https://github.com/draykerdk/.github/blob/master/GOVERNANCE.md), or find a bounded contribution on the [open-functions board](https://drayker.org/fn/).

Part of [Drayker](https://drayker.org). Content licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
