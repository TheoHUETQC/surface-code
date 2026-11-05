# Surface Code & Quantum Error Correction with Qiskit

This GitHub repository contains practical work and notebooks dedicated to the study of **surface codes** and **quantum error correction** implemented using **Qiskit**.

---

## 1. Principle of a Surface Code
Physical quantum computers are extremely sensitive to environmental noise (decoherence, fluctuations). The **surface code** is one of the most robust topological architectures to achieve fault tolerance. 
Its principle consists in encoding the information of a **logical qubit** within a two-dimensional grid (a 2D lattice) composed of a large number of **physical qubits** (for example, 17 qubits for a distance $d=3$). This allows errors to be detected and corrected locally using only interactions between neighboring qubits.

## 2. What is a Stabilizer? (Definition)
Since the no-cloning theorem prevents copying a quantum state to check if it has been altered, we use the **stabilizer formalism**:
* **Definition:** A stabilizer is a multi-qubit Pauli operator (typically measured on a plaquette of 4 data qubits around an ancilla qubit) that leaves the logical state invariant ($g |\psi_L\rangle = +1 |\psi_L\rangle$).
* **Role:** 
  * **$Z$ plaquettes ($Z^{\otimes 4}$)** measure phase parity and detect **Bit-flip ($X$)** errors.
  * **$X$ plaquettes ($X^{\otimes 4}$)** measure bit parity and detect **Phase-flip ($Z$)** errors.
* **Non-destructive measurement:** Using ancilla qubits and logic gates (CNOT, Hadamard), we extract an **error syndrome** ($\pm 1$ values) without collapsing or destroying the quantum state of the data.

---

## 3. Repository Contents (Notebooks)

### Current Notebook:
* **`surface_code_introduction.ipynb`** : 
  Step-by-step implementation of a distance $d=3$ planar surface code (17 physical qubits). This notebook covers:
  * Modeling the 2D geometric topology (data and ancilla qubits).
  * Creating syndrome extraction circuits for $X$ and $Z$ stabilizers.
  * Artificially injecting Pauli errors ($X$, $Z$, $Y$).
  * Simulation using Qiskit (`AerSimulator`) and implementing a classical decoder via a **Look-up Table**.

* **`machine_learning_decoder_for_surface_codes.ipynb`** *(in progress)* : 
  I would like to work on using Machine Learning methods (PyTorch MLP) to replace the classical look-up table, allowing us to handle complex syndromes and correct multiple errors with a weight greater than 1.

### Future Notebooks (Upcoming Projects):
* **Google Quantum AI - Scaling & Fault Tolerance Notebook** *(Coming Soon)* : 
  I would like to reproduce and analyze the results of Google's landmark 2023 paper on the suppression of logical errors through surface code scaling.

---

## References

- **An introduction to the surface code** 
  Andrew N. Cleland, *University of Chicago, Chicago IL 60637, USA* (SciPost Phys. Lect. Notes 49 (2022) · published 3 May 2022).
- **Quantum Computation and Error-Control Codes** (Master 2) 
  Course by Yunos EL KADERI.
- **IBM Qiskit documentation** 
  [https://quantum.cloud.ibm.com/docs/en/guides](https://quantum.cloud.ibm.com/docs/en/guides)
- **Suppressing quantum errors by scaling a surface code logical qubit** 
  Research article by Google Quantum AI (2023).
- **Machine Learning for Physics** (2025-2026) 
  Midlands Physics Alliance Graduate School (MPAGS): Course Module, Access: [https://warwick.ac.uk/fac/sci/physics/mpags/modules/comp/machinelearning/25-26/](https://warwick.ac.uk/fac/sci/physics/mpags/modules/comp/machinelearning/25-26/)
- **PyTorch documentation** [https://docs.pytorch.org/docs/main/](https://docs.pytorch.org/docs/main/)