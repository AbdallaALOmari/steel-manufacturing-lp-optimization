[README.md](https://github.com/user-attachments/files/26123324/README.md)
# Steel Manufacturing LP Optimization
**Course:** Operations Research 1 — Khalifa University  
**Tools:** Python · Gurobi · Linear Programming  

---

## Overview
Multi-period linear programming model to minimise total production and capacity
expansion costs for a steel manufacturer across two planning horizons (2025 → 2035),
subject to demand, capacity, and environmental policy constraints.

This project covers three parts:

- **Part a** — Base case: find the least-cost production and expansion plan
- **Parts b/c** — Evaluate the impact and marginal cost of individual environmental policies (water, electricity, fuel, pollutants) requiring a 20% reduction by 2035
- **Part d** — Combined water + pollutant constraints simultaneously

---

## Files

| File | Contents |
|------|----------|
| `q3_part_a_base_case.ipynb` | Base case LP — optimal production plan, shadow prices |
| `q3_parts_bcd_environmental.ipynb` | Environmental constraints — scenario analysis, infeasibility detection, shadow prices |
| `OR_1_Group_15_Project_Report.pdf` | Full project report including Q1 (trade optimisation) and Q2 (manufacturing profit maximisation) |

---

## Model Summary

**Decision variables:**
- `x25[p]` — production (kt) of process p in 2025
- `x35[p]` — production (kt) of process p in 2035  
- `E[p]` — capacity expansion (kt) of process p by 2035

**Objective:** Minimise total operational + investment cost across both periods

**Constraints:** Capacity limits, expansion limits, demand satisfaction, environmental limits (Parts b–d)

---

## Results Summary

| Scenario | Optimal Cost | Feasible? |
|----------|-------------|-----------|
| Base case (Part a) | $203,000 | ✅ |
| Water constraint (−20%) | $562,400 | ✅ |
| Electricity constraint (−20%) | — | ❌ Infeasible |
| Fuel constraint (−20%) | — | ❌ Infeasible |
| Pollutant constraint (−20%) | $416,400 | ✅ |
| Water + Pollutant combined (Part d) | $586,400 | ✅ |

**Shadow prices (marginal policy cost):**
- Water: **$2,050 per unit reduction** — tightening the water limit by 1 unit costs the company $2,050
- Pollutant: **$512.50 per unit reduction**

---

## How to Run

1. Install [Gurobi](https://www.gurobi.com/) and obtain a free academic licence via the [Gurobi Academic Program](https://www.gurobi.com/academia/academic-program-and-licenses/)
2. Install the Python package: `pip install gurobipy`
3. Open either notebook in Jupyter and run all cells
4. To test different environmental scenarios, open `q3_parts_bcd_environmental.ipynb` and follow the instructions in Section 3 to uncomment the relevant constraint

---

## Key Findings

The base case favours **Process 1** (lowest combined cost) up to its capacity limit, supplemented by **Process 2**.  

Environmental policies reveal a fundamental trade-off:
- **Water** and **pollutant** constraints are feasible but costly — they force a shift toward Process 3 (low water) or Process 2 (low pollutant)
- **Electricity** and **fuel** constraints are **infeasible** — no process combination can meet 200 kt demand while achieving a 20% reduction given available expansion limits
- The combined constraint (Part d) costs more than either individual policy, reflecting the compounding difficulty of satisfying two environmental limits simultaneously
