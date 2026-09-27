# Meeting of Machines

### Consumer Agents, Seller Agents, and Hidden Fulfilment Risk in Online Retail

**An information-systems case study with a reproducible multi-agent laboratory.**

When a household agent commits to an order by talking to a seller agent, the human sees a confirmation. The warehouse sees a promise that may never have been true. This repository treats that gap as an information-systems problem: **lossy representation + misaligned agent objectives + no shared operational ledger.**

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](#how-to-run)
[![Notebook](https://img.shields.io/badge/Artefact-Jupyter%20Laboratory-F37626?logo=jupyter&logoColor=white)](Meeting_of_Machines_Fulfilment_Risk_Case_Study.ipynb)
[![Domain](https://img.shields.io/badge/Field-Information%20Systems-1B4332)](#theoretical-stance)
[![Status](https://img.shields.io/badge/Lab-Pedagogical%20simulation-6C757D)](#what-the-laboratory-shows)

---

## The claim

Agent-to-agent commerce improves **transactional** efficiency. It can simultaneously raise **hidden fulfilment risk**: the chance that an order which looks valid at commitment fails on completeness, punctuality, substitution quality, or dispute resolution — and that this chance is invisible to the human principal because the old interface cues have been compressed away.

Conversion can look excellent. Exception queues do not.

> If machines are now meeting to create obligations that warehouses, stores, and couriers must honour, what information must be true at the moment of commitment, and what control system keeps that information true?

---

## Why this is an IS case, not a warehouse anecdote

| Layer | What breaks |
|---|---|
| Representation | Agents score advertised ATP, SLA, and listing quality. True stock, true cut-offs, and true defect rates stay below the commitment bar. |
| Agency | Consumer agents are rewarded for completing a mandate. Seller agents are rewarded for acceptance. Dispute-free delivery is the unmeasured residual. |
| Interorganisational systems | Marketplace, dark store, 3PL, courier, and two agent runtimes can create an obligation without a shared event log. |
| Control | A perfect JSON order can still be physically infeasible. Gates have to bind language-model commitments to operational constraints. |

---

## Risk taxonomy

| Code | Family | Hidden until | IS lever |
|---|---|---|---|
| **R1** | Inventory opacity | Short-ship, silent substitute | Signed, node-level ATP and reservation TTL |
| **R2** | SLA / promise mismatch | Late delivery, broken cold chain | Booked promise ticket, not a generated ETA |
| **R3** | Identity and authorisation | Chargeback, over-limit buy | Agent credentials and policy tokens |
| **R4** | Listing manipulation | Wrong seller, SEO-for-agents | Provenance and integrity score |
| **R5** | Last-mile accountability | Days-later dispute | Shared fulfilment event log |

Two kinds of hiding matter: **interface hiding** (the human sees a confirmation, not the machine conversation) and **temporal hiding** (defects and returns arrive after the agent has already reported success).

---

## What the laboratory shows

The notebook builds a synthetic market of seller agents and consumer agents, then matches them under three regimes.

| Regime | What the consumer side can see |
|---|---|
| Human baseline | Advertised fields plus a coarse risk badge |
| Naive A2A | Advertised price, quality, and SLA only |
| Governed A2A | Advertised fields plus a signed attestation of inventory / SLA / listing integrity |

Expected teaching pattern:

1. Naive A2A does not struggle to match. Advertised quality is cheap.
2. Demand concentrates on sellers who inflate listings and availability.
3. On-time complete rate and true fill rate are the residual — not the confirmation screen.
4. Governance does not add pickers. It changes the scoring function so hidden state is priced into the meeting of machines.

Treat the numbers as mechanism evidence, not industry calibration.

---

## Repository contents

```text
Meeting_of_Machines_Fulfilment_Risk_Case_Study.ipynb
README.md
```

The notebook is the full artefact: literature map, agent anatomy, formal model, executable laboratory, Monte Carlo and sensitivity cells, design agenda, governance notes, seminar questions, and parameter appendix.

---

## How to run

```bash
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install numpy pandas matplotlib seaborn jupyter
jupyter notebook Meeting_of_Machines_Fulfilment_Risk_Case_Study.ipynb
```

Execute cells from top to bottom. Change `PARAMS` in the first code cell to vary market size, seed, and listing-gaming prevalence.

```python
PARAMS = dict(
    seed=42,
    n_sellers=36,
    n_consumers=160,
    gaming_share=0.35,
    human_badge_cuts=(0.15, 0.30),
)
```

---

## Design agenda the case argues for

- **Signed ATP** — node-level quantity, reservation id, TTL, cycle-count age.
- **Promise ticket** — a booked slot, not a slogan.
- **Agent identity and policy tokens** — who may spend, how much, in which categories.
- **Listing integrity score** — provenance of copy versus operational quality.
- **Shared fulfilment event log** — reservation → pick → pack → handoff → exception, with common identifiers.
- **Residual-risk gate** — step-up to the human when the estimated hidden gap exceeds a threshold.
- **Outcome-priced matching** — feed short-ship, defect, and dispute rates back into agent scoring.

Two principles:

1. Do not generate what you have not booked.
2. Measure the channel by commitments honoured, not by commitments formed.

---

## Suggested citation

If you use this laboratory in a course or paper:

```text
Aryan, R. (2026). Meeting of Machines: Consumer Agents, Seller Agents,
and Hidden Fulfilment Risk in Online Retail [Jupyter case study].
```

Adjust author line to match the repository owner.

---

## Licence and scope

Pedagogical research artefact. The simulation is fully specified and inspectable. It is not an estimate of industry-wide agentic-commerce loss. Operational extensions — live OMS/WMS gaps, multi-item baskets, reservation hoarding, and seller-side listing arms races — are listed in the notebook as dissertation-ready next steps.
