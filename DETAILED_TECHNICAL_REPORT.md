# Detailed 32-Group Multi-Cloud Ledger & Active-Space Molecular Chemistry Results

*Companion technical report to [`README.md`](README.md) in [`prometheus-circuit-complexity-atlas`](https://github.com/PrometheusDynamicsCanada/prometheus-circuit-complexity-atlas).*

## 1. Complete Un-Cherry-Picked 32-Group Live 3-Compiler Benchmark Ledger (`186` Completed Benchmark Jobs/Tasks, `1,407,488` Physical Shots)

Every completed 3-compiler benchmark executed through the Prometheus Execution Control Plane (`Nov 20-23, 2026`) is listed below in chronological order (`G01` to `G32`), including all `5` baseline wins (`G02`, `G03`, `G06`, `G26`, `G30`). Exact cloud Job IDs and AWS Braket Task ARNs are recorded in [`data/ALL_187_PILOT_CLOUD_JOBS_LEDGER.csv`](data/ALL_187_PILOT_CLOUD_JOBS_LEDGER.csv) and [`data/ALL_32_THREE_WAY_COMPARISONS.csv`](data/ALL_32_THREE_WAY_COMPARISONS.csv).

| ID | Processor | Family (`Max Q`, `Pack`) | SABRE $F_B$ `(↑)` | TKET $F_B$ `(↑)` | Prom $F_B$ `(↑)` | Mean `2Q` (`S / T / P`) `(↓)` | Prom Billed `(↓)` | Prom vs. Best Base `(↑)` |
| :---: | :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| `G01` | `iqm_emerald` | Molecular QWC & Conserved-Particle (`6Q`, `4w`) | `0.9675` | `0.9666` | **`0.9739`** | `3.0` / `3.0` / `3.0` | `3.0 credits` | `+0.66%` |
| `G02` | `ibm_kingston` | QAOA MaxCut (`9Q`, `4w`) | `0.9345` | `0.9243` | **`0.9457`** | `73.25` / `95.75` / `65.0` | `6.0 seconds` | `+1.20%` |
| `G03` | `ibm_fez` | Heterogeneous Dense + Star + QFT + QAOA (`15Q`, `1w`) | **`0.4554`** | `0.4089` | `0.3290` | `166.25` / `298.0` / `185.0` | `7.0 seconds` | `-27.76%` |
| `G04` | `ibm_kingston` | Heterogeneous Dense + Star + QFT + QAOA (`17Q`, `1w`) | **`0.6765`** | `0.6129` | `0.6732` | `196.5` / `346.75` / `177.75` | `11.0 seconds` | `-0.49%` |
| `G05` | `ibm_kingston` | Heterogeneous Dense + Star + QFT + QAOA (`17Q`, `2w`) | `0.6284` | `0.5859` | **`0.6748`** | `178.25` / `357.0` / `161.0` | `9.0 seconds` | `+7.38%` |
| `G06` | `ibm_kingston` | Molecular QWC & Conserved-Particle (`6Q`, `4w`) | `Halted ($0.00)` | `0.9609` | **`0.9664`** | `Halted` / `3.0` / `3.0` | `6.0 seconds` | `+0.57%` |
| `G07` | `iqm_emerald` | Dense All-to-All (K_N) (`7Q`, `1w`) | `0.8923` | `0.8526` | **`0.9236`** | `37.0` / `55.0` / `28.0` | `2.25 credits` | `+3.51%` |
| `G08` | `iqm_emerald` | Independent-Set / MIS (`6Q`, `2w`) | `0.9127` | **`0.9393`** | `0.9189` | `5.0` / `5.0` / `6.5` | `2.25 credits` | `-2.17%` |
| `G09` | `iqm_emerald` | Molecular QWC & Conserved-Particle (`6Q`, `4w`) | `0.9680` | `0.9690` | **`0.9743`** | `3.0` / `3.0` / `3.0` | `2.25 credits` | `+0.55%` |
| `G10` | `iqm_emerald` | Molecular QWC & Conserved-Particle (`6Q`, `4w`) | `0.9550` | `0.9552` | **`0.9747`** | `3.0` / `3.0` / `3.0` | `2.25 credits` | `+2.04%` |
| `G11` | `ibm_kingston` | Heterogeneous Dense + Star + QFT + QAOA (`15Q`, `2w`) | `0.5977` | `0.4209` | **`0.7401`** | `105.25` / `223.25` / `71.5` | `8.0 seconds` | `+23.82%` |
| `G12` | `ibm_kingston` | Heterogeneous Dense + Star + QFT + QAOA (`12Q`, `2w`) | `0.7357` | `0.7472` | **`0.7776`** | `71.25` / `123.25` / `69.0` | `7.0 seconds` | `+4.07%` |
| `G13` | `ibm_kingston` | Heterogeneous Dense + Star + QFT + QAOA (`50Q`, `2w`) | `0.6763` | `0.6719` | **`0.7965`** | `151.0` / `210.25` / `104.0` | `10.0 seconds` | `+17.77%` |
| `G14` | `ibm_kingston` | Heterogeneous Dense + Star + QFT + QAOA (`10Q`, `2w`) | `0.8632` | `0.9154` | **`0.9308`** | `58.75` / `73.5` / `53.25` | `8.0 seconds` | `+1.68%` |
| `G15` | `ibm_kingston` | Heterogeneous Dense + Star + QFT + QAOA (`50Q`, `1w`) | `0.7383` | `0.7311` | **`0.8206`** | `129.5` / `187.5` / `103.25` | `14.0 seconds` | `+11.15%` |
| `G16` | `ibm_kingston` | Molecular QWC & Conserved-Particle (`4Q`, `5w`) | `0.9911` | `0.9918` | **`0.9918`** | `3.0` / `3.0` / `3.0` | `8.0 seconds` | `+0.00%` |
| `G17` | `ibm_kingston` | Molecular QWC & Conserved-Particle (`6Q`, `1w`) | `0.9574` | `0.9647` | **`0.9749`** | `17.0` / `27.0` / `17.0` | `32.0 seconds` | `+1.06%` |
| `G18` | `iqm_emerald` | Central-Hub Star (K_{1,N-1}) (`13Q`, `1w`) | `0.3370` | `0.7248` | **`0.7903`** | `25.0` / `24.0` / `18.0` | `3.0 credits` | `+9.04%` |
| `G19` | `aws_rigetti_cepheus` | Central-Hub Star (K_{1,N-1}) (`13Q`, `1w`) | `0.1025` | `0.0860` | **`0.2622`** | `24.0` / `36.0` / `17.0` | `$7.97 USD` | `+155.80%` |
| `G20` | `ibm_fez` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `0.8486` | `0.8726` | **`0.9423`** | `13.0` / `11.0` / `8.0` | `6.0 seconds` | `+7.99%` |
| `G21` | `ibm_marrakesh` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `0.8626` | `0.7476` | **`0.8906`** | `11.0` / `11.0` / `14.0` | `6.0 seconds` | `+3.25%` |
| `G22` | `ibm_kingston` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `0.8982` | `0.9255` | **`0.9315`** | `13.0` / `10.0` / `8.0` | `6.0 seconds` | `+0.65%` |
| `G23` | `iqm_garnet` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `0.8309` | `0.8335` | **`0.9088`** | `7.0` / `12.0` / `7.0` | `1.0 credits` | `+9.03%` |
| `G24` | `aws_rigetti_cepheus` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `Halted ($0.00)` | `Halted ($0.00)` | **`0.7313`** | `Halted` / `Halted` / `12.0` | `$1.91 USD` | **Only Pass** |
| `G25` | `ibm_fez` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `0.8970` | `0.8709` | **`0.9451`** | `13.0` / `11.0` / `8.0` | `6.0 seconds` | `+5.36%` |
| `G26` | `ibm_kingston` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `0.9149` | `0.9145` | **`0.9360`** | `13.0` / `10.0` / `8.0` | `6.0 seconds` | `+2.31%` |
| `G27` | `ibm_marrakesh` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | **`0.9127`** | `0.5323` | `0.8469` | `11.0` / `11.0` / `14.0` | `6.0 seconds` | `-7.21%` |
| `G28` | `iqm_garnet` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `0.8219` | `0.8357` | **`0.9068`** | `7.0` / `12.0` / `7.0` | `1.0 credits` | `+8.51%` |
| `G29` | `aws_rigetti_cepheus` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `0.2565` | `0.4006` | **`0.7439`** | `12.0` / `12.0` / `12.0` | `$1.91 USD` | `+85.70%` |
| `G30` | `iqm_garnet` | Central-Hub Star (K_{1,N-1}) (`3Q`, `1w`) | **`0.9782`** | `0.9717` | `0.9762` | `2.0` / `2.0` / `2.0` | `1.0 credits` | `-0.20%` |
| `G31` | `iqm_garnet` | Central-Hub Star (K_{1,N-1}) (`7Q`, `1w`) | `0.8768` | `0.8938` | **`0.9208`** | `6.33` / `7.33` / `6.0` | `2.0 credits` | `+3.02%` |
| `G32` | `iqm_garnet` | Central-Hub Star (K_{1,N-1}) (`10Q`, `1w`) | `0.6644` | `0.7799` | **`0.8383`** | `12.67` / `15.67` / `10.0` | `2.0 credits` | `+7.49%` |

---

## 2. Reconstructed Spin-Orbital Jordan-Wigner Molecular Chemistry Benchmarks (`G16` `4Q H2` & `G17` `6Q LiH`)

### Table 2A: `G16` - `4Q H2` `STO-3G` `5`-Way Spatial Packing Workflow on `IBM Kingston` (`N = 6` Jobs, `16,384` Packed HW Shots vs. `81,920` Baseline HW Shots)
- **IBM Job IDs:** SABRE `dc1csqts2omc738aeubg`, `dc1ct0eq4uuc73a3p0tg` (`26.0 s`); TKET `dc1csrqnj2vs73df6ce0`, `dc1ct46q4uuc73a3p120` (`26.0 s`); Prometheus `dc1csr2nj2vs73df6ccg`, `dc1ct0dhdvas73bklue0` (**`8.0 s`, `-69.23%` QPU time**).

| Metric (`0.74 A` Eq. + `1.50 A` Stretched, `10` `QWC` Circuits) | Qiskit SABRE O3 (`1`-Way) | Quantinuum TKET (`1`-Way) | Prometheus (`5`-Way Packed) | Prometheus Delta vs. Best Baseline |
| :--- | :---: | :---: | :---: | :---: |
| **Billed QPU Allocation (`IBM s`) `(↓)`** | `26.00 s` (`10` PUBs/wave) | `26.00 s` (`10` PUBs/wave) | **`8.00 s` (`2` PUBs/wave)** | **`-69.23%` billed QPU time (`-80.0%` HW shots)** |
| **`H2 (0.74 A)` `\|E_sym - E_FCI\| +/- SE` (`mHa`) `(↓)`** | `8.38 +/- 2.43` | `11.58 +/- 2.52` | **`4.46 +/- 2.22`** | **`-46.79%` lower error (`-3.92 mHa` vs. SABRE)** |
| **`H2 (1.50 A)` `\|E_sym - E_FCI\| +/- SE` (`mHa`) `(↓)`** | `18.03 +/- 2.24` | `21.67 +/- 2.23` | **`15.62 +/- 2.20`** | **`-13.38%` lower error (`-2.41 mHa` vs. SABRE)** |
| **Mean `\|E_meas - E_FCI\|` (`Sym` / `Raw QWC`, `mHa`) `(↓)`** | `13.20` / `53.69` | `16.62` / `73.78` | **`10.04` / `46.55`** | **`-23.98%` Sym / `-13.29%` Raw lower error** |

### Table 2B: `G17` - `6Q LiH Frozen-Core CAS(2e,3o)` Matched `1`-Way Hardware Run on `IBM Kingston` (`N = 6` Jobs, `106,496` Shots/Arm, Equal `32.0 s`)
- **IBM Job IDs:** SABRE `dc1eme6q4uuc73a3r5cg`, `dc1emplhdvas73bko2l0`; TKET `dc1emf5hdvas73bko260`, `dc1en56q4uuc73a3r6e0`; Prometheus `dc1eme6q4uuc73a3r5d0`, `dc1en1lhdvas73bko2tg`.

| Metric (`R = 1.595 A`, `13` `QWC` Circuits, `E_FCI = -7.877185 Ha`) | Qiskit SABRE O3 (`1`-Way) | Quantinuum TKET (`1`-Way) | Prometheus (`1`-Way) | Prometheus Delta vs. Best Baseline |
| :--- | :---: | :---: | :---: | :---: |
| **Unmitigated Raw `QWC` Error `\|E_raw - E_FCI\| +/- SE` (`mHa`) `(↓)`** | `104.12 +/- 3.19` | `96.53 +/- 3.24` | **`82.32 +/- 3.12`** | **`-14.72%` vs. TKET (`-20.94%` vs. SABRE)** |
| **Off-Diagonal `X/Y` Correlation Error (`Circuits #2-#13`, `mHa`) `(↓)`** | `+6.87` | `+6.33` | **`+4.30`** | **`-32.07%` vs. TKET (`-37.41%` vs. SABRE)** |
| **`Z`-Basis Conserved `(1a, 1b)` Spin-Sector Retention `(↑)`** | `81.71%` | `84.07%` | **`88.24%`** | **`+4.17 pp` vs. TKET (`+6.53 pp` vs. SABRE)** |
| **`Z`-Postselected Error `\|E_sym - E_FCI\| +/- SE` (`mHa`) `(↓)`** | **`10.23 +/- 1.74`** | `11.97 +/- 1.81` | `13.98 +/- 1.84` | `+3.75 mHa` (`1.48 sigma` within shot SE; all `<= 14 mHa`) |
| **Distribution Overlap $F_B$ `*(mean)*` `(↑)` / `2Q` Gates `(↓)`** | `0.9574` / **`221`** | `0.9647` / `351` | **`0.9749`** / **`221`** | **`+1.06%` $F_B$ & `-37.04%` fewer `2Q` gates vs. TKET** |
