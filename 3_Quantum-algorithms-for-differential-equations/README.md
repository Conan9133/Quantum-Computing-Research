# Quantum Algorithms for Differential Equations

This folder contains exploratory implementations of quantum algorithms for differential equations and dynamical systems, with a focus on Variational Quantum Linear Solver (VQLS)-based time stepping.

The goal is not to claim quantum advantage, but to study how VQLS behaves as a local linear solver inside time-stepping algorithms and to identify limitations such as conditioning, cost-function choice, ansatz design, optimizer behaviour, nonlinear error accumulation, and output/readout constraints.

## Contents

| Notebook | Description |
|---|---|
| `01_VQLS_linear_pendulum.ipynb` | VQLS-based time stepping for the linear pendulum. |
| `02_VQLS_nonlinear_pendulum.ipynb` | VQLS-based time stepping for the nonlinear pendulum using a stepwise treatment of the nonlinear term. |
| `03_nonlinear_ode_linearization_methods.ipynb` | Classical exploration of explicit stepwise methods, Newton iteration, Carleman linearization, and Koopman-type linearization. |
| `04_VQLS_limitations_noiseless.ipynb` | Noiseless VQLS limitations: condition number, cost functions, ansatz depth, residuals, and optimizer behaviour. |
| `05_classical_LBM_D1Q3_diffusion.ipynb` | Classical D1Q3 lattice Boltzmann method for diffusion, implemented to understand the collision-streaming structure. |
| `06_LCU_linear_pendulum.ipynb` | Linear Combination of Unitarities (LCU)-based operator-evolution methods for Linear pendulum. |

## Under preparation

| Notebook | Description |
|---|---|
| `07_VQLS_lorenz_system.ipynb` | VQLS applied to the Lorenz system as a nonlinear chaotic stress test. |
| `08_LCU_nonlinear_pendulum.ipynb` | LCU-based operator-evolution methods for pendulum-type systems. |
| `09_Block_encoding_linear_and_nonlinear_pendulum.ipynb` | Block-encoding-based approaches for linear and nonlinear pendulum examples. |

## Main lessons

- VQLS can reproduce small classical time-stepping benchmarks in controlled regimes.
- Conditioning affects VQLS performance, but does not explain all errors.
- Nonlinear systems introduce error feedback through the evolving right-hand side.
- Ansatz architecture matters; for example, circular entanglement can improve performance in coupled systems.
- Lower optimizer iteration count does not necessarily mean better performance; it must be interpreted together with final cost, fidelity, and residuals.
- Full statevector reconstruction is used only for small-scale validation and is not scalable.
- Scalable quantum differential-equation algorithms should focus on observable extraction or methods that avoid full readout.

## Scope and limitations

These notebooks are small-scale exploratory studies. They are intended to validate formulations, compare diagnostics, and understand algorithmic limitations of VQLS-based time stepping.

They do not demonstrate quantum advantage. In the current simulations, full statevector reconstruction is used for validation because the systems are small. For large-scale quantum algorithms, one would need to extract selected observables or functionals of the solution state, rather than reconstructing the full solution vector.

## Requirements

The notebooks use:

- Python
- NumPy
- SciPy
- Pandas
- Matplotlib
- Qiskit
- Qiskit Aer

A typical installation is:

```bash
pip install numpy scipy pandas matplotlib qiskit qiskit-aer

## Acknowledgement

The notebooks on LCU and Block-encoding methods benefited from discussions within our summer research group. Especially, Diego's notes helped me understand the circuit-level implementation of the LCU and block-encoding methods. The implementation and presentation here were written independently, and any errors or interpretations are my own.

