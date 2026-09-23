---
layout: default
title: "Übung 2: Lineares Randwertproblem"
nav_order: 22
parent: Übungen
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Lineares Randwertproblemes
To model this, we can use the **1D Steady-State Heat Equation**. 

Imagine a wall of thickness $L$ (where the interval is $[0, L]$). 
*   At $x=0$, the wall is connected to the interior of a heated room.
*   At $x=L$, the wall meets a window/exterior surface where heat is lost to the outside air via convection.

### 1. Mathematical Formulation

**The Differential Equation:**
For steady-state heat conduction with no internal heat generation ($g(x)=0$), the equation simplifies to:
$$k \frac{d^2T}{dx^2} = 0$$
Here, $a_2(x) = k$ (thermal conductivity), $a_1=0, a_0=0, g(x)=0$.

**The Boundary Conditions:**
1.  **Dirichlet at $x=0$ (Inside wall):** The temperature is held constant by the room's heater.
    $$T(0) = T_{room}$$
2.  **Robin at $x=L$ (Window/Outside surface):** According to **Newton's Law of Cooling**, the heat flux leaving the wall must equal the heat transferred to the outside air via convection.
    $$-k \frac{dT}{dx}\bigg|_{x=L} = h(T(L) - T_{out})$$
    Rearranging to the form $U_2[T(L)] = \gamma_2$:
    $$k T'(L) + h T(L) = h T_{out}$$
    *(Where $h$ is the convective heat transfer coefficient).*

