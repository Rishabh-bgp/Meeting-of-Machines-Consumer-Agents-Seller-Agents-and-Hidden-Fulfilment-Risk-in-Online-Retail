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
and Hidden Fulfilment Risk in Online Retail [Case study]. Github URL: https://github.com/Rishabh-bgp/Meeting-of-Machines-Consumer-Agents-Seller-Agents-and-Hidden-Fulfilment-Risk-in-Online-Retail
```

---

## Licence and scope

Pedagogical research artefact. The simulation is fully specified and inspectable. It is not an estimate of industry-wide agentic-commerce loss. Operational extensions — live OMS/WMS gaps, multi-item baskets, reservation hoarding, and seller-side listing arms races — are listed in the notebook as dissertation-ready next steps.

## 🔗 Other repositories by Rishabh Aryan

| Repository | Description | Live |
|---|---|---|
| [100-days-of-python](https://github.com/Rishabh-bgp/100-days-of-python) | My original, offline, no-API-key solutions to all 100 projects of the 100 Days of Code Python bootcamp curriculum… | — |
| [Agentic-Engineering-Ebook](https://github.com/Rishabh-bgp/Agentic-Engineering-Ebook) | Agentic Engineering is a practical notebook-book on specifying, generating, verifying, and refining multi-tenant… | — |
| [beed-ml-study](https://github.com/Rishabh-bgp/beed-ml-study) | Provenance audit and leakage-aware benchmark of seizure-type classifiers on the Bangalore EEG Epilepsy Dataset — IIT… | — |
| [Brain-Computer-Interfaces-and-Cognitive-Computing-An-Introduction](https://github.com/Rishabh-bgp/Brain-Computer-Interfaces-and-Cognitive-Computing-An-Introduction) | Brain–computer interfaces (BCIs) link neural activity to external devices, translating brain signals via algorithms… | — |
| [building-a-virtual-cell-in-python](https://github.com/Rishabh-bgp/building-a-virtual-cell-in-python) | A cell has a normal gene-activity pattern. Knock out one gene and that pattern changes. This project trains a small… | — |
| [Chronic-Kidney-Disease-Stage-Identification-in-HIV-Infected-Patients-Using-Supervised-ML](https://github.com/Rishabh-bgp/Chronic-Kidney-Disease-Stage-Identification-in-HIV-Infected-Patients-Using-Supervised-ML) | ML is transforming Chronic Kidney Disease (CKD) detection in HIV patients, catching early asymptomatic stages to… | — |
| [cobratate](https://github.com/Rishabh-bgp/cobratate) | Cobratate, an esoteric imperative programming language. Tate-flavored syntax, ordinary semantics, and a Python… | [open](https://rishabh-bgp.github.io/cobratate/) |
| [coda-synth](https://github.com/Rishabh-bgp/coda-synth) | CoDA-Synth: stylometric detection of LLM-rewritten dark-web documents with sparse TF-IDF + LinearSVC. Research lab,… | [open](https://shale-ember-delta-kite.grok.me/) |
| [IIT-ROPAR-GENAI-FOUNDATIONS](https://github.com/Rishabh-bgp/IIT-ROPAR-GENAI-FOUNDATIONS) | Free open-source Generative AI foundations ebooks (2026) covering Claude, Grok, Gemini, Cursor, OpenAI and more —… | — |
| [iris-classification](https://github.com/Rishabh-bgp/iris-classification) | Iris flower classification in Python: scikit-learn model comparison, tuning and evaluation, FastAPI /predict API,… | [open](https://rishabh-bgp.github.io/iris-classification/) |
| [kbc-game](https://github.com/Rishabh-bgp/kbc-game) | Kaun Banega Crorepati (KBC) quiz game for the terminal in Python: 16-question prize ladder, safe levels and 4… | — |
| [knn-classifier](https://github.com/Rishabh-bgp/knn-classifier) | Simple K-Nearest Neighbors classifier on the classic Iris dataset using scikit-learn. Loads data, trains the model,… | — |
| [linear-regression-model-](https://github.com/Rishabh-bgp/linear-regression-model-) | Supervised linear regression on the scikit-learn diabetes dataset. A single feature (BMI) is used to predict… | — |
| [logistic-regression](https://github.com/Rishabh-bgp/logistic-regression) | This graduate capstone applies multi-class logistic regression to the Iris dataset. It includes EDA, stratified… | — |
| [logistics-website-capstone](https://github.com/Rishabh-bgp/logistics-website-capstone) | Logistics website capstone: Kargonaut Logistics, a premium freight site mixing claymorphism, glassmorphism and… | [open](https://rishabh-bgp.github.io/logistics-website-capstone/) |
| [lovelight-leap](https://github.com/Rishabh-bgp/lovelight-leap) | 💖 Lovelight Leap: a love-themed 2D platformer in vanilla JS canvas. 4 worlds, a boss you cheer up, original… | [open](https://rishabh-bgp.github.io/lovelight-leap/) |
| [machine-learning-part-1](https://github.com/Rishabh-bgp/machine-learning-part-1) | Machine learning in Python with scikit-learn: heart disease classification and medical insurance cost regression… | — |
| [morocco-city-aware-load-forecasting](https://github.com/Rishabh-bgp/morocco-city-aware-load-forecasting) | City-aware short-term load forecasting and peak detection on high-resolution Moroccan smart-meter data (5 zones).… | — |
| [NIELIT-DATA-SCIENCE](https://github.com/Rishabh-bgp/NIELIT-DATA-SCIENCE) | Hands-on NumPy, Pandas, and Matplotlib Jupyter notebooks for the NIELIT Data Science curriculum — practical,… | — |
| [NIELIT-MACHINE-LEARNING-PROJECTS](https://github.com/Rishabh-bgp/NIELIT-MACHINE-LEARNING-PROJECTS) | Nineteen end-to-end machine learning projects: classification, regression, clustering, and recommendation, with… | — |
| [NIELIT-PYTHON-](https://github.com/Rishabh-bgp/NIELIT-PYTHON-) | Open-source Python teaching notebooks: a language reference and five capstone programs, with detailed documentation.… | — |
| [pan-cancer-classification](https://github.com/Rishabh-bgp/pan-cancer-classification) | Leakage, equivalence, conformal reliability and data efficiency on the UCI TCGA Pan-Cancer RNA-Seq dataset — IIT… | — |
| [Predicting-Hot-Events-in-the-Early-Period-through-Bayesian-Model-for-Social-Networks](https://github.com/Rishabh-bgp/Predicting-Hot-Events-in-the-Early-Period-through-Bayesian-Model-for-Social-Networks) | This notebook details the implementation and evaluation of a Bayesian perspective Early stage Event Prediction… | — |
| [prediction-as-power](https://github.com/Rishabh-bgp/prediction-as-power) | Laboratory and working paper on prediction as power in European electricity markets. A DE-like hourly simulator… | — |
| [real-estate-valuation-taiwan](https://github.com/Rishabh-bgp/real-estate-valuation-taiwan) | Taiwan real estate valuation (Xindian, New Taipei): house price per ping prediction with scikit-learn gradient… | [open](https://rishabh-bgp.github.io/real-estate-valuation-taiwan/) |
| [snakes-and-ladders](https://github.com/Rishabh-bgp/snakes-and-ladders) | 🐍🪜 Original Snakes & Ladders browser game: hand-drawn SVG snakes and ladders, 3D dice, 2-4 humans or bots, sound,… | [open](https://rishabh-bgp.github.io/snakes-and-ladders/) |
| [spam-scan](https://github.com/Rishabh-bgp/spam-scan) | Explainable spam, phishing & Indian-scam detector for SMS/email (English, Hindi, Hinglish): TF-IDF + Logistic… | [open](https://spam-scan.onrender.com) |
| [vedic-math-hybrid-kt](https://github.com/Rishabh-bgp/vedic-math-hybrid-kt) | Hybrid Vedic Math AI: rule-based sutras (Urdhva-Tiryagbhyam, Nikhilam, Yavadunam) plus RF classifier that cleans… | — |
| [wind-turbine-power-model](https://github.com/Rishabh-bgp/wind-turbine-power-model) | Single-turbine power curves + wind-farm simulation. Weibull wind stats, hourly NASA-style speed data, and… | — |
| [zoo-website-capstone](https://github.com/Rishabh-bgp/zoo-website-capstone) | Capstone project: a fictional zoo website built twice — a beginner-style simple version and a cinematic advanced… | [open](https://rishabh-bgp.github.io/zoo-website-capstone/) |
