# n-bit Superdense Coding Protocol

© 2025 Saba Arife Bozpolat. 
This dataset is licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0).
Commercial use is not permitted.

# JSON Data File Outlines

1. fez_metadata_n_*
    - `job_id`: unique identifier assigned to this job submission by IBM Quantum / Qiskit Runtime
    - `backend`: name of the quantum hardware used ("ibm_fez")
    - `status`: completion status of the job ("DONE")
    - `metrics.caller`: the software component that submitted the job (qiskit_ibm_runtime sampler)
    - `metrics.qiskit_version`: version information of the qiskit packages used
    - `metrics.timestamps.created/running/finished`: lifecycle timestamps of the job
    - `metrics.bss.seconds`: —
    - `metrics.usage.quantum_seconds`: —
    - `metrics.usage.seconds`: —
    - `timestamp`: local timestamp of the run (file-naming format)
    - `n`: message length / number of qubits for this run
    - `shots`: number of times each circuit was executed (4096)

2. fez_layouts_n_*
    - each key (message bitstring) → list of physical qubit indices selected by the transpiler for that message

3. fez_exec_stats_n_*
    - `depth`: circuit depth after transpilation
    - `gate_count`: total gate count after transpilation
    - `gate_counts_detail`: breakdown by gate type (`rz`, `sx`, `cz`, `x`, `measure`, `barrier` → count)

4. fez_counts_raw_n_*
    - each key (transmitted message) → raw counts of observed output bitstrings across 4096 shots

5. fez_counts_mitigated_n_*
    - each key (transmitted message) → output bitstring counts after readout error mitigation (matrix-inversion correction), fractional, non-negative, renormalized

6. fez_readout_errors_n_*
    - each key (physical qubit index, "0"–"155") → that qubit's readout error probability

7. fez_readout_data_n_*
    - `readout_error`: overall readout error probability of the qubit
    - `prob_meas0_prep1`: probability of measuring "0" when the qubit was prepared in $|1\rangle$
    - `prob_meas1_prep0`: probability of measuring "1" when the qubit was prepared in $|0\rangle$
  
