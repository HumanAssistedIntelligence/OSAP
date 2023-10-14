# Open Source Agent Protocol: (OSAP)

The Open Source Agent Protocol (OSAP) facilitates an open standard that allows AI automated agents and APIs to streamline, validate, and formalize their interactions. It is designed to encompass a range of agents, including humans, bots proficient in natural language processing, and APIs. The goal is to enable heterogeneous multi-agent collaboration.

## Main Components:

 - Schema: Lays the foundation by providing a structured format for agent interactions.
 - Schema Validation: Acts as a quality check, ensuring all interactions strictly adhere to the established schema.
 - Process State & Step Verification: This component allows agents to authenticate and cross-check the current state and specific action of another agent within a deterministic dialogue. (see notes below)
 - Reference Library: This serves as a centralized resource, offering implementations of necessary functions across various languages, including Rust.
 - Reference Clients and Servers: These are representative HTTP servers, equipped to deliver the anticipated functions vital for the seamless interaction of agents.


## Key Management:

Every user on HAI.AI is assigned a unique public/private key pair. While these keys have encryption capabilities, within OSAP, their primary function mirrors PGP's or JWT's signature functionalities. Dialog steps can be authenticated using a chain of these signatures. It's important to note that, unlike blockchain, the objective isn't to synchronize a unified state across all participating systems. The emphasis is on confirming identity, content integrity, and data reception acknowledgement.

### Centralized Key Registries:

A central public key repository is essential. HAI.AI will manage one such registry, with root certificates from individual hosts serving as proof of key authenticity.

### Key Management Implementations of OSAP:

 - Public Key Server: It will host and validate public keys.
 - Agent Server: This will be responsible for key generation, public key sharing with key servers, public key validation, processing inbound messages, and dispatching outbound messages.

Where the protocol can leverage the existing SSL ecosystem, it should.


## Implementation Goals


OSAP is permissively licensed, with reference implementations available in Rust, Go, Python, and Typescript. Depending on the complexity, there might be native versions in each language, or it might draw upon a Rust library supplemented with wrappers/WASM for other languages. While Http2 is the anticipated protocol, alternatives like GRPC may also be explored in the reference implementation.


# Notes

## Deterministic Dialogs vs. Informal Dialogs:

Dialogues between bots (or between a bot and a human) can be broadly categorized into two types based on their structure and purpose: deterministic and informal.

 - Deterministic Dialogs: These are structured conversations where both parties, especially when at least one is a bot, need to mutually agree upon a set sequence of steps to achieve a specific goal or complete a task. Every step within this dialogue is predetermined and requires explicit consent from the involved parties before proceeding to the next. This is what we refer to as the "transactional process." It doesn't necessarily have to be financial; any interaction that follows a strict sequence, from setting up a meeting to signing a digital contract, falls under this category. The primary advantage of deterministic dialogs is that they ensure clarity, consistency, and mutual agreement at every stage, eliminating ambiguities and potential misunderstandings.

 - Informal Dialogs: In contrast, informal dialogues are open-ended conversations without a predetermined sequence or set outcome. They are more fluid and can change direction based on the inputs from the involved parties. Examples include casual chats or brainstorming sessions where the conversation's path is not strictly defined.

In the realm of AI and bots, deterministic dialogs are crucial, especially when tasks or decisions are involved that require mutual agreement and verification at each step. It ensures both parties are on the same page, enhancing the reliability and efficiency of the interaction.

## Legal Framework for Agents as Authorized Representatives

For OSAP to be functional, users must empower their bots to make decisions on their behalf. These decisions might encompass financial choices, commitments ranging from everyday tasks to legally binding contracts. The automation of such decisions will inevitably introduce a host of new legal challenges.
