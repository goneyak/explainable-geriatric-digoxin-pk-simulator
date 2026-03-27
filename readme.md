# Explainable Geriatric Digoxin PK Simulator Prototype

**An explainable, patient-specific pharmacokinetic simulator for safer digoxin dosing in older adults.**

This project is a browser-based digital twin that simulates how digoxin exposure changes with age-related physiological differences such as reduced renal function, low body weight, and frailty.

It is designed to show why **one-size-fits-all dosing can fail in geriatric patients** and how individualized pharmacokinetic modeling can support safer medication decisions.

---

## Why This Project Matters

Digoxin has a **narrow therapeutic index**, meaning small increases in concentration can raise the risk of toxicity.

Older adults are especially vulnerable because pharmacokinetic parameters often change with:

- declining renal function  
- lower body weight or lean mass  
- altered volume of distribution  
- longer half-life and drug accumulation  

This simulator makes those differences visible through **patient-specific concentration–time curves, exposure metrics, and clinical interpretation**.

---

## What the Tool Does

The simulator allows users to enter patient-specific information and compare the resulting digoxin profile with a reference healthy adult.

### Inputs
- age
- sex
- weight
- serum creatinine
- dose
- dosing interval
- number of doses

### Outputs
- estimated creatinine clearance
- clearance and volume parameters
- elimination rate and half-life
- concentration–time curve
- steady-state exposure metrics
- exposure category and interpretation

---

## Current Versions

### `version_1.html`
A simplified educational PK model for demonstrating the basic impact of renal function and body weight on digoxin exposure.

### `version_2.html`
A more mechanistic population PK version with improved structure and dose optimization logic.

### `version_3.html`
The most advanced prototype, including richer clinical interpretation and a more complete precision-dosing workflow.

---

## Tech Stack

- HTML5
- CSS3
- Vanilla JavaScript
- Chart.js

No backend or external server is required.

---

## How to Run

Clone the repository and open one of the HTML files in your browser.

```bash
git clone https://github.com/goneyak/geriatric-digoxin-pk-digital-twin.git
cd geriatric-digoxin-pk-digital-twin
open version_3.html
```
## Project Goal

This project sits at the intersection of:

- clinical pharmacology  
- pharmacokinetic modeling  
- explainable decision support  
- precision medicine for older adults  

The goal is not just to predict concentrations, but to build a **transparent and clinically meaningful tool** that helps explain why individualized dosing matters.

---

## Limitations

This is a research and portfolio prototype, not a validated clinical device.

It is intended for demonstration and educational purposes only.

Current limitations include:

- no external validation dataset  
- simplified parameter assumptions  
- educational Bayesian / precision dosing logic  
- not intended for real clinical decision-making  

---

## References

- Jelliffe RW, Brooker G. *A clinically useful method for the determination of digoxin doses and maintenance regimens.* J Chronic Dis. 1974;27(1):15-22.
- Koup JR, Green BL. *Clinical pharmacokinetics of digoxin in the elderly.* Clin Pharmacokinet. 1980;5(6):531-540.
- Jusko WJ, Weintraub M, Vore M. *Digoxin disposition in obesity.* Clin Pharmacol Ther. 1978;24(1):28-35.
- Aronson JK. *Clinical pharmacokinetics of digoxin.* Clin Pharmacokinet. 1980;5(2):167-179.
- Brocks DR. *The pharmacokinetics of digoxin in the elderly: a review.* J Clin Pharm Ther. 2012;37(4):379-385.
- Holford NHG. *Target concentration intervention.* Clin Pharmacokinet. 2012;51:261-279.
- FDA. *Guidance for Industry: Population Pharmacokinetics.* 2022.
- EMA. *Guideline on Reporting the Results of Population Pharmacokinetic Analyses.* 2007.
