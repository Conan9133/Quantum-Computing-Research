# Quantum Algorithms for Differential Equations

This folder contains exploratory implementations of quantum algorithms for differential equations and dynamical systems, with a focus on VQLS-based time stepping.

The goal is not to claim quantum advantage, but to study how VQLS behaves as a local linear solver inside time-stepping algorithms and to identify limitations such as conditioning, cost-function choice, ansatz design, optimizer behavior, nonlinear error accumulation, and output/readout constraints.

## Contents

| Notebook | Description |
|---|---|
| `01_vqls_linear_pendulum.ipynb` | VQLS-based time stepping for the linear pendulum. |
| `02_vqls_nonlinear_pendulum.ipynb` | Nonlinear pendulum using stepwise treatment of the nonlinear term. |
| `03_nonlinear_ode_linearization_methods.ipynb` | Classical exploration of explicit, Newton, Carleman, and Koopman-type linearization methods. |
| `04_vqls_lorenz_system.ipynb` | VQLS applied to the Lorenz system as a nonlinear chaotic stress test. |
| `05_vqls_limitations_noiseless.ipynb` | Noiseless VQLS limitations: condition number, cost functions, ansatz depth, and residuals. |
| `06_classical_lbm_d1q3_diffusion.ipynb` | Classical D1Q3 lattice Boltzmann method for diffusion. |

## Main lessons

- VQLS can reproduce small classical time-stepping benchmarks in controlled regimes.
- Conditioning affects VQLS performance, but does not explain all errors.
- Nonlinear systems introduce error feedback through the evolving right-hand side.
- Ansatz architecture matters; for example, circular entanglement can improve performance in coupled systems.
- Full statevector reconstruction is used only for small-scale validation and is not scalable.
- Scalable quantum differential-equation algorithms should focus on observable extraction or methods that avoid full readout.

## Requirements

Python, NumPy, SciPy, Pandas, Matplotlib, Qiskit, and Qiskit Aer.

## Notes

These notebooks are exploratory research-code examples. They are intended for validation, diagnostics, and studying algorithmic limitations rather than demonstrating quantum advantage.
