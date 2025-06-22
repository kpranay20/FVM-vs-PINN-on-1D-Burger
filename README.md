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

- The PINN solution closely approximates the FVM solution in smooth regions of the domain:
  
  ![image](https://github.com/user-attachments/assets/e78f08e3-9222-4256-84e5-45bdd447f9dd)
  ![image](https://github.com/user-attachments/assets/bc7690bc-7f71-478d-8c95-77ac519427ae)

- Discrepancies between PINN and FVM appear near steep gradients or quasi-shock-like structures:
  
  ![image](https://github.com/user-attachments/assets/3b024679-8fc0-4a66-8878-ca6e55aeb7e9)
  ![image](https://github.com/user-attachments/assets/1a93fcb8-9c85-4887-8c99-ccf3c2458a35)

- In each of the above images, first image represents the solution by FVM while the second image represents the solution by PINN.
  
