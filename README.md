# Multi-Cloud Circuit Width & Connectivity Comparison (3Q to 23Q)

*Portfolio Hub: [Prometheus Quantum Overview](https://github.com/PrometheusDynamicsCanada/prometheus-quantum-overview) · [Detailed Technical Report](DETAILED_TECHNICAL_REPORT.md) · [Data Dictionary](DATA_DICTIONARY.md)*

As quantum circuits widen and connect distant qubits, routing swaps accumulate and hardware output degrades. We tested how Prometheus compares against Qiskit SABRE O3 and Quantinuum TKET across six cloud processors (IBM Fez, Kingston, and Marrakesh; IQM Emerald and Garnet; and Rigetti Cepheus-1-108Q on Amazon Braket) from 3 to 23 qubits.

Across 36 completed three-compiler benchmark groups, Prometheus ranked first in 30 of 36 comparisons (83.3%), improving average output agreement by 9.00% over the strongest overall baseline (TKET) and 9.63% over SABRE, while two additional groups halted pre-flight at $0.00 when a baseline targeted a disabled hardware qubit. Highlights include 33.8% to 36.9% lower 8-qubit linear H4 active-space energy error on IQM Emerald (plus 21.4% lower credit cost when packed 3-way) and 4 of 4 verified passes on 10-qubit matchgate circuits on IBM Kingston (+9.76% vs. TKET).

On small 3-qubit circuits all three compilers tied near 0.98; baselines won 6 of 36 completed groups (5 SABRE, 1 TKET), simultaneous 3-way H4 packing traded +11.8 mHa crosstalk for lower credit spend, and above 20 qubits on dense all-to-all circuits hardware noise reduced absolute agreement across every compiler.

This repository contains the circuits, raw measurements, and offline verification tools from 224 completed benchmark jobs and tasks (225 total provider records, 1.78 million measurement shots).

![As non-local circuits widen, Prometheus retains higher output-distribution agreement](assets/fig0_simple_scaling_absolute_and_gain.png)
*Summary figure: Average output agreement (0 to 1.0) and percent gain versus the strongest baseline across 3-to-13-qubit star and 7-to-23-qubit dense all-to-all circuits on 156-qubit IBM Heron processors.*

**[Read the detailed results](#detailed-results) · [Verify the data](#verify-the-data) · [Request an evaluation](https://prometheusdynamics.ca/connect/) · [Book a demonstration](mailto:william@prometheusdynamics.ca?subject=Prometheus%20Evaluation)**

---

<a id="detailed-results"></a>
## Executive Summary (`36` Completed 3-Way Groups + `2` Pre-Flight Baseline Halts = `38` Groups, `1,782,272` Shots)

*Hardware IDs:* `112` IBM (`dbvuld2nj2vs73dd6g10`..`dc27p8qnj2vs73dg9hng`), `99` IQM (`01a1f5e1-db66..`..`01a20cb2-6aed..`), and `14` AWS Braket Rigetti tasks (`064ec617..`..`f245e7e9..`). Exact *(mean)* across all `36` completed 3-arm groups (kept separate from `G06` & `G24` where a stock baseline targeted a disabled qubit and halted pre-flight at `$0.00`):

| Compiler (`36` Completed 3-Way Groups) | Output-Distribution Agreement $F_B$ `(↑)` | Squared Hellinger $F_H$ `(↑)` | `HOP` `(↑)` | `TVD` `(↓)` | `XEB` `(↑)` | Entropy `(↓)` | `2Q` Gates / Depth `(↓)` | Completed `#1` Wins (`36` Groups) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Qiskit SABRE O3** | `0.7610` | `0.6332` | `0.6382` | `0.3855` | `170.5` | `5.22` | `47.11` / `55.78` | `5 / 36` (`13.9%`) |
| **Quantinuum TKET** | `0.7654` | `0.6353` | `0.6395` | `0.3824` | `211.6` | `5.30` | `72.69` / `64.81` | `1 / 36` (`2.8%`) |
| **Prometheus** | **`0.8343`** | **`0.7274`** | **`0.7252`** | **`0.2909`** | **`303.7`** | **`4.71`** | **`42.60` / `50.80`** | **`30 / 36` (`83.3%`; `32/38` incl. `2` halts)** |

*Metric Key:* Output-distribution agreement is Classical Bhattacharyya Overlap $F_B = \sum_x \sqrt{P_{\text{ideal}}(x)P_{\text{meas}}(x)}$ (labeled `"State Fidelity"` in Studio UIs); Squared Hellinger Fidelity is $F_H = F_B^2$. `(↑)` higher is better, `(↓)` lower is better.

---

<a id="verify-the-data"></a>
## Inspect the Evidence & Reproduce Supported Checks Offline

- **Command:** `python scripts/verify_complexity_atlas.py`
- **Dependencies & measured runtime:** Python 3 + `numpy` (`qiskit` optional for live OpenQASM statevector simulation; **`~1.29 s`** measured runtime with `qiskit` installed, `0` cloud credentials; verifies all `225` unique cloud IDs, `112` completed arms, and SHA-256 digests).
- **Request an evaluation or book a demonstration:** [prometheusdynamics.ca/connect](https://prometheusdynamics.ca/connect/) | [william@prometheusdynamics.ca](mailto:william@prometheusdynamics.ca?subject=Prometheus%20Evaluation)


*Release note (`v2026.11.24`):* Expanded archive from 187 to 225 unique cloud records (224 completed benchmark jobs/tasks + 1 cancelled auxiliary record; 38 three-compiler groups; 1.78M shots), adding 8Q Linear H4 STO-3G cohorts on IQM Emerald and 10Q QC-AFQMC matchgate cohorts on IBM Kingston and IQM Emerald.

---

## Deep-Dive Common-Denominator Tables & Scientific Multi-Panel Figures

<details>
<summary><strong>1. Common-Denominator Slices Across Family, Width Tier, QPU & Isolation Mode - Click to expand</strong></summary>

*(Note: Group win denominators below reflect all `38` groups; in `G06` [`ibm_kingston` chemistry] stock SABRE halted pre-flight at `$0.00` while TKET [`0.9609`] and Prometheus [`0.9664`] completed, and in `G24` [`aws_rigetti_cepheus` `7Q` Star] both stock baselines targeted isolated `q[49]` and halted at `$0.00` while Prometheus [`0.7313`] completed; *(mean)* columns average completed 3-way arms.)*

| Common-Denominator Slice | `#1` Wins `(↑)` | SABRE $F_B$ *(mean)* `(↑)` | TKET $F_B$ *(mean)* `(↑)` | Prom $F_B$ *(mean)* `(↑)` | Mean `2Q` Gates (`S / T / P`) `(↓)` | `% F_B Delta vs. Best Baseline (S / T)` `(↑)` |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Family: Star-Hub (`K_{1,N-1}`, `3Q-13Q`)** | **`13 / 15` (`86.7%`)** | `0.7287` | `0.7421` | **`0.8457`** | `12.14` / `13.21` / **`9.93`** | **`+13.96%` vs. best** (`+16.05%` S / `+13.96%` T) |
| **Family: Chemistry (`H2`, `LiH`, `Linear H4`)** | **`9 / 9` (`100.0%`)** | `0.9237` | `0.9347` | **`0.9482`** | **`17.50`** / `21.38` / `20.48` | **`+1.44%` vs. best** (`+2.65%` S / `+1.44%` T) (`-21.4%` to `-69.2%` packed) |
| **Family: `10Q QC-AFQMC` Matchgate Quartet** | **`2 / 3` (`66.7%`)** | `0.5648` | `0.6253` | **`0.6934`** | `71.33` / `95.17` / **`68.83`** | **`+10.90%` vs. best** (`+22.77%` S / `+10.90%` T) (`+9.76%` `4/4` on Kingston) |
| **Family: Multi-Family Batches (`8Q-17Q`)** | **`6 / 8` (`75.0%`)** | `0.6714` | `0.6368` | **`0.7178`** | `132.09` / `227.44` / **`115.59`** | **`+6.91%` vs. best** (`+6.91%` S / `+12.73%` T) |
| **Family: Dense All-to-All (`7Q K_7`, `Emerald`)** | **`1 / 1` (`100.0%`)** | `0.8923` | `0.8526` | **`0.9236`** | `37.00` / `55.00` / **`28.00`** | **`+3.51%` vs. best** (`+3.51%` S / `+8.33%` T) |
| **Family: Combinatorial (`QAOA` & `MIS`)** | `1 / 2` (`50.0%`) | `0.9236` | `0.9318` | **`0.9323`** | `39.12` / `50.38` / **`35.75`** | **`+0.05%` vs. best** (`+0.94%` S / `+0.05%` T) |
| **Width Tier: Small (`3Q-7Q`)** | **`17 / 20` (`85.0%`)** | `0.8746` | `0.8577` | **`0.9267`** | `9.96` / `11.57` / **`8.75`** | **`+5.96%` vs. best** (`+5.96%` S / `+8.05%` T) |
| **Width Tier: Medium (`8Q-10Q`)** | **`8 / 9` (`88.9%`)** | `0.7452` | `0.7917` | **`0.8323`** | `52.19` / `66.94` / **`52.17`** | **`+5.13%` vs. best** (`+11.69%` S / `+5.13%` T) |
| **Width Tier: Frontier (`12Q-17Q`)** | **`7 / 9` (`77.8%`)** | `0.5498` | `0.5544` | **`0.6516`** | `116.33` / `200.67` / **`100.72`** | **`+17.53%` vs. best** (`+18.52%` S / `+17.53%` T) |
| **QPU: AWS `Rigetti Cepheus-1` (`108Q`)** | **`3 / 3` (`100.0%`)** | `0.1795` | `0.2433` | **`0.5030`** | `18.00` / `24.00` / **`14.50`** | **`+106.76%` vs. best** (`+180.25%` S / `+106.76%` T) |
| **QPU: `IBM Kingston` (`156Q`)** | **`13 / 14` (`92.9%`)** | `0.7763` | `0.7800` | **`0.8461`** | `84.21` / `139.60` / **`71.10`** | **`+8.47%` vs. best** (`+8.98%` S / `+8.47%` T) |
| **QPU: `IQM Emerald` (`54Q`)** | **`9 / 11` (`81.8%`)** | `0.7998` | `0.8345` | **`0.8660`** | **`28.73`** / `33.00` / `29.03` | **`+3.78%` vs. best** (`+8.29%` S / `+3.78%` T) |
| **QPU: `IQM Garnet` (`20Q`)** | **`4 / 5` (`80.0%`)** | `0.8344` | `0.8629` | **`0.9102`** | `7.00` / `9.80` / **`6.40`** | **`+5.48%` vs. best** (`+9.08%` S / `+5.48%` T) |
| **QPU: `IBM Fez` (`156Q`)** | **`2 / 3` (`66.7%`)** | `0.7337` | `0.7175` | **`0.7388`** | **`64.08`** / `106.67` / `67.00` | **`+0.70%` vs. best** (`+0.70%` S / `+2.97%` T) |
| **QPU: `IBM Marrakesh` (`156Q`)** | `1 / 2` (`50.0%`) | **`0.8877`** | `0.6400` | `0.8687` | **`11.00`** / **`11.00`** / `14.00` | `-2.13%` vs. best (`-2.13%` S / `+35.75%` T) |
| **Mode: `Matched 1-Way` (`0` Packing)** | **`20 / 25` (`80.0%`)** | `0.7209` | `0.7330` | **`0.8100`** | `41.84` / `61.36` / **`39.45`** | **`+10.49%` vs. best** (`+12.36%` S / `+10.49%` T) |
| **Mode: `Multi-Way Packed` (`2w-5w`)** | **`12 / 13` (`92.3%`)** | `0.8413` | `0.8300` | **`0.8831`** | `57.65` / `95.33` / **`48.90`** | **`+4.96%` vs. best** (`+4.96%` S / `+6.39%` T) |

</details>

<details>
<summary><strong>2. Full Scientific Figures (3-Panel Best-Baseline Atlas & Simultaneous 5-QPU Matrix) + Dense K_N Table - Click to expand</strong></summary>

![Detailed 3-Panel Non-Local Scaling Atlas](assets/fig1_nonlocal_scaling_star_and_dense_kn.png)

![Simultaneous 5-QPU Cross-Cloud Benchmark Matrix](assets/fig2_simultaneous_5qpu_cross_cloud_matrix.png)

| Width Bin (`N = 69` Completed 3-Way `IBM Heron` `K_N` Jobs) | SABRE $F_B$ *(mean)* `(↑)` | TKET $F_B$ *(mean)* `(↑)` | Prom $F_B$ *(mean)* `(↑)` | `% vs. Best Baseline` `(↑)` | Linear `XEB` *(mean)* (`S / T / P`) `(↑)` | `2Q` `CZ` Gates *(mean)* (`S / T / P`) `(↓)` |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **`7Q-8Q`** (`N = 4`) | `0.8049` | `0.7087` | **`0.8188`** | **`+1.73%`** (`1.02x` vs. S) | `12.4` / `9.8` / **`13.4`** | `66.0` / `87.8` / **`54.5`** |
| **`10Q-12Q`** (`N = 3`) | `0.5847` | `0.4292` | **`0.6628`** | **`+13.36%`** (`1.13x` vs. S) | `16.0` / `9.2` / **`21.3`** | `153.0` / `221.3` / **`118.7`** |
| **`13Q-15Q`** (`N = 6`) | `0.3221` | `0.2142` | **`0.4122`** | **`+27.97%`** (`1.28x` vs. S) | `53.3` / `29.3` / **`83.4`** | `222.8` / `371.3` / **`184.0`** |
| **`16Q-17Q`** (`N = 10`) | `0.2004` | `0.1142` | **`0.2653`** | **`+32.39%`** (`1.32x` vs. S) | `128.1` / `37.3` / **`159.4`** | `333.0` / `496.0` / **`276.6`** |
| **`18Q-19Q`** (`N = 18`) | `0.1145` | `0.0482` | **`0.1792`** | **`+56.51%`** (`1.57x` vs. S) | `245.8` / `81.8` / **`406.8`** | `419.9` / `665.7` / **`360.6`** |
| **`20Q-21Q`** (`N = 17`) | `0.0396` | `0.0055` | **`0.0612`** | **`+54.55%`** (`1.55x` vs. S) | `224.3` / `20.1` / **`244.3`** | `520.6` / `848.8` / **`442.5`** |
| **`22Q-23Q`** (`N = 11`) | `0.0271` | `0.0013` | **`0.0390`** | **`+43.91%`** (`1.44x` vs. S) | `531.5` / `30.7` / **`738.4`** | `592.5` / `1042.6` / **`529.6`** |

*(Algorithmic context: Star-hub `K_{1,N-1}` graphs appear in Hadamard-test / `QC-AFQMC` trial overlaps, Quantum Phase Estimation `QPE`, non-local Jordan-Wigner Pauli exponentials, and `QEC` syndrome fanout; dense `K_N` and matchgate `SO(2N)` graphs appear in fermionic orbital rotations and `QFT`. Full chronological `G01`-`G38` ledger plus `4Q H2`, `6Q LiH`, `8Q Linear H4`, and `10Q Matchgate` tables are in [`DETAILED_TECHNICAL_REPORT.md`](DETAILED_TECHNICAL_REPORT.md).)*

</details>
