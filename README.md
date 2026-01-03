# Which Groups Benefited Most from the 2006 Massachusetts Health Care Reform(Revised)?

**Author:** Minjae Seo
**Date:** January 3rd, 2025

---

## Abstract

This paper examines the heterogeneous effects of the 2006 Massachusetts Health Care Reform on health insurance coverage across demographic groups. Using a difference-in-differences event study design with New England states as controls, I find that the reform reduced the uninsurance rate by approximately 5 percentage points (56% decline). Effects are substantially larger for vulnerable populations: low-income individuals experienced an 11 percentage point reduction, while young adults (ages 18-30) saw a 12 percentage point decline.

---

## Repository Structure

```
EconometricsGame/
├── Seo_Minjae_Writing_Sample.pdf    # Final writing sample (main output)
├── main.tex                          # LaTeX source code
├── writingsample.ipynb               # Python analysis notebook
├── cpsinsure.dta                     # CPS insurance data (IPUMS)
├── PNG/                              # Figures and additional analysis
│   ├── 2.png                         # Event study: Full sample
│   ├── 4.png                         # Event study: Income heterogeneity
│   ├── 5.png                         # Event study: Age heterogeneity
│   └── econometric_comp.ipynb        # Additional analysis notebook
└── README.md                         # This file
```

---

## Data

**Source:** Current Population Survey (CPS) Annual Social and Economic Supplement (ASEC), obtained from [IPUMS-CPS](https://cps.ipums.org/).

**Sample:**
- Adults aged 18-64
- New England states (MA, NH, RI, VT)
- Years: 2001-2013
- N = 180,839 person-year observations

**Key Variables:**
| Variable | Description |
|----------|-------------|
| `hcovany` | Any health insurance coverage |
| `incwage` | Wage income |
| `age` | Age in years |
| `statefip` | State FIPS code |

---

## Methodology

### Empirical Strategy: Event Study Difference-in-Differences

$$Y_{ist} = \alpha_i + \gamma_s + \delta_t + \sum_{\tau \neq 2007} \beta_\tau (\text{Mass}_s \times \mathbf{1}(t=\tau)) + \varepsilon_{ist}$$

- **Outcome:** Uninsured indicator (1 = lacks health insurance)
- **Treatment:** Massachusetts (vs. NH, RI, VT)
- **Fixed Effects:** Individual, state, year
- **Standard Errors:** Clustered at state level

### Identification
- Parallel trends assumption supported by insignificant pre-treatment coefficients
- SUTVA: No spillovers between states; well-defined treatment

---

## Key Results

| Group | Effect (p.p.) | Interpretation |
|-------|---------------|----------------|
| **Overall** | -0.05*** | 56% reduction in uninsurance |
| **Low Income** | -0.11*** | Largest gains for bottom tercile |
| **High Income** | -0.02 | No significant effect |
| **Young (18-30)** | -0.12*** | Strong response among young adults |
| **Older (50-64)** | -0.04** | Moderate effects |

*Note: *** p<0.01, ** p<0.05*

---

## Replication Instructions

### Requirements
- Python 3.8+
- Packages: `pandas`, `numpy`, `statsmodels`, `linearmodels`, `matplotlib`, `seaborn`
- LaTeX distribution (TeX Live 2020+)

### Steps

1. **Run Analysis:**
   ```bash
   jupyter notebook writingsample.ipynb
   ```

2. **Compile PDF:**
   ```bash
   pdflatex main.tex
   pdflatex main.tex  # Run twice for references
   ```

---

## References

- Finkelstein, A., et al. (2012). "The Oregon Health Insurance Experiment." *QJE*, 127(3), 1057-1106.
- Kolstad, J. T., & Kowalski, A. E. (2012). "The Impact of Health Care Reform on Hospital and Preventive Care." *JPubE*, 96(11-12), 909-929.
- Mazumder, B., & Miller, S. (2016). "The Effects of the Massachusetts Health Reform on Household Financial Distress." *AEJ: Economic Policy*, 8(3), 284-313.
- Miller, S. (2012). "The Impact of the Massachusetts Health Care Reform on Health Care Use among Children." *AER*, 102(3), 502-507.

---

## Contact

**Minjae Seo**
Email: [minjaeseo@uchicago.edu]

---