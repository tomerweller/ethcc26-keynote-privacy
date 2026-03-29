# EthCC Talk - Privacy That Doesn't Break the Chain

**Description:** Most privacy systems undermine what makes blockchain useful: openness and transparency. This talk outlines the future of privacy onchain -- modular, opt-in, without sacrificing openness or interoperability. Privacy designed for the real world.

**Duration:** 20 minutes max

---

## Intro (~0.5 min)

Hi, I'm Tomer, CPO at the Stellar Development Foundation. I've been in crypto for almost 9 years and for the last couple of years, privacy has been one of my focal points. This talk is about what we've learned in discussions with institutions about privacy.

---

## Why Privacy? (~1.5 min)

If you're in this room you're probably already sold on privacy. But just to level set:

Blockchain is the only financial system where every transaction is visible to everyone. Your paycheck is private. Your bank balance is private. But the moment any of that moves on-chain, it's public.

For individuals, this means anyone with a block explorer can reconstruct your financial life. For institutions, it's worse -- volumes, relationships, trading strategies, payroll. This is competitive intelligence, exposed to every competitor, in real time.

When we talk to financial institutions, they make it clear: not having a way to manage visibility is a non-starter.

**Transition**: Easy -- we've been working on privacy for 10 years, no? Not exactly.

---

## The Privacy Mistake (~1.5 min)

Yeah, we've been working on privacy for a while but with a strong focus on cypherpunk values -- complete financial freedom.

And that's awesome. But for the next wave of adoption we need institutions -- we need them to feel comfortable bringing their assets on chain, making payroll, accepting merchant payments, engaging with blockchain in a meaningful way.

For these institutions privacy means something different -- it means managing visibility in a way that allows them to stay competitive and compliant.

**Transition**: The mistake is that we've built absolute privacy. But what institutions are telling us is that privacy is a spectrum.

---

## Privacy is a Spectrum (~1.5 min)

Privacy is not binary. It's a spectrum with an enormous number of permutations:

- **Jurisdictions vary.** A regulated asset issued in the US adheres to a completely different regulatory regime than a similar one issued in Germany.
- **Use cases vary.** Payroll needs different privacy than trading, which needs different privacy than remittances.
- **Technology varies.** ZK proofs, FHE, MPC, TEEs -- each has different tradeoffs in performance, trust assumptions, and what they can actually hide.

The real problem is that we've been treating privacy as a single feature when it's actually a multi-dimensional design space. Any solution that doesn't acknowledge this complexity is going to fail for real-world adoption.

**Transition:** Not recognizing the privacy spectrum has led us to develop what I call "Privacy Dead Ends"

---

## Privacy Dead Ends (~2 min)

When we started looking at privacy for Stellar, we realized that most privacy solutions today end up in one of two failure modes, or "dead ends". 

### All-or-Nothing
Privacy solutions that have two modes: full transparency or full privacy, nothing in between. This can take the shape of a smart contract pool, an L2 or an appchain - but the premise is the same: all or nothing. Unfortunately, this doesn't leave room for nuance for regulated financial institutions to engage with.

### Permissioned Chains
I've been in crypto almost 9 years and it's very depressing - as soon as you think that the concept of permissioned chains is dead, they come back to life. Recently they've come back to life on the pretense of being private. Of course they're private - they're a fucking database on your computer, bro. Just to be clear: institutions are looking for open-participation networks - they see the value of interoperability, composability and verifiability. Permissioned chains are a dead end.

**Transition:** So how do you avoid these privacy dead-ends? 

---

## The Privacy Stack (~2 min)

We think that the answer is simple: a clear architectural separation.

- **Transparency first.** The base layer stays open and auditable. This might come as a surprise given that this is a talk about privacy but transparency is a core value proposition of blockchains for institutions. The fact that an executive at an asset management company can go on a block explorer and see the total supply of an asset and its distribution - that is a feature - not a bug - they love that shit.

- **Building blocks for privacy.** The base layer should provide the primitives that enable privacy -- without enshrining a specific type of privacy. We've seen L1s try to enshrine privacy - sometimes it ends poorly with bugs, sometimes it's just obsolete by the time it comes out. With Stellar we took a building blocks approach and our X-Ray upgrade earlier this year introduced an advanced set of ZK primitives that now enable many different privacy protocols.

And that's the final layer: 

- **Privacy protocols on top.** Different protocols for different privacy guarantees, different administrative controls, different underlying tech. Most importantly: there will be many of them.

**Transition:** We keep talking about different privacy protocols for different use cases. Let's demonstrate with some concrete examples. 

---

## Private Payments (~2 min)

We're going to focus on Private Payments. There's interesting stuff happening in private defi and trading but these are still a ways out and payments are by far the most important and immediate use case.

We're seeing two main families of private payment protocols these days, the first one is confidential tokens.

### Confidential Tokens

Hide the **what** -- payment amounts and balances are concealed. But the sender and receiver are still visible on-chain. You know who's transacting, you just can't see how much. This is great for when counterparty relationships are known. For example with payroll, people know I'm employed by SDF but my salary is private. 

There are a bunch of different implementations of this. Stellar is part of the confidential token association and we're working with OpenZeppelin on an implementation. 

Confidential tokens deliver narrower privacy guarantees but the tech is fairly scalable and it's a bit easier for compliance.

The second family we're seeing are privacy pools.

### Privacy Pools
These are payment protocols that hide the what **and the who** -- funds are mixed so that sender and receiver identities are hidden. This provides anonymity, not just confidentiality.

Some notable examples are 0xBow in the Ethereum ecosystem, and Nethermind is building a dedicated Stellar implementation -- SPP (Stellar Private Payments).

Privacy Pools have much stronger privacy guarantees but they inherently mix funds, which means legitimate funds can be commingled with illicit funds - which there are ways to tackle.

**Transition:** This demonstrates different privacy guarantees, and the question is how do we build administrative controls to enable compliance with these solutions and others.   

---

## Privacy Compliance* Menu (~3 min)

At Stellar, we've been working with various builders in the space to define a compliance menu of opt-in administrative controls. The asterisk is deliberate. First of all I'm not a lawyer, and also regulators haven't defined what compliance looks like for on-chain privacy yet. These are the administrative controls we're starting to see as requirements, this is not a comprehensive list and the idea is to have these as configurable opt-in as needed. 

- **Selective Disclosure (View Keys):** The user chooses to reveal specific transaction details to specific parties. This allows the user to show a source of funds on demand. This is a very powerful primitive that has existed for a while, but unfortunately we haven't seen great products built around it yet.

- **Non-Selective Disclosure (Auditor Keys):** A third party authority (e.g., an issuer or a pool operator) holds a key that can view all transactions within a scope. This means that if a law enforcement agency has a subpoena they have an actual door to knock on.

- **Association Sets** have been pioneered with Privacy Pools, these are allow lists controlled by a pool operator - they ensure that all funds mixed come from approved addresses and reduces the risk of commingling with illicit funds.

- **Forced Transparent Withdrawals:** These address an issue with association sets: what happens if an account gets revoked? They're forced to withdraw transparently with no privacy guarantees. 0xBow calls this rage quit and we're starting to see more of these.

- **Clawback:** And finally, yes - clawback. If clawbacks are triggering for you then you are in the wrong room and you are not ready for what's coming next. Tokenization is at full speed and regulated assets often require clawback capabilities. If we want to see RWA issuers have first class support for privacy on blockchains - they need clawback capabilities. 

**Transition:** This menu is a starting point to let you compose the type of compliance you need. If you're in this room and this menu is offensive to you - let us know - it's work in progress and we'd love to get feedback. 

---

## Privacy That Doesn't Break the Chain (~1 min)

So to wrap up:

In crypto, we've been building privacy with ideology first and that's great -- but it's not enough. Institutions need privacy too, and for them it's more nuanced.

Privacy is a spectrum. Different jurisdictions, different use cases, different tech. There's no single answer and that's okay.

The right approach is transparency first -- keep the base layer open, provide the low-level building blocks and build configurable privacy on top: things like confidential tokens and privacy pools, administrative controls as needed.  

All the building blocks are in place - we have a non-hostile administration in the US, we have institutions that are at the table and see the value in blockchain, and the tech is ready.

There are no excuses - we're building privacy that doesn't break the chain. If that's interesting to you -- come build with us on Stellar.

Thanks. 