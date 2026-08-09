# Manufacturing Analytics & IIoT — Technical Portfolio

A from-scratch, public demonstration of manufacturing analytics concepts relevant to Industrial IoT, smart manufacturing, and HPDC process monitoring.

## Important disclosure

This repository is an **independent portfolio demonstration**.

- All data in `data/` is synthetic and generated specifically for this repository.
- No UNO Minda production data is included.
- No NEEV presentation, internal document, source code, machine configuration, supplier information, credentials, dashboard export, or proprietary architecture is included.
- The repository is intentionally written so that the methods can be demonstrated without exposing confidential company information.

The repository is inspired by manufacturing analytics work I have encountered in an Industry 4.0 context, but it is **not an official UNO Minda or NEEV repository**.

## What this demonstrates

The project demonstrates a manufacturing-data workflow covering:

1. Data preparation
2. Correlation analysis
3. Feature standardisation
4. PCA
5. K-Means clustering
6. Isolation Forest anomaly detection
7. SPC-style statistical limits
8. Process-drift scoring
9. Association-rule analysis
10. Dashboard-oriented visualisation

## Architecture

```text
Synthetic machine/process data
            |
            v
      Data preparation
            |
            +----> Correlation analysis
            |
            +----> PCA + K-Means
            |
            +----> Isolation Forest
            |
            +----> SPC limits
            |
            +----> Association rules
            |
            v
      Process-drift indicators
            |
            v
      Streamlit dashboard
```

## Dataset

`data/synthetic_hpdc_data.csv` contains 1,200 synthetic production-shot records.

Example variables:

- cycle time
- cast pressure
- Hi-V
- P-rise
- filling time
- biscuit thickness
- die temperature
- shot weight
- synthetic reject indicator

The values are generated mathematically and are **not copied from industrial production records**.

## Run locally

### 1. Create an environment

```bash
python -m venv .venv
```

Activate it:

**Windows**
```bash
.venv\Scripts\activate
```

**Linux/macOS**
```bash
source .venv/bin/activate
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the analytics pipeline

```bash
python src/analysis_pipeline.py
python src/association_rules_demo.py
```

Generated files are written to `outputs/`.

### 4. Launch the dashboard

```bash
streamlit run dashboard/app.py
```

## Technical notes

### Correlation

Correlation is used as an initial screening step to understand relationships between process variables and reduce redundant features.

### PCA

Principal Component Analysis provides a lower-dimensional representation of the standardised process space.

### K-Means

K-Means groups process shots into operating-regime clusters. The repository reports the silhouette score as a simple cluster-quality indicator.

### Isolation Forest

Isolation Forest identifies observations that are relatively isolated in the multidimensional process space.

### SPC

The demonstration calculates conventional mean ± 3σ limits for selected variables. These are illustrative statistical limits and should not be interpreted as validated production control limits.

### Process drift

A simple baseline-distance score is used to flag observations that move away from the initial operating distribution.

### Association analysis

The association-rule demonstration bins process variables into low/high conditions and calculates support, confidence, and lift.

## Limitations

This is a portfolio demonstration rather than a production manufacturing system.

A production deployment would require:

- validated machine-data interfaces
- sensor/data-quality checks
- domain-approved control limits
- traceable quality labels
- MES integration
- model validation and monitoring
- cybersecurity controls
- governance and change management

## Author

**Athul Suresh**  
Mechatronics Engineer | Industrial IoT | Smart Manufacturing | Robotics

This repository is intended to demonstrate technical thinking and implementation skills in manufacturing analytics and Industry 4.0.
