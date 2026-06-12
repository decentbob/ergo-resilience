# Ergo: Notes on Resilience
### decentralized, not unorganized

**Contents**

1. [Why resilience](#1-why-resilience)
2. [Technical resilience](#2-technical-resilience)
3. [Continuity resilience](#3-continuity-resilience)
4. [Economic resilience](#4-economic-resilience)
5. [Governance resilience](#5-governance-resilience)
6. [Adversarial resilience](#6-adversarial-resilience)
7. [Growth as resilience](#7-growth-as-resilience)
8. [The ethos as backstop](#8-the-ethos-as-backstop)
9. [Synthesis](#9-synthesis)

---

## 1. Why resilience

> "Because the tools we are building may not benefit you today, make no mistake, they may be the lifeboat of tomorrow."
>
> *Ergo Manifesto*

The [Ergo Manifesto](https://ergoplatform.org/en/blog/2021-04-26-the-ergo-manifesto/) is clear about why Ergo exists. It has a stated purpose: ergonomic money for ordinary people, built to be private, permissionless, secure. Oriented to the long run rather than the next market cycle. The Manifesto calls this Ergo's Social Contract. A protocol which intentionally violates these principles should not be called Ergo.

For a decentralized blockchain, resilience is the priority that every other priority depends on. The most advanced cryptography counts for nothing if the system collapses, gets captured, or quietly dies. A chain like this exists to be the thing people can still rely on when other systems fail. So its first duty is to still be there, and still be itself when that day comes.

There are two ways Ergo can fail. One is to stop (halted chain, successful attack, critical bug). The other is to keep going while ceasing to be Ergo (captured, speculative casino, ghost chain).

**Staying decentralized takes work.** Left alone, an open system re-centralizes. Around whoever is most capable, the entity that legally signs things, the pool with the most hash, the person keeping the lights on. None of that requires bad intent. It is simply where responsibility pools when it is not deliberately spread out.

The Manifesto understood this:

> "Any party's social leaders, software developers, hardware manufacturers, miners, and funds need to avoid central points of failure."
>
> *Ergo Manifesto, Decentralization First*

That is an organizational instruction, the Manifesto doesn't say how. This document is an attempt at the missing how. Which organizational practices actually keep Ergo decentralized, secure, funded, and alive, while staying aligned with its ethos. An unorganized system does not stay decentralized for long. It re-centralizes quietly.

Two habits follow. Resilience should always be weighed and impact on it stated explicitly for major proposals. And Ergo should be audited honestly for its central points of failure.

---

## 2. Technical resilience

> "Ergo is committed to best security practices. This is a continual commitment to prevent network attacks, preserve privacy and protect on-chain value."
>
> *Ergo Manifesto, Open Permissionless and Secure*

For a chain built around secure money for the long term, security is the foundation. Not only for the protocol, but also for the infrastructure on top of it.

**Security budget.** Ergo is GPU mined with an ASIC-resistant algorithm, which keeps mining open to ordinary GPU owners. With block reward reaching its floor of 3 ERG (until 2045) and price falling, the hashrate has dropped substantially. In theory that makes Ergo cheap to attack, in practice an attack is not profitable. Exchange liquidity is too low to cash out a large double-spend and CEXs would freeze withdrawals quickly. But that's a weak guarantee. Supplements can help decouple the budget from emission and price: fees and storage rent (currently low relative to block rewards), FIMO and merge mining (non-ergo rewards, proposed). 

**Concentration points.** ASIC resistance is meant to keep block production in many hands, but it also lets a large AI or cloud datacenter point idle GPUs at Ergo and pull them away just as fast. Datacenters are also more efficient and outcompete small miners. Margins shrink or get negative. That makes hashrate more volatile and a majority easier to build. Pool concentration is a current form of the same problem. A single pool that mines a majority of blocks carries that weight in soft-fork voting and can delay or drop valid transactions (transaction policy or stale configuration). Lithos can help here if enough miners care to switch. Cross-chain bridges have separate exposure and are one of the most frequent targets in the industry. Rosen concentrates significant value behind a guard-set multisig with a collateralized watcher layer reporting cross-chain events.

**The protocol over time.** Ergo's signatures use the same elliptic curve as Bitcoin. Large quantum computers would break them, though the POW itself would survive. The path is a future hard fork, with some groundwork being laid through hash based, curve free primitives. A chain meant to last has to evolve its cryptography ahead of the threat.

The same long view also applies to core code, keep it simple and auditable. High complexity, like sophisticated privacy constructions, lives out of the core where bugs are not as severe. Resilience also wants more than one independent node implementation, so no single codebase is a chokepoint. Alternative implementations are in development. Long term shared specification should be used, instead of treating the reference client as the source of truth.

**Emergency response.** It's a coordination problem. Shipping patched clients that operators adopt, while exchanges pause withdrawals and pools decline exploit transactions, has to happen quickly. Still, emergency merge authority has to stay with the few people that can judge a consensus-critical fix.

**The layer above the protocol.** Users don't touch the protocol directly, they reach Ergo through nodes, explorers, indexers, APIs, oracles, wallets, front-ends. Many dApps depend on an off-chain executor or bot. The base can stay perfectly healthy while Ergo is hard to use because that layer has degraded. Much of it is public-goods infrastructure run by a single operator or sitting on a centralized web2 provider, and most of it is under-incentivized. An attack on this layer, or simply neglect, can stall the network without touching consensus. The InfraDAO is the community effort now meant to fund and coordinate the infrastructure.

**Practices to uphold.** Have a security disclosure channel watched by more than one person, an agreed incident response process, and a maintained contact list for pools, exchanges, and major operators. An open question is who owns the protocol specification and conformance suite, so having multiple clients is a strength and not a split risk.

---

## 3. Continuity resilience

> "All actors whose absence will disrupt the system's function need to have contingency plans in the event of a disruption."
>
> *Ergo Manifesto, Decentralization First*

Ergo's protocol research, much of its reference-client review and merge authority, a good deal of its technical coordination, much of its emergency judgement, and ownership of main community channels currently run through one person, Kushti (Alexander Chepurnoy, co-founder of Ergo). He has rare and deep expertise and has built his life around the project. That concentration is Ergo's greatest strength and its most significant resilience risk.

The manifesto addresses this directly. Actors whose absence would disrupt the system need contingency plans.

**Continuity is different from replacement.** Surviving someone's absence doesn't require an identical replacement. It requires that the system keeps functioning without them. 

The first part runs through Kushti today but does not have to: release mechanics, review and merge of code that is not consensus-critical, acting as the central communications hub and first responder, custody of critical keys and accounts. None of it needs irreplaceable expertise. All of it can be distributed to people who exist, through documentation, named backups, and shared authority.

The second part is hard to substitute: deep protocol research and novel design. That part shrinks only slowly through years of onboarding and mentorship.

Kushti is the clearest case, but the principle is general. Anyone whose absence would disrupt the system needs named and documented backup, so that no single exit stalls the project.

Of course distributing responsibility needs people with the skill and willingness to take it on. Ergo may not have enough of them today. Making the core less dependent on one person and growing the base of contributors are the same goal.

**The environment.** A hostile or high conflict environment drives people away and burns them out. Outsiders judge a project by how its community behaves, reputation for drama should be minimized. Welcoming and retaining people is as important for resilience as recruiting them.

**Practices to uphold.** List the functions that can be distributed now with named backups and documentation. Publish who holds merge right, key custody, and critical accounts. The structures should be public, not only known to insiders. Where possible put keys and accounts under multisig or secret-sharing (already established for community treasuries and many contract updates).

---

## 4. Economic resilience

> "The Foundation treasury is set to 4.37% of the total coins mined, and it isn't possible to change the core elements of token economics further."
>
> *Ergo Manifesto, A Note On Token Economics*

A project can have good governance and still fail because nobody can afford to keep building.

Ergo has a fair launch without premine or VC allocation. The Foundation treasury is fixed at 4.37% of total supply. That's a real strength for decentralization, but also means funding is limited.

The price has been in a long decline and developers keep working with little financial incentive. This is the environment where resilience is actually tested. A system that only functions in a bull market is not resilient, it's lucky. Much of the work is donated, the people who keep building largely came for the principle rather than payout. But that only stretches so far. Commercial infrastructure runs on the prospect of profit, which is low with few users. 

With its funds depleted, the EF is effectively a legal signature holder. Dev or bug bounties, supported research, professional audits, paid marketing, independent integrations and infrastructure upkeep all need funding. Core development funding now runs through the community DevDAO, and infrastructure through the InfraDAO. Where work cannot pay for itself, it has to be sustained through donations, raffles and crowdfunding.

Transparency should be non-negotiable. Funds being visible on-chain is not the same as their use being legible. A public foundation like the EF, and any DAO that holds community money, should keep an up-to-date record of what was funded, how much, to whom, and what it produced. Transparent spending is a resilience mechanism, it makes capture harder and builds trust that attracts contributors. Several DAOs currently use [Paideia](https://app.paideia.im) for transparent spending and voting.

**Practices to uphold.** Transparency must be upheld, but doesn't resolve the funding problem. There has to be coordination about where funding has the most impact and how to keep public-goods infrastructure running through a long bear market. Donations should be collected before missing funding breaks vital functions.

---

## 5. Governance resilience

> "All code for the core protocol must remain fully open and transparent. Every line should be fully auditable and transparent, preventing manipulation and building decentralized resiliency."
>
> *Ergo Manifesto, Open Permissionless and Secure*

Governance in Ergo is mostly implicit.

The one piece that is explicit and works is protocol change through miner signaling. Soft-forks activate by miners voting over a defined window. Miners consent to consensus changes. The concentration noted in 'Technical resilience' also carries directly into the vote.

Other pieces that already work are the [EIP process](https://github.com/ergoplatform/eips), where protocol proposals are written down and argued in public. And the Sigmanauts program, handing self-governance to the community and running key social channels.

Real decentralization is hard on web2 platforms. Admin and moderation rights are granted and revoked at the owner's discretion.

Almost all else is loose coordination. Informality has real advantages, it is flexible and avoids bureaucracy. But that undocumented process is also illegible, and illegible systems tend to re-centralize and keep newcomers out, because only insiders know how things actually happen.

When structure is absent, responsibility defaults back to whoever is willing to carry it. DAOs meant to distribute work thin out to a few committed people.

The more legible a system is, through documented process, published rules, recorded decisions, and a clear path for newcomers, the harder it is to capture and the easier it is to join. Writing things down is the most ethos aligned form of decentralization available.

**Practices to uphold.** Write down, in one place, how protocol and ecosystem decisions actually get made, even if the answer is just "informally". And publish the path a new contributor earns review and merge authority. A problem to solve for active contributors is, how responsibility stays decentralized, rather than just defaulting to whoever is willing.

---

## 6. Adversarial resilience

> "Financial privacy is especially vital because it can be the difference between survival and systematic suppression of an opposition group in a country with an authoritarian government."
>
> *Ergo Manifesto, Privacy*

Ergo's whole reason to exist is to be a tool that survives centralized and state power on behalf of ordinary people. A chain with that mission has to be harder to capture than the system it offers an exit from. External and adversarial pressure is a first order resilience concern.

**The targets.** Privacy capable and permissionless money is a regulatory target. Pressure can be applied directly on privacy features and uncensorable payments, or on the people and entities around the chain. The easiest targets are those with a name and address. Operators of dApps, known developers, legal entities, exchanges that list Ergo.

Many contributors are anonymous. Open-source developers have been pursued for writing code that other people used. A project that relies on a small number of identifiable people also has their legal exposure as a resilience risk. One more argument for distributing roles.

A legal entity is useful to sign listings or publish on compliant platforms, but also an easy target of pressure. A trade-off between convenience and exposure.

The edges can be deplatformed even when the protocol cannot. Exchanges can delist, hosting and domain providers can drop a site or repository. A censorship-resistant chain should assume the edges to be pressured and have fallbacks ready.

**Hostile capture.** Capture can be gradual. Accumulating enough hashrate to swing votes, buying influence in a treasury, or social engineering into a maintainer or signing role. The Manifesto's instruction is to find a way to reduce their impact level. The defenses are discussed in other sections as well, distributed authority, legible processes, multiple independent eyes.

Ergo's design already makes takeover difficult. No privileged keys, non-custodial and non-interactive applications, minimal reliance on operators, fully open and auditable code.

**Practices to uphold.** Map named operators, legal entities and single provider infrastructure. Decide for each if it can be made non-custodial, distributed, or anonymous, and prepare fallbacks.

---

## 7. Growth as resilience

> "Ergo should be as decentralized as possible. Always strive to spread and grow."
>
> *Ergo Manifesto, Decentralization First*

Growth shouldn't be dismissed as marketing or price chasing. For Ergo it is a security concern.

More users means more economic weight behind the chain and delivery on the mission. More capable contributors is the direct answer to the part of the concentration problem that is not solved by governance. More use cases for ordinary people make the chain much more resilient than one that only gets traded.

This is a real weakspot. The technology is far ahead of adoption, liquidity and developer attraction. Outreach is rightly treated as a shared community responsibility, which also means it's mostly done without strategy or not at all. Getting relevant means doing something that people actually use.

Growth should optimize for lowering friction between Ergo and the people the Manifesto was written for. That needs strong onboarding and documentation, a coherent entry point for new developers such as the [Ergo book](https://github.com/kushti/ergo-book), and some real-world use cases that show that the mission works. The [Ergo Developer Knowledge Base](https://ergo-knowledge-base.vercel.app/) and [Transcripts](https://ergo-transcripts.vercel.app/) for example integrate with AIs, making it easier to start building. The natural audience is a community that already shares Ergo's values or needs the tools it can provide. Not investment hype.

**Practices to uphold.** Prove the Manifesto's promise to a non-crypto person with the use cases being built. Do outreach to communities that already share Ergo's values, led with utility. Building growth on principles, instead of price, is also much better for retention.

---

## 8. The ethos as backstop

> "This might be referred to as 'Ergo's Social Contract'. In case of intentional violation of any of these principles, the resulting protocol should not be called Ergo."
>
> *Ergo Manifesto, Ergo Basic Principles*

In a project without formal governance, the shared ethos is the actual coordination mechanism. Decentralization first, permissionless and secure, built for regular people, privacy as a choice, long-term focus, are the substrate that lets many uncoordinated people pull roughly in the same direction.

The ethos is also the last line of defense. The name is tied to the principles rather than any particular chain. If Ergo ever got captured, the community that still holds the principles can fork and carry the name with it. But that only works when the ethos is held widely enough.

A long downturn separates those who came for the principle from those who came for financial gain. There is no point trying to retain the second. Factionalism is healthy as long as the factions still share the core principles. To survive, the ethos has to be writable, teachable and held by many.

The Manifesto's answer to all this is education. An ethos survives only if it is continuously taught. Education is infrastructure.

---

## 9. Synthesis

> "This long-term vision must never die for Ergo to survive. Ergo was born in crypto winter when many had already begun dismissing the future of distributed systems and their ability to create value; nonetheless, we endured and kept building."
>
> *Ergo Manifesto, Long-term Focus*

A well functioning decentralized system needs coordination, and structures that deliberately redistribute power. Most of the document reduces to these practices:

1. **Written contingency for every critical function**, with named backup and documented knowledge
2. **An agreed incident response process** and a working security disclosure channel
3. **Critical keys and accounts under multisig or secret-sharing**
4. **Distributed, legible authority**. Decision making written down, review tiered by how consensus-critical it is, a real path for new contributors to earn merge authority
5. **Public accounting** of ecosystem funds, clear and readable
6. **A growing base of capable contributors**, mentored towards work only a few can do today
7. **Funded and maintained public-goods infrastructure**
8. **Minimize attack surfaces** of core code, regulatory targets, power grabs, and have fallbacks
9. **Active education** for using and building tools, and the ethos

Ergo is rare and worth protecting. Decentralized, therefore not unorganized.
