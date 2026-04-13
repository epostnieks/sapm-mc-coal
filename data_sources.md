# Data Sources — Coal Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Coal: Carbon Intensity Floor) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_co2_climate_damages`

CO₂ from coal combustion: 15Gt CO₂/yr × $190/t SCC. 40% of energy-related emissions. Sources: EPA 2023 SCC, IEA, GIVE model.

*Full citations: paper §4 (available SSRN).*

### `C2_air_pollution_mortality`

1M deaths/yr conservative × $3.76M global avg VSL. Lelieveld upper: 2.5M deaths. SO₂, NOx, PM2.5. Sources: Lelieveld et al. 2023, WHO.

*Full citations: paper §4 (available SSRN).*

### `C3_coal_mine_methane`

Coal mine methane at SC-CH₄=$1,600/t. Sources: EPA, IEA Global Methane Tracker.

*Full citations: paper §4 (available SSRN).*

### `C4_extraction_harms`

Mountaintop removal, acid mine drainage, subsidence, water contamination. Sources: EPA, OSMRE.

*Full citations: paper §4 (available SSRN).*

### `C5_mercury_neurotoxicity`

Mercury emissions — leading anthropogenic source. Neurodevelopmental damage. Sources: UNEP Minamata, EPA MATS.

*Full citations: paper §4 (available SSRN).*

### `C6_governance_failure`

Lobbying delay, $2.4B self-bonded reclamation, stranded-asset socialization. Sources: OpenSecrets, OSMRE, GAO.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $990.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Coal (Carbon Intensity Floor)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
