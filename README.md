# SAPM Monte Carlo — Coal / Carbon Intensity Floor

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Coal (Carbon Intensity Floor).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **6.95** |
| β_W mean | 7.01 |
| β_W std | 0.86 |
| **90% CI** | **[5.7, 8.5]** |
| 99% CI | [5.3, 9.3] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$6,882.1B/yr** |
| Π (revenue) | $990.0B/yr |

**β_W = 6.95** means the coal industry destroys **$6.95 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 1 — Impossibility

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-coal.git
cd sapm-mc-coal
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 6.95` and `ΔW median : $6,882.1B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_co2_climate_damages | $2,848.2B | [$2,371.9B, $3,417.7B] | Lognormal |
| C2_air_pollution_mortality | $3,758.3B | [$2,824.8B, $5,010.4B] | Lognormal |
| C3_coal_mine_methane | $72.0B | [$47.1B, $109.9B] | Lognormal |
| C4_extraction_harms | $50.0B | [$31.2B, $79.9B] | Lognormal |
| C5_mercury_neurotoxicity | $8.7B | [$5.4B, $13.9B] | Lognormal |
| C6_governance_failure | $116.9B | [$76.1B, $180.0B] | Lognormal |
| **Total ΔW** | **$6,882.1B** | **[$5,649.1B, $8,435.5B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 3.0 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0000%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Coal (Carbon Intensity Floor)*.
> GitHub: epostnieks/sapm-mc-coal.
> https://github.com/epostnieks/sapm-mc-coal
