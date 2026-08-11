The whole network is based on authentication and encryption. To reach encrypted data you must first perform a calculation for the distributed system; if the authentication is not successful, the encryption of the data changes.

The documentation describes the system as a hydra: cut off one head and two grow in its place.

## Why this exists

Drayker is a way of working where people keep creating, discovering and learning while intelligence carries the rest, and what results reaches the work that produced it. Living Cryptography is how a network that anyone may join stays trustworthy anyway.

The argument in full is on the [manifesto](https://drayker.org/manifesto/); the [economy page](https://drayker.org/economy/) states plainly what contributing here earns and what it does not.

## How the proposal works

Integrated with the distributed processing system, a network request requires a **uPOW** — a unit of work the requester runs so that the network can analyse the request and approve or reject it. Part of that computation goes to the authentication schemes; the larger part goes to the distributed network itself.

If a request is rejected, the cryptographic scheme changes. That is what removes the value of repeating a brute-force attempt: the target you were guessing against no longer exists.

The stated consequence is unusual and worth reading twice. **Under attack, the network receives more work, not less** — and the security algorithms are meant to get stronger, optimizing the cryptographic schemes as they go.

## Role in the system

Living Cryptography is the security layer attached to [Dk Network](https://dknetwork.drayker.org): security is designed as part of the network's computation rather than as a service standing beside it.

## State of this documentation

A design proposal, described in prose. There is no specification of the uPOW, no threat model, and no analysis of what happens to legitimate users under load. Those absences are the honest state of this layer, and each of them is a piece of work someone could take.

All proposed resolutions presented here are solutions to the requirements of Dk and the Drayker platform; only those requirements are final.

## Contributing

Open an issue — a critical reading of the model is as valuable here as an extension of it. Issues small enough for one person to finish carry the `open-function` label and appear on the board at [drayker.org](https://drayker.org/fn/).

Related: [`dk-network`](https://dknetwork.drayker.org) · [`bsdk`](https://bsdk.drayker.org) · [`dk`](https://dk.drayker.org)

Other languages: [Português](./README.PT.md) · [Español](./README.ES.md) — both currently behind this English version.

---

Content licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
