# Open Source Agent Protocol: (OSAP)

OSAP exists to create an open protocol for AI automated agents and APIs to verify and formalize interactions between agents (humans, natural language capable bots, and apis). OSAP consists of a schema, schema validation, process (state and step) verification.


Process state and step means that one agent may want to verify the state of another agent at a certain time and within a certain step of a deterministic process. A deterministic dialog, instead of an informal dialog, is a process bots agree to follow for a specific transaction.

For every user of HAI.AI a public/private key pair is created. The key pair can be used to encrypt, but its use in the OSAP protocol is more like PGP’s or JWT’s signatures. The signatures are chained so that the order of a dialog’s steps can be verified. Unlike blockchain there is no goal of creating one large shared state that is consistent across all participating transactional systems. Every host may have a different understanding of the state of data. The protocol only verifies the identity, content, and reception of data.

Central registries of public keys will need to be established. HAI.AI will host one. The proof of the public private key will be satisfied, like the internet, by root certificates by each host.

So this means two implementations of the protocol are

Public key server - host public keys and verify a public key.
Agent server - generate keys, share public key with key servers, verify a public key, accept inbound messages, send outbound messages.

Where the protocol can leverage the existing SSL ecosystem, it should.

The OSAP protocol will be open source. It will consist of reference implementation in Rust, Go, Python and Typescript. If simple enough there can be a native version in each, or it may rely on a Rust lib with wrappers/WASM in other languages. Http2 is the expected protocol, but a binary protocol like GRPC may also be developed in the reference implementation.

https://github.com/HumanAssistedIntelligence/OSAP


Legal Framework for Agents as Authorized Representatives
For OSAP to work, people need to be able to authorize their bot to make certain decisions for them. More than financial choice, a decision may involve commitments. A commitment could be as simple as promising to do dishes, to a meeting at a date and time, to a legal contract. Automating will create many new legal issues.
