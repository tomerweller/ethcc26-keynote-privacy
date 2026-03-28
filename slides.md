---
marp: true
theme: default
paginate: true
backgroundColor: #1a1a2e
color: #eee
style: |
  section {
    font-family: 'Inter', 'Helvetica Neue', sans-serif;
  }
  h1 {
    color: #fff;
    font-size: 2.2em;
  }
  h2 {
    color: #ccc;
    font-size: 1.4em;
    font-weight: 400;
  }
  strong {
    color: #7eb8ff;
  }
  blockquote {
    border-left: 4px solid #7eb8ff;
    color: #bbb;
    font-style: italic;
  }
  table {
    font-size: 0.85em;
  }
  th {
    background-color: #2a2a4a;
  }
---

# Privacy That Doesn't Break the Chain

## EthCC · Tomer Weller

<!--
Introduce yourself. CPO at Stellar Development Foundation.
This talk is about why the crypto ecosystem has been building privacy wrong, and what it looks like to get it right -- especially for institutions.
-->

---

# Why Privacy?

Your paycheck is private.
Your bank balance is private.
Your supplier payments are private.

**On-chain, all of it is public.**

<!--
Blockchain is the only financial system where every transaction is visible to everyone. Start with something relatable -- everyone in the room has a bank account. That privacy is taken for granted. The moment you move any of that on-chain, it's gone.
-->

---

# Why Privacy?

For institutions, this is **competitive intelligence** exposed in real time:

- Deposit volumes
- Counterparty relationships
- Trading strategies
- Payroll

<!--
For individuals it's bad. For institutions it's existential. A competitor watching deposit flows in real time knows your vendors, your payroll schedule, when you're under pressure. This isn't hypothetical -- this is why institutions say they can't come on-chain.
-->

---

> "Unless you can protect my information, I can't do anything on the blockchain."

That's not a cypherpunk talking. **That's a bank.**

<!--
This is a direct quote from a major global bank. They weren't talking about customer data. They were talking about their own competitive intelligence. The gap isn't regulatory -- it's technical. Once data is broadcast on a transparent ledger, it cannot be re-privatized.
-->

---

# The Privacy Mistake

The crypto ecosystem built privacy with **cypherpunk values**.

Mixers. Shielded chains. Fully private L1s.

The ideology: transparency is the enemy, privacy is absolute.

<!--
The crypto ecosystem's approach to privacy was shaped by cypherpunk ideology -- the belief that privacy means hiding everything from everyone. That gave us mixers, shielded chains, fully private L1s. All designed around "reveal nothing to nobody."
-->

---

# The Privacy Mistake

Institutions don't want to hide from regulators.
They want to hide from **competitors** while remaining **accountable**.

We built privacy tools for an audience that doesn't include the people holding the next trillion dollars of capital.

<!--
This is the core mismatch. Cypherpunk privacy is about hiding from authority. Institutional privacy is about hiding from competitors while remaining fully accountable to regulators. These are fundamentally different requirements, and we built for the wrong one.
-->

---

# The Privacy Mistake

The mistake wasn't building privacy.

It was treating privacy as an **ideology** instead of a **practical requirement**.

<!--
Land this clearly. Nobody is saying privacy is bad. The mistake is framing it as all-or-nothing, as a philosophical stance rather than a practical engineering problem with many valid configurations.
-->

---

# Privacy is a Spectrum

Privacy is not binary. It's a spectrum with an enormous number of permutations.

<!--
Transition: so if all-or-nothing is wrong, what does the right model look like? It starts with recognizing that privacy is not a single feature. It's a multi-dimensional design space.
-->

---

# Privacy is a Spectrum

**Jurisdictions vary.**
EU ≠ US ≠ Singapore ≠ Brazil. There is no single compliance framework.

**Use cases vary.**
Payroll ≠ trading ≠ lending ≠ remittances.

**Technology varies.**
ZK proofs, FHE, MPC, TEEs -- different tradeoffs, different capabilities.

<!--
Three axes of variation. Jurisdictions: GDPR vs US frameworks vs MAS in Singapore -- completely different requirements. Use cases: payroll privacy is nothing like trading privacy. Technology: each primitive (ZK, FHE, MPC, TEEs) can hide different things with different trust assumptions and performance profiles.
-->

---

# Privacy is a Spectrum

There is no one-size-fits-all privacy.

**We need to design for the spectrum.**

<!--
The right question isn't "private or public?" -- it's "private from whom?" Pre-trade privacy but post-settlement transparency. Counterparty-visible but public-hidden. Regulator-accessible but competitor-blind. These are all valid points on the spectrum.
-->

---

# Privacy Dead Ends

When you ignore the spectrum, you end up at one of two extremes.

<!--
So what happens when you don't design for the spectrum? You end up at one of two dead ends. Neither works.
-->

---

# Dead End: All-or-Nothing

Fully shielded chains. Total opacity.

✓ Privacy
✗ Composability
✗ Auditability
✗ Compliance

**The transparent ledger -- the thing that makes blockchain trustworthy -- is gone.**

<!--
The first dead end: total privacy. Fully shielded chains give you opacity but you lose everything that makes blockchain valuable. You can't compose with DeFi. You can't audit. You can't comply with any regulatory framework. The transparent ledger -- the thing that makes blockchain trustworthy -- is gone. You've broken the chain.
-->

---

# Dead End: Revert to Database

Permissioned databases. Private ledgers.

✓ Privacy
✓ Compliance
✗ Neutrality
✗ Composability
✗ Shared settlement
✗ Open access

**You're back to the old system with extra steps.**

<!--
The second dead end: give up on public chains entirely. Institutions retreat to permissioned databases or private ledgers. You get privacy and compliance, but you lose neutrality, composability, shared settlement, open access. You're back to the old system with extra steps. You've abandoned the chain.
-->

---

# Privacy Dead Ends

All-or-nothing **breaks** the chain.

Reverting to a database **abandons** it.

<!--
Pause here. Let this land. Both extremes fail. We need a third path.
-->

---

# Transparency First

The answer is a clear **architectural separation**.

<!--
The third path. Not a compromise -- a clear architectural principle.
-->

---

# Transparency First

**Open, transparent base layer.**
The L1 stays public. Anyone can verify. The chain's integrity is preserved.

**Privacy protocols built on top.**
Opt-in, configurable at the application layer. You choose what to reveal and what to hide.

<!--
Two layers. The base layer stays fully transparent -- that's the feature, that's what gives blockchain its integrity. Privacy is built on top, at the application layer. It's opt-in. It's configurable. You choose what to reveal and what to hide, based on your jurisdiction, your use case, and your risk profile. The base layer doesn't need to change.
-->

---

# Transparency First

Open by default. Private when needed.

The chain stays transparent. **Privacy lives at the application layer.**

Example: Stellar's X-Ray upgrade -- ZK primitives (BN254, Poseidon) at the protocol level, enabling configurable privacy without compromising the base chain.

<!--
Stellar's X-Ray upgrade (Protocol 25) is an example of this approach. It adds BN254 elliptic curves and Poseidon hashing natively to the protocol -- these are foundational ZK primitives that let application developers build configurable privacy without compromising the transparency of the base chain. The base stays open. The applications choose their privacy posture.
-->

---

# Private Payments

Privacy on payments isn't monolithic.
Two distinct families of protocols.

<!--
Now let's get concrete. When we talk about privacy on payments, there are actually two different families of protocols, and they do fundamentally different things.
-->

---

# Confidential Tokens

Hide the **what**.

- Payment amounts and balances are concealed
- Sender and receiver are still visible
- You know *who* is transacting, not *how much*

**Use case:** Treasury operations, supplier payments, payroll.

<!--
Confidential tokens hide the what -- amounts and balances are concealed, but the sender and receiver are still visible on-chain. You know who's transacting, you just can't see how much. This is the right tool for institutions making payments where the counterparty relationship is already known or acceptable, but the amounts are sensitive. Think treasury operations, supplier payments, payroll.
-->

---

# Privacy Pools

Hide the **who**.

- Funds are mixed, sender identity is obscured
- Provides **anonymity**, not just confidentiality

**Use case:** Consumer payments where the individual shouldn't be identifiable.

**Tradeoff:** Legitimate funds can be commingled with illicit funds.

<!--
Privacy pools hide the who. Funds are mixed so the sender's identity is obscured. This provides anonymity, not just confidentiality. The use case is consumer payments where the individual shouldn't be identifiable. But the tradeoff is real: mixing means legitimate funds can be commingled with illicit funds. This is the core tension that compliance tooling needs to address.
-->

---

# Private Payments

Confidentiality ≠ Anonymity

| | Amounts hidden | Identity hidden |
|---|---|---|
| **Confidential Tokens** | ✓ | ✗ |
| **Privacy Pools** | ✓ | ✓ |

Different use cases need **different combinations**.

<!--
Key takeaway from this section: confidentiality and anonymity are separate properties. They're not competing approaches -- they're different tools for different points on the spectrum. Some use cases need one, some need both, some need neither. This is what "design for the spectrum" means in practice.
-->

---

# Privacy Compliance* Menu

*\* Regulators haven't defined what compliance looks like for on-chain privacy yet.*

*These are administrative controls we believe are necessary -- an approximation, built proactively, before the rules are written.*

<!--
Now, how do you make any of this work for regulated institutions? The asterisk on "compliance" is deliberate. Regulators haven't told us what compliance looks like for on-chain privacy. There's no playbook. So what we're presenting here is an approximation -- the set of administrative controls we believe are necessary, built proactively, before the rules are written.
-->

---

# The Menu

**Selective Disclosure** (View Keys)
User chooses to reveal transaction details to specific parties.

**Non-Selective Disclosure** (Auditor Keys)
A designated authority can view all transactions within a scope.

<!--
Selective disclosure via view keys: the user chooses to open the window. They reveal specific transaction details to specific parties -- a regulator, an auditor, a counterparty. The user is in control. Non-selective disclosure via auditor keys: a designated authority -- an issuer, a regulator -- holds a key that can view all transactions within a scope. The user doesn't choose. The visibility is built into the system from the start.
-->

---

# The Menu

**Association Sets**
Define who can transact privately together. A closed group -- a private booth at a restaurant.

**Forced Transparent Withdrawals**
Exiting the private context is fully visible on-chain.

<!--
Association sets define the privacy perimeter -- who can transact privately together. Think of it as a private booth at a restaurant. Inside the booth, transactions are private. Outside, everything is transparent. This bounds the risk. Forced transparent withdrawals mean that when assets leave the private context, the exit is fully visible. You can operate privately within the set, but re-entering the public chain is transparent. This prevents private pools from becoming black holes.
-->

---

# The Menu

**Clawback**

Yes, clawback.

In regulated finance, the ability to reverse or freeze transactions is not optional -- it's a requirement.

Ignoring this doesn't make it go away. **It just means institutions won't come.**

<!--
Clawback. Yes, this is controversial in crypto. Deliberately so. In regulated finance, the ability to reverse or freeze transactions isn't optional -- it's a legal requirement. For privacy protocols to serve institutions, they need to support administrative actions like clawback, even if that challenges crypto's core ethos. We can have the philosophical debate, but ignoring this requirement doesn't make it disappear. It just means institutions won't adopt on-chain privacy. We're choosing to tackle it head on.
-->

---

# Privacy Compliance* Menu

These are **dials**, not switches.

Different combinations serve different jurisdictions, use cases, and risk profiles.

The menu lets you compose the compliance posture you need.

<!--
The key framing: these are dials, not switches. You don't pick one -- you compose a combination that fits your jurisdiction, your use case, your risk profile. A stablecoin issuer in the EU will turn different dials than a DeFi protocol in Singapore. That's the point. The menu lets you build the compliance posture you need, not the one someone else decided for you.
-->

---

# Privacy That Doesn't Break the Chain

1. We built privacy for cypherpunks, not for the real world
2. Privacy is a spectrum -- jurisdictions, use cases, and technology all vary
3. All-or-nothing breaks the chain. Databases abandon it.
4. Separate the open base layer from configurable privacy on top
5. Confidential tokens for confidentiality. Privacy pools for anonymity.
6. A compliance menu to tune both.

<!--
Quick recap of the full arc. Hit each point briefly -- the audience has heard the detail, this is just anchoring the structure.
-->

---

# Privacy That Doesn't Break the Chain

Regulators haven't written the rules yet.

**We can build the toolkit now -- so that when they do, we're ready.**

<!--
Close strong. The regulators haven't written the rules. But we don't need to wait. We can build the toolkit -- configurable, compliance-ready, open by default -- so that when the rules come, the infrastructure is already there. Privacy that works with the chain, not against it.
-->

---
