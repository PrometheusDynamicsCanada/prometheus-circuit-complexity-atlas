# Data Dictionary (`prometheus-circuit-complexity-atlas`)

## 1. `data/ALL_187_PILOT_CLOUD_JOBS_LEDGER.csv`
- `record_index`: Sequential record index (`1..187`).
- `hardware_job_id`: Verifiable IBM Quantum Job ID, IQM Resonance Job UUID, or AWS Braket Quantum Task ARN (`0` duplicates across all `14` quantum repositories).
- `provider` / `backend_name`: Cloud provider (`ibm`, `iqm`, `aws`) and physical QPU (`ibm_fez`, `ibm_kingston`, `ibm_marrakesh`, `iqm_emerald`, `iqm_garnet`, `aws_rigetti_cepheus`).
- `record_role`: `benchmark` (`186` completed hardware executions) or `auxiliary_cancelled` (`1` cancelled IQM job `01a1f5e1-db66-7245-9aff-f8c80e4da662` with `0` benchmark shots).
- `compiler_arm`: `Qiskit_SABRE_O3`, `Quantinuum_TKET`, or `Prometheus`.
- `wave`: `primary` or `confirmation` independent hardware wave.
- `pack_factor` / `physical_pubs` / `physical_shots`: Spatial packing factor, physical PUBs executed in that cloud job, and physical QPU shots (`1,407,488` total benchmark physical shots; never multiplied by unpacked subcircuit count).

## 2. `data/ALL_32_THREE_WAY_COMPARISONS.csv` & `data/COMMON_DENOMINATOR_SUMMARY.json`
- Contains all `32` head-to-head 3-compiler benchmark groups (`G01..G32`) with full observables (`F_B`, `F_H`, `TVD`, `HOP`, `XEB`, `Shannon Entropy`), structural metrics (`mean_compiled_two_q_gates`, `mean_compiled_depth`), settled native billing units, and common-denominator aggregations across scientific domain, width tier (`3Q-7Q`, `8Q-10Q`, `12Q-17Q`), QPU processor, and `1`-way vs. multi-way spatial packing.

## 3. `data/LOGICAL_BENCHMARK_CIRCUITS_AND_HISTOGRAMS.json`
- Unrouted logical OpenQASM 2.0 circuits and raw measured bitstring histograms (`primary_per_circuit`, `confirm_per_circuit`) used by `scripts/verify_complexity_atlas.py` to recompute $F_B$ from scratch.
