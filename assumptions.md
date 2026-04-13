# Monte Carlo Assumptions — Coal / Carbon Intensity Floor

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $990.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 6.95 | Confirmed by N=100,000 draws |
| ΔW median (result) | $6,882.1B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_co2_climate_damages` | lognormal | $2,280.0B | $2,850.0B | $3,420.0B | CO₂ from coal combustion: 15Gt CO₂/yr × $190/t SCC. 40% of energy-related emissi |
| `C2_air_pollution_mortality` | lognormal | $2,500.0B | $3,760.0B | $5,000.0B | 1M deaths/yr conservative × $3.76M global avg VSL. Lelieveld upper: 2.5M deaths. |
| `C3_coal_mine_methane` | lognormal | $45.0B | $72.0B | $110.0B | Coal mine methane at SC-CH₄=$1,600/t. Sources: EPA, IEA Global Methane Tracker. |
| `C4_extraction_harms` | lognormal | $30.0B | $50.0B | $80.0B | Mountaintop removal, acid mine drainage, subsidence, water contamination. Source |
| `C5_mercury_neurotoxicity` | lognormal | $5.0B | $8.7B | $14.0B | Mercury emissions — leading anthropogenic source. Neurodevelopmental damage. Sou |
| `C6_governance_failure` | lognormal | $70.0B | $117.0B | $180.0B | Lobbying delay, $2.4B self-bonded reclamation, stranded-asset socialization. Sou |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 3.0 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 3.0) = 0.0000%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 6.93 | 20% DC adj = 5.54 | 40% DC adj = 4.16

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $6,882B = 6.5% of world GDP ($106T) ✓
- **β_W range**: 6.95 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
