# Solving 1D Burgers' Equation: PINN vs FVM

This repository presents two different approaches to solving the 1D viscous as well as inviscid Burgers' equation:

- **Physics-Informed Neural Networks (PINNs)** — a deep learning-based method that incorporates the PDE and boundary conditions directly into the loss function.
- **Finite Volume Method (FVM)** — a classical numerical method based on conservation laws, commonly used for solving fluid dynamics problems.

The goal is to check how accurate PINNs are in comparison to traditional numerical methods like FVM, by solving the same PDE and comparing their solutions.

---

## Problem A Statement:

We solve the 1D viscous Burgers' equation:

$$
\frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} = \mu \frac{\partial^2 u}{\partial x^2}
$$

for $u = u(x,t)$, $x \in [-6, 6]$ at $t = 5.0s $, with the following initial and boundary conditions:
- Initial Condition: $u(x,0) = e^{-x^2/2}$
- Dirichlet Boundary Condition: $u(-6,t) = u(6,t) = 0 \forall t \in [0,5s]$ 

---
## Problem B Statement:

We solve the 1D inviscid Burgers' equation:

$$
\frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} = 0
$$

for $u = u(x,t)$, $x \in [-6, 6]$ at $t = 5.0s $, with the following initial and boundary conditions:
- Initial Condition: $u(x,0) = e^{-x^2/2}$
- Dirichlet Boundary Condition: $u(-6,t) = u(6,t) = 0 \forall t \in [0,5s]$ 

---

## Observations:

- The PINN solution closely approximates the FVM solution in **smooth regions** of the domain.
- Discrepancies between PINN and FVM appear near **steep gradients** or **quasi-shock-like structures**.

