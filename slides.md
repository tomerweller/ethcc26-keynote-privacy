---
marp: true
theme: uncover
paginate: false
backgroundColor: #0F0F0F
color: #F6F7F8
style: |
  @import url('https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,600;0,700;1,400&family=Inter:wght@400;500;600&display=swap');

  :root {
    --stellar-yellow: #FDDA24;
    --stellar-black: #0F0F0F;
    --stellar-offwhite: #F6F7F8;
    --stellar-warmgray: #D6D2C4;
    --stellar-lavender: #B7ACE8;
    --stellar-teal: #00A7B5;
    --stellar-navy: #002E5D;
  }

  section {
    font-family: 'Inter', 'Helvetica Neue', sans-serif;
    padding: 80px 100px;
    background-color: var(--stellar-black);
    justify-content: center;
  }

  h1 {
    font-family: 'Lora', serif;
    color: var(--stellar-offwhite);
    font-size: 2.6em;
    font-weight: 700;
    line-height: 1.15;
    margin-bottom: 0.3em;
  }

  h2 {
    font-family: 'Inter', sans-serif;
    color: var(--stellar-warmgray);
    font-size: 1.2em;
    font-weight: 400;
    margin-top: 0;
  }

  p, li {
    font-family: 'Inter', sans-serif;
    color: var(--stellar-warmgray);
    font-size: 0.9em;
    line-height: 1.6;
  }

  strong {
    color: var(--stellar-yellow);
    font-weight: 600;
  }

  em {
    color: var(--stellar-lavender);
    font-style: normal;
  }

  blockquote {
    border-left: 3px solid var(--stellar-yellow);
    padding-left: 1.2em;
    margin-left: 0;
    color: var(--stellar-warmgray);
    font-family: 'Lora', serif;
    font-style: italic;
    font-size: 1.1em;
  }

  a {
    color: var(--stellar-teal);
  }

  section.title {
    text-align: left;
  }

  section.title h1 {
    font-size: 3em;
  }

  section.title h2 {
    color: var(--stellar-warmgray);
    font-size: 1.1em;
    margin-top: 0.5em;
  }

  footer {
    font-family: 'Inter', sans-serif;
    font-size: 0.55em;
    color: var(--stellar-warmgray);
    opacity: 0.5;
  }
---

<!-- _class: title -->

# Privacy That Doesn't Break the Chain

## Tomer Weller · EthCC

<!--
Hi, I'm Tomer Weller, CPO at the Stellar Development Foundation. I've been in crypto for almost 9 years and for the last couple of years, privacy has been my main focus. This talk is about what we've learned in discussions with institutions about privacy.
-->

---

# Why Privacy?

<!--
If you're in this room you're probably already sold on privacy. But just to level set:

Blockchain is the only financial system where every transaction is visible to everyone. Your paycheck is private. Your bank balance is private. But the moment any of that moves on-chain, it's public.

For individuals, this means anyone with a block explorer can reconstruct your financial life. For institutions, it's worse -- volumes, relationships, trading strategies, payroll. This is competitive intelligence, exposed to every competitor, in real time.

When we talk to financial institutions, they make it clear: not having a way to manage visibility is a non-starter.

Transition: Easy -- we've been working on privacy for 10 years, no? Not exactly.
-->

---

# The Privacy Mistake

<!--
Yeah, we've been working on privacy for a while but with a strong focus on cypherpunk values -- complete financial freedom.

And that's awesome. But for the next wave of adoption we need institutions -- we need them to feel comfortable bringing their assets on chain, making payroll, accepting merchant payments, engaging with blockchain in a meaningful way.

For these institutions privacy means something different -- it means managing visibility in a way that allows them to stay competitive but also in compliance.

Transition: The mistake is that we've built absolute privacy. But what institutions are telling us is that privacy is a spectrum.
-->

---

# Privacy is a Spectrum

<!--
Privacy is not binary. It's a spectrum with an enormous number of permutations:

Jurisdictions vary. A regulated asset issued in the US adheres to a completely different regulatory regime than a similar one issued in Germany.

Use cases vary. Payroll needs different privacy than trading, which needs different privacy than remittances.

Technology varies. ZK proofs, FHE, MPC, TEEs -- each has different tradeoffs in performance, trust assumptions, and what they can actually hide.

The real problem is that we've been treating privacy as a single feature when it's actually a multi-dimensional design space. Any solution that doesn't acknowledge this complexity is going to fail for real-world adoption.

Transition: This is what I call "Privacy Dead Ends".
-->

---

# Privacy Dead Ends

<!--
When we started looking at privacy for Stellar, we realized that most privacy solutions end up in one of two failure modes, or "dead ends".

All-or-Nothing: Privacy solutions that have two modes: full transparency or full privacy, nothing in between. This can take the shape of a smart contract pool, an L2 or an appchain - but the premise is the same. Unfortunately, this doesn't leave room for regulated financial institutions to engage with.

Permissioned Chains: I've been in crypto almost 9 years and it's very depressing - as soon as you think that the concept of permissioned chains is dead, they come back to life. Recently they've come back to life on the pretense of being private. Of course they're private - they're a fucking database on your computer, bro. Just to be clear: institutions are looking for open-participation networks - they see the value of interoperability, composability and verifiability. Permissioned chains are a dead end.

Transition: So how do you avoid these privacy dead-ends?
-->

---

# Transparency First

<!--
The answer is simple: a clear architectural separation.

An open, transparent base layer -- a maximally auditable source of truth. This is the default - this is the primary issuance platform. Anyone can verify - interoperability is trivial.

Privacy protocols built on top. Different privacy guarantees, different administrative controls, different underlying tech.

Why transparency first? This might come as a surprise given that this is a talk about privacy but transparency is a core value proposition of blockchains. The fact that an executive at an asset manager company can go on a block explorer and see the total supply of an asset and its distribution - that is a feature - not a bug - they love that shit.

With that said, our base layers should provide a rich set of building blocks for privacy. Stellar's X-Ray upgrade is an example of this approach -- adding ZK primitives (BN254, Poseidon) at the protocol level so that application developers can build configurable privacy without compromising the transparency of the base chain.

Transition: We keep talking about different privacy protocols for different use cases. Let's demonstrate with some concrete examples.
-->

---

# Private Payments

<!--
We're going to focus on Private Payments. There's interesting stuff happening in private defi but these are still a ways out.

The two main families of private payment protocols that we see are confidential tokens and privacy pools.

Confidential Tokens: Hide the what -- payment amounts and balances are concealed. But the sender and receiver are still visible on-chain. You know who's transacting, you just can't see how much. This is great for when counterparty relationships are known - for example with payroll, people know I'm employed by SDF but my salary is private. There are a bunch of different implementations of this. Stellar is part of the confidential token association and we're working with OpenZeppelin on an implementation. Narrower privacy guarantees but the tech is fairly scalable and it's a bit easier for compliance.

Privacy Pools: Payment protocols that also hide the who -- funds are mixed so that sender and receivers identities are hidden. This provides anonymity, not just confidentiality. Much stronger privacy guarantees but they inherently mix funds, which means legitimate funds can be commingled with illicit funds - which there are ways to tackle.

Transition: This demonstrates different privacy guarantees, and the question is how do we build administrative controls to enable compliance with these solutions and others.
-->

---

# Privacy Compliance* Menu

<!--
At Stellar, we've been working with various builders in the space to define a compliance menu of opt-in administrative controls. The asterisk is deliberate. First of all I'm not a lawyer, and also regulators haven't defined what compliance looks like for on-chain privacy yet. These are the administrative controls we're starting to see as requirements, this is not a comprehensive list and the idea is to have these as configurable opt-in.

Selective Disclosure (View Keys): The user chooses to reveal specific transaction details to specific parties. This allows the user to show a source of funds on demand. This is a very powerful primitive that has existed for a while, but unfortunately we haven't seen great products built around it yet.

Non-Selective Disclosure (Auditor Keys): A third party authority (e.g., an issuer or a pool operator) holds a key that can view all transactions within a scope. This means that if a law enforcement agency has a subpoena they have an actual door to knock on.

Association Sets: An allow list controlled by a pool operator - it ensures that all funds mixed come from approved addresses and reduces the risk of commingling with illicit funds.

Forced Transparent Withdrawals: Addresses an issue with association sets: what happens if an account gets revoked? They're forced to withdraw transparently -- no hiding behind the pool on the way out. 0xBow calls this rage quit and we're starting to see more of these.

Clawback: And finally, yes - clawback. If clawbacks are triggering for you then you are in the wrong room and you are not ready for what's coming next. Tokenization is at full speed and regulated assets often require clawback capabilities. If we want to see RWA issuers have first class support for privacy on blockchains - they need clawback capabilities.

Transition: These are dials, not switches. Different combinations serve different jurisdictions, use cases, and risk profiles. The menu lets you compose the compliance posture you need.
-->

---

<!-- _class: title -->

# Privacy That Doesn't Break the Chain

<!--
So to wrap up:

We've been building privacy with ideology first and that's great -- but it's not enough. Institutions need privacy too, and for them it's more nuanced.

Privacy is a spectrum. Different jurisdictions, different use cases, different tech. There's no single answer and that's okay -- that's actually the point.

The right approach is transparency first -- keep the base layer open, build configurable privacy on top. Confidential tokens, privacy pools, a compliance menu of administrative controls. Dials, not switches.

All the building blocks are in place - we have a non-hostile administration in the US, we have institutions that are at the table and see the value in blockchain, and the tech is ready.

There are no excuses - we're building privacy that doesn't break the chain. If that's interesting to you -- come build with us on Stellar.

Thanks.
-->
