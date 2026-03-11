# 💊 Geriatric Digoxin PK Digital Twin
### An Explainable, Patient-Specific Pharmacokinetic Simulator for Precision Geriatric Dosing

## 📖 Overview
This project is a fully client-side, web-based **Explainable Pharmacokinetic Digital Twin** that simulates how **Digoxin** behaves in:
- **Normal adults**
- **Frail geriatric patients** (reduced renal function, low body weight, sarcopenia)

Digoxin has a **Narrow Therapeutic Index (NTI)**. Small concentration increases can cause toxicity (arrhythmia, bradycardia, visual disturbances). The simulator demonstrates why **population-based dosing fails** in older adults and why **individualized PK** is essential.

👉 **Live Demo:** *(Add link)*

---

## 🧠 Core Idea
> **One dose does not fit all.**

This tool provides:
- Individualized PK parameters
- Concentration–time curves
- Steady-state metrics
- Explainable clinical insights
- Side-by-side comparison with healthy adults

---

## 💡 Key Features
### ✔ Patient-Specific PK Modeling
Inputs: age, sex, weight, Scr, dose, tau, number of doses  
Outputs: CrCl, CL, Vd, k, t1/2, Cmax_ss, Cmin_ss, exposure category

### ✔ Dual Digital Twin Comparison
Solid: patient  
Dashed: normal adult

### ✔ Explainable Clinical Interpretation  
Describes underexposure, accumulation, renal decline, dose needs.

### ✔ Fully Browser-Based  
No backend · No dependencies · Privacy-friendly

---

## 🔬 Scientific Background (Clinical PK)
| PK Factor | Normal Adult | Older Adult | Effect |
|----------|--------------|-------------|--------|
| CrCl | 80–120 mL/min | 30–50 mL/min | ↓ renal function |
| CL | 6–8 L/h | 3–4 L/h | ↓ 50% → accumulation |
| Vd | 6–7 L/kg | 5–6 L/kg | ↓ lean mass |
| t1/2 | 36–48 h | 60–80 h | ↑ 1.5–2× |
| Cmin_ss | 0.4–0.7 ng/mL | 0.8–1.5 ng/mL | ↑ toxicity |

References include findings from Jusko (1978), Koup (1980), Aronson, Brocks, Jelliffe.

---

## 🛠 Tech Stack
- HTML5 / CSS3 / Vanilla JS
- Chart.js
- Serverless client-side architecture

---

## 🚀 Getting Started

```bash
git clone https://github.com/yourusername/geriatric-digoxin-digitalTwin.git
cd geriatric-digoxin-digitalTwin
open index.html   # or double-click
```

---

## 🧩 Versioned Modeling Assumptions

### 🔹 Version 1.0 — Educational PK Model (Current)
- One-compartment IV bolus
- Renal scaling:
  
CL = TV_CL × (CrCl/80)^0.75
- Weight scaling:
  
V = TV_V × (weight/70)
- Cockcroft–Gault CrCl
- Steady-state via exponential decay summation
- Therapeutic range: 0.5–1.0 ng/mL  
**Limitations:** No IIV, no Bayesian updating, no distribution phase

### 🔹 Version 2.0 — Mechanistic PopPK
- Two-compartment PO model (gut → central → peripheral)
- PopPK covariate models (CrCl, weight)
- Dose-optimisation grid search with exposure scoring
- Cockcroft–Gault CrCl, Euler integration  
**File:** `version_2.html`

### 🔹 Version 3.0 — MIPD Prototype (Current)
- Everything in v2.0, plus:
- **Monte Carlo 95 % prediction interval** (N = 500, IIV on CL/V1/V2/Q)
- **Bayesian MAP TDM individualisation** (coordinate-descent on η_CL, η_V1)
- **MC-based precision dosing** (PTA per regimen, N = 200)
- **Clinical alerts engine** (renal severity, hypokalaemia, P-gp DDI, distribution-phase TDM warning)
- **Prediction-error metrics** (ME, RMSE — population vs MAP, shown when TDM entered)
- **Model Card** with full parameter table, references, limitations  
**File:** `version_3.html`

### 🔹 Version 3.5 — Planned
- External validation dataset & GOF plots (PRED vs OBS, VPC)
- Full MCMC posterior sampling (replace grid search)
- Inter-occasion variability (IOV)
- Electrolyte effects (K⁺, Mg²⁺, Ca²⁺) with quantitative sensitivity
- TRIPOD-AI–style reporting & software V&V documentation

---

## 🏁 Summary
A transparent, interpretable Digital Twin for geriatric Digoxin dosing, integrating:
- Clinical pharmacology
- PK/PD modeling
- Explainable AI  
Ideal for:
- PhD applications  
- PK/PD portfolios  
- Precision medicine research  

---

## 📚 Citation

Jelliffe RW, Brooker G. A clinically useful method for the determination of digoxin doses and maintenance regimens. J Chronic Dis. 1974;27(1):15-22.
Koup JR, Green BL. Clinical pharmacokinetics of digoxin in the elderly. Clin Pharmacokinet. 1980;5(6):531-540.
Jusko WJ, Weintraub M., Vore M. Digoxin disposition in obesity. Clin Pharmacol Ther. 1978;24(1):28-35.
Brocks DR. The pharmacokinetics of digoxin in the elderly: a review. J Clin Pharm Ther. 2012;37(4):379-385.
Aronson JK. Clinical pharmacokinetics of digoxin 1980. Clin Pharmacokinet. 1980;5(2):167-179.
Holford NHG. Target concentration intervention. Clin Pharmacokinet. 2012;51:261-279.
FDA Guidance for Industry: Population Pharmacokinetics (2022).
EMA Guideline on Reporting the Results of Population Pharmacokinetic Analyses (2007).

---

## 📋 Model Card (v3.0)

### Architecture
Two-compartment first-order oral absorption · Euler numerical integration (Δt = 0.2 h)

### Population Parameters
| Parameter | Typical | Covariate Scaling | IIV ω² |
|-----------|---------|-------------------|--------|
| CL | 6.0 L/h | (CrCl/80)^1.0 × (WT/70)^0.75 | 0.09 (~30 % CV) |
| V1 | 30.0 L | (WT/70)^1.0 | 0.04 (~20 % CV) |
| V2 | 470.0 L | (WT/70)^1.0 | 0.04 (~20 % CV) |
| Q | 6.0 L/h | (WT/70)^0.75 | 0.04 (~20 % CV) |
| ka | 1.0 h⁻¹ | – | – |
| F | 0.70 | DDI adjustment | – |

### Residual Error
Proportional (log-domain): σ² = 0.04 (~20 % CV)

### Bayesian MAP
- Coordinate-descent grid search on η_CL (and η_V1 if ≥ 2 TDM points)
- Prior: log-normal IIV · Likelihood: proportional error

### Drug–Drug Interactions (Educational)
| Inhibitor | CL Factor | Mechanism |
|-----------|-----------|----------|
| Amiodarone | ×0.75 | P-gp inhibition |
| Verapamil | ×0.70 | P-gp inhibition |
| Quinidine | ×0.50 | P-gp inhibition |

### Validation Status
- Internal consistency verified (mass balance, steady-state convergence)
- Prediction-error metrics (ME, RMSE) displayed when TDM data are entered
- **No external dataset evaluation** — planned for v3.5

### Intended Use
Educational / portfolio demonstration of MIPD concepts.  
**NOT for clinical decision-making.**

### Limitations
- No external validation dataset
- Fixed IIV & σ (not estimated from real data)
- Simplified Bayesian (grid search, not MCMC)
- No inter-occasion variability (IOV)
- Euler integration (not adaptive ODE solver)
- Single absorptive pathway (no enterohepatic recirculation)


© 2025 Goyeun Yun. All rights reserved.
