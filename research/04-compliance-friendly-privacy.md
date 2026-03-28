# Open by Default, Private When Needed: Compliance-Friendly Privacy On Stellar
**Author:** James Bachini | **Source:** stellar.org

## Core Concept

Stellar maintains its public ledger while enabling privacy mechanisms at the application layer. Protocol X-Ray upgrade introduces ZK proof verification using Noir circuits within Stellar smart contracts.

## Key Mechanisms

### Association Sets
Private transaction spaces where authorized participants transact confidentially. "The public can see a stablecoin balance entering the association set, and they can verify the total supply..." while internal transactions remain obscured.

**Metaphor:** "A private booth at a restaurant, where invited participants can transact privately."

### View Keys
Selective disclosure mechanism. Participants reveal transaction specifics to authorized auditors/regulators without exposing details to the general public.

**Metaphor:** "A window into the booth, allowing participants within the association to reveal attributes of their transactions."

## Technical Implementation

Noir circuit validates three conditions simultaneously:
1. Account membership within an association
2. Transaction amounts below compliance thresholds
3. Transaction commitments matching public chain records

## The Model

"A controlled aperture that combines financial privacy with compliance tools" -- not a black box, but adjustable visibility.
