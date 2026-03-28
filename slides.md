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

---

# Why Privacy?

Your paycheck is private.
Your bank balance is private.
Your supplier payments are private.

**On-chain, all of it is public.**

---

# Why Privacy?

For institutions, this is **competitive intelligence** exposed in real time:

- Deposit volumes
- Counterparty relationships
- Trading strategies
- Payroll

---

> "Unless you can protect my information, I can't do anything on the blockchain."

That's not a cypherpunk talking. **That's a bank.**

---

# The Privacy Mistake

The crypto ecosystem built privacy with **cypherpunk values**.

Mixers. Shielded chains. Fully private L1s.

The ideology: transparency is the enemy, privacy is absolute.

---

# The Privacy Mistake

Institutions don't want to hide from regulators.
They want to hide from **competitors** while remaining **accountable**.

We built privacy tools for an audience that doesn't include the people holding the next trillion dollars of capital.

---

# The Privacy Mistake

The mistake wasn't building privacy.

It was treating privacy as an **ideology** instead of a **practical requirement**.

---

# Privacy is a Spectrum

Privacy is not binary. It's a spectrum with an enormous number of permutations.

---

# Privacy is a Spectrum

**Jurisdictions vary.**
EU ≠ US ≠ Singapore ≠ Brazil. There is no single compliance framework.

**Use cases vary.**
Payroll ≠ trading ≠ lending ≠ remittances.

**Technology varies.**
ZK proofs, FHE, MPC, TEEs -- different tradeoffs, different capabilities.

---

# Privacy is a Spectrum

There is no one-size-fits-all privacy.

**We need to design for the spectrum.**

---

# Privacy Dead Ends

When you ignore the spectrum, you end up at one of two extremes.

---

# Dead End: All-or-Nothing

Fully shielded chains. Total opacity.

✓ Privacy
✗ Composability
✗ Auditability
✗ Compliance

**The transparent ledger -- the thing that makes blockchain trustworthy -- is gone.**

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

---

# Privacy Dead Ends

All-or-nothing **breaks** the chain.

Reverting to a database **abandons** it.

---

# Transparency First

The answer is a clear **architectural separation**.

---

# Transparency First

**Open, transparent base layer.**
The L1 stays public. Anyone can verify. The chain's integrity is preserved.

**Privacy protocols built on top.**
Opt-in, configurable at the application layer. You choose what to reveal and what to hide.

---

# Transparency First

Open by default. Private when needed.

The chain stays transparent. **Privacy lives at the application layer.**

Example: Stellar's X-Ray upgrade -- ZK primitives (BN254, Poseidon) at the protocol level, enabling configurable privacy without compromising the base chain.

---

# Private Payments

Privacy on payments isn't monolithic.
Two distinct families of protocols.

---

# Confidential Tokens

Hide the **what**.

- Payment amounts and balances are concealed
- Sender and receiver are still visible
- You know *who* is transacting, not *how much*

**Use case:** Treasury operations, supplier payments, payroll.

---

# Privacy Pools

Hide the **who**.

- Funds are mixed, sender identity is obscured
- Provides **anonymity**, not just confidentiality

**Use case:** Consumer payments where the individual shouldn't be identifiable.

**Tradeoff:** Legitimate funds can be commingled with illicit funds.

---

# Private Payments

Confidentiality ≠ Anonymity

| | Amounts hidden | Identity hidden |
|---|---|---|
| **Confidential Tokens** | ✓ | ✗ |
| **Privacy Pools** | ✓ | ✓ |

Different use cases need **different combinations**.

---

# Privacy Compliance* Menu

*\* Regulators haven't defined what compliance looks like for on-chain privacy yet.*

*These are administrative controls we believe are necessary -- an approximation, built proactively, before the rules are written.*

---

# The Menu

**Selective Disclosure** (View Keys)
User chooses to reveal transaction details to specific parties.

**Non-Selective Disclosure** (Auditor Keys)
A designated authority can view all transactions within a scope.

---

# The Menu

**Association Sets**
Define who can transact privately together. A closed group -- a private booth at a restaurant.

**Forced Transparent Withdrawals**
Exiting the private context is fully visible on-chain.

---

# The Menu

**Clawback**

Yes, clawback.

In regulated finance, the ability to reverse or freeze transactions is not optional -- it's a requirement.

Ignoring this doesn't make it go away. **It just means institutions won't come.**

---

# Privacy Compliance* Menu

These are **dials**, not switches.

Different combinations serve different jurisdictions, use cases, and risk profiles.

The menu lets you compose the compliance posture you need.

---

# Privacy That Doesn't Break the Chain

1. We built privacy for cypherpunks, not for the real world
2. Privacy is a spectrum -- jurisdictions, use cases, and technology all vary
3. All-or-nothing breaks the chain. Databases abandon it.
4. Separate the open base layer from configurable privacy on top
5. Confidential tokens for confidentiality. Privacy pools for anonymity.
6. A compliance menu to tune both.

---

# Privacy That Doesn't Break the Chain

Regulators haven't written the rules yet.

**We can build the toolkit now -- so that when they do, we're ready.**

---
