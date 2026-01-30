# Aadhaar Inclusion Gap Analysis

This repository analyzes Aadhaar Biometric, Demographic, and Enrolment datasets to identify coverage gaps and update trends across states, districts, and pincodes.

## Repository Structure

```
.
├── aadhaar_analysis.ipynb          # Main analysis notebook
├── api_data_aadhar_biometric/      # Biometric update CSVs
│   └── api_data_aadhar_biometric/api_data_aadhar_biometric/*.csv
├── api_data_aadhar_demographic/    # Demographic update CSVs
│   └── api_data_aadhar_demographic/api_data_aadhar_demographic/*.csv
├── api_data_aadhar_enrolment/      # Enrolment CSVs
│   └── api_data_aadhar_enrolment/api_data_aadhar_enrolment/*.csv
└── Output/                         # Saved visualization outputs
    ├── Univariate_Analysis/
    ├── Bivariate_Analysis/
    └── Trivariate_Analysis/
```

## Aadhaar Lifecycle (from the code flow)

The notebook models the Aadhaar lifecycle as a data journey from enrolment to updates, then derives analytics:

1. **Enrolment**  
   New Aadhaar records are registered and captured in the enrolment dataset (age groups: 0–5, 5–17, 18+).
2. **Demographic Updates**  
   Aadhaar holders update personal details (e.g., name/address corrections) captured in the demographic dataset (age groups: 5–17, 17+).
3. **Biometric Updates**  
   Fingerprint/iris updates are captured in the biometric dataset (age groups: 5–17, 17+).
4. **Analytics & Insights**  
   The notebook standardizes geographic fields, aggregates data, and creates univariate, bivariate, and trivariate insights. Visual outputs are stored in `Output/`.

## Data Overview

| Dataset | Columns | Notes |
| --- | --- | --- |
| Enrolment | date, state, district, pincode, age_0_5, age_5_17, age_18_greater | New Aadhaar registrations |
| Demographic | date, state, district, pincode, demo_age_5_17, demo_age_17_ | Demographic updates |
| Biometric | date, state, district, pincode, bio_age_5_17, bio_age_17_ | Biometric updates |

## Getting Started

### Prerequisites
- Python 3.9+
- Jupyter Notebook
- Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`

### Run the Notebook

1. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```
2. Open the notebook:
   ```bash
   jupyter notebook aadhaar_analysis.ipynb
   ```
3. Update the `BASE_DIR` in the notebook to your local repository path so the CSV glob paths resolve correctly.
   - The notebook expects the nested data paths shown above.
   - `OUTPUT_DIR` is defined as `analysis_output`, but the charts are saved to the `Output/` directory via explicit save paths in the notebook.

## Outputs

Generated charts are stored in `Output/`, including:
- Univariate summaries (total enrolments, total state volume)
- Bivariate analysis (cross-sectional comparisons)
- Trivariate analysis (multi-dimensional trends)
  - Some shipped filenames use the spelling `enrolement` (matching the current notebook output names).

## Notes

- The project currently uses file-based CSV inputs shipped in this repository.
- No automated tests or build scripts are defined yet.
