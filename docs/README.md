# Living Cryptography

> Research into adaptive authentication and encryption.

Living Cryptography investigates how authentication, computational work and changes to encryption state might cooperate in a distributed network. Its proposals need an explicit threat model and reproducible evaluation.

An open network must handle compromised credentials, hostile requests and ordinary mistakes while keeping legitimate access usable.

## The research question

The original proposal connects access to encrypted information with a unit of computational work, called **uPOW**. Part of that work would support authentication and part would contribute to the distributed system. It also explores changing encryption state after a failed authentication.

The central question is whether these mechanisms can provide useful protection at an acceptable cost. A failed authentication may be an attack, a lost credential or a routine mistake. The design must distinguish the consequences of those cases and prevent an attacker from using the response itself to exhaust resources or deny access.

## What an evaluation should establish

A threat model should identify protected assets, attacker capabilities, trust assumptions and the limits of recovery. A specification should then explain how uPOW is checked, when encryption state changes, how authorised users recover access and how much computation and coordination each step requires.

An experiment should measure attack cost alongside legitimate-user latency, availability and resource consumption. It should also examine compromised keys and information already disclosed: changing future access conditions cannot retract a copy an attacker already obtained.

The earlier hydra metaphor describes an aspiration for adaptation. Whether hostile traffic can produce useful work or improve protection is a hypothesis to test, with failure cases reported alongside successful results.

## Where it fits

[Dk Network](https://dknetwork.drayker.org) needs authentication and secure communication across different operators and computing tiers. [UID](https://uid.drayker.org) needs credential and delegation mechanisms, [OSDK](https://osdk.drayker.org) needs a way for devices to join within explicit permissions, and the [veto chain](https://uid.drayker.org) needs the channels between the nodes that verify and relay its entries to be authenticated end to end. These relationships define requirements for the research; they do not establish the security of a proposed mechanism.

## First contributions

A useful starting contribution is a threat model for one access flow, followed by a small reproducible experiment comparing legitimate access, accidental failure and hostile requests. The public documentation currently describes the idea in prose; uPOW, recovery behaviour and the response to load still need specifications and analysis.

## Participation and sources

This repository develops a proposal through public documentation and review. Read the [contribution guide](https://github.com/draykerdk/.github/blob/master/CONTRIBUTING.md) and [current governance](https://github.com/draykerdk/.github/blob/master/GOVERNANCE.md), or find a bounded contribution on the [open-functions board](https://drayker.org/fn/).

Part of [Drayker](https://drayker.org). Content licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
