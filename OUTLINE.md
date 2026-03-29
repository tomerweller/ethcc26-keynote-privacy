# EthCC Talk - Privacy That Doesn't Break the Chain

**Description:** Most privacy systems undermine what makes blockchain useful: openness and transparency. This talk outlines the future of privacy onchain -- modular, opt-in, without sacrificing openness or interoperability. Privacy designed for the real world.

**Duration:** 20 minutes max

---

## Why Privacy? (~2 min)

If you're in this room you're probably already sold on privacy. But just to level set:

Blockchain is the only financial system where every transaction is visible to everyone. Your paycheck is private. Your bank balance is private. But the moment any of that moves on-chain, it's public.

For individuals, this means anyone with a block explorer can reconstruct your financial life. For institutions, it's worse -- volumes, relationships, trading strategies, payroll. This is competitive intelligence, exposed to every competitor, in real time.

When we talk to financial institutions, they make it clear: not having a way to manage visibility is a non-starter.

**Transition**: Easy -- we've been working on privacy for 10 years, no? Not exactly.

---

## The Privacy Mistake (~3 min)

Yeah, we've been working on privacy for a while but with a strong focus on cypherpunk values -- complete financial freedom.

And that's awesome. But for the next wave of adoption we need institutions -- we need them to feel comfortable bringing their assets on chain, making payroll, accepting merchant payments, engaging with blockchain in a meaningful way.

For these institutions privacy means something different -- it means managing visibility in a way that allows them to stay competitive but also in compliance.

**Transition**: The mistake is that we've built absolute privacy. But what institutions are telling us is that privacy is a spectrum.

---

## Privacy is a Spectrum (~3 min)

Privacy is not binary. It's a spectrum with an enormous number of permutations:

- **Jurisdictions vary.** A regulated asset issued in the US adheres to a completely different regulatory regime than a similar one issued in Germany.
- **Use cases vary.** Payroll needs different privacy than trading, which needs different privacy than remittances.
- **Technology varies.** ZK proofs, FHE, MPC, TEEs -- each has different tradeoffs in performance, trust assumptions, and what they can actually hide.

The real problem is that we've been treating privacy as a single feature when it's actually a multi-dimensional design space. Any solution that doesn't acknowledge this complexity is going to fail for real-world adoption.

**Transition:** This problem has led to us developing what I call "Privacy Dead Ends"

---

## Privacy Dead Ends (~3 min)

When we started looking at privacy for Stellar, we realized that most privacy solutions end up in one of two failure modes, or "dead ends". 

### All-or-Nothing
Privacy solutions that have two modes: full transparency or full privacy, nothing in between. This can take the shape of a smart contract pool, an L2 or an appchain - but the premise is the same. Unfortunately, this doesn't leave room for regulated financial institutions to engage with.

### Permissioned Chains
I've been in crypto almost 9 years and it's very depressing - as soon as you think that the concept of permissioned chains is dead, they come back to life. Recently they've come back to life on the pretense of being private. Of course they're private - they're a fucking database on your computer, bro. Just to be clear: institutions are looking for open-participation networks - they see the value of interoperability, composability and verifiability. Permissioned chains are a dead end.

**Transition:** So how do you avoid these privacy dead-ends? 

---

## Transparency First (~3 min)

The answer is simple: a clear architectural separation.

- **An open, transparent base layer** a maximally auditable source of truth. This is the default - this is the primary issuance platform. Anyone can verify - interoperability is trivial.

- **Privacy protocols built on top.** different privacy guarantees, different administrative controls, different underlying tech.

Why transparency first? This might come as a surprise given that this is a talk about privacy but transparency is a core value proposition of blockchains. The fact that an executive at an asset manager company can go on a block explorer and see the total supply of an asset and its distribution - that is a feature - not a bug - they love that shit. 

With that said, our base layers should provide a rich set of building blocks for privacy. Stellar's X-Ray upgrade is an example of this approach -- adding ZK primitives (BN254, Poseidon) at the protocol level so that application developers can build configurable privacy without compromising the transparency of the base chain.

**Transition:** We keep talking about different privacy protocols for different use cases. Let's demonstrate with some concrete examples. 

---

## Private Payments (~3 min)

We're going to focus on Private Payments. There's interesting stuff happening in private defi but these are still a ways out.

The two main families of private payment protocols that we see are confidential tokens and privacy pools 

### Confidential Tokens

Hide the **what** -- payment amounts and balances are concealed. But the sender and receiver are still visible on-chain. You know who's transacting, you just can't see how much. This is great for when counterparty relationships are known - for example with payroll, people know I'm employed by SDF but my salary is private. 

There are a bunch of different implementations of this. Stellar is part of the confidential token association and we're working with OpenZeppelin on an implementation. Narrower privacy guarantees but the tech is fairly scalable and it's a bit easier for compliance.

### Privacy Pools
Payment protocols that also hide the **who** -- funds are mixed so that sender and receivers identities are hidden. This provides anonymity, not just confidentiality.

Much stronger privacy guarantees but they inherently mix funds, which means legitimate funds can be commingled with illicit funds - which there are ways to tackle.

**Key point:** This demonstrates different privacy guarantees, and the question is how do we build administrative controls to enable compliance with these solutions and others.   

---

## Privacy Compliance* Menu (~3 min)

*The asterisk is deliberate. Regulators haven't defined what compliance looks like for on-chain privacy yet. These are the administrative controls we believe are necessary -- an approximation built proactively, before the rules are written.*

The tools available to tune privacy to compliance requirements:

- **Selective Disclosure (View Keys):** The user chooses to reveal specific transaction details to specific parties. A regulator or auditor can see inside the "private booth" -- but only when the participant opens the window.

- **Non-Selective Disclosure (Auditor Keys):** A designated authority (e.g., an issuer or regulator) holds a key that can view all transactions within a scope. The user doesn't choose -- the visibility is built into the system.

- **Association Sets / Non-Association Sets:** Define who can transact privately together. An association set is a closed group -- a private booth at a restaurant. Outside the set, transactions are transparent. This bounds the privacy perimeter.

- **Forced Transparent Withdrawals:** When assets leave a private context, the withdrawal is fully transparent. You can operate privately within the set, but exiting into the public chain is visible.

- **Clawback:** Yes, clawback. This is controversial in crypto, and deliberately so. In regulated finance, the ability to reverse or freeze transactions is not optional -- it's a requirement. For privacy protocols to serve institutions, they need to support administrative actions like clawback, even if that challenges crypto's core ethos. Ignoring this doesn't make it go away. It just means institutions won't come.

**Key point:** These are dials, not switches. Different combinations serve different jurisdictions, use cases, and risk profiles. The menu lets you compose the compliance posture you need.

---

## Privacy That Doesn't Break the Chain (~2 min)

1. **The mistake:** We built privacy for cypherpunks, not for the real world.
2. **The real problem:** Privacy is a spectrum -- jurisdictions, use cases, and technology all vary.
3. **The failure modes:** All-or-nothing breaks the chain. Reverting to databases abandons it.
4. **The solution:** Separate the open base layer from opt-in, configurable privacy on top.
5. **The tools:** Confidential tokens for confidentiality. Privacy pools for anonymity. A compliance menu to tune both.
6. **The future:** Privacy that works with the chain, not against it. Open by default, private when needed.

Regulators haven't written the rules yet. But we can build the toolkit now -- so that when they do, we're ready.
