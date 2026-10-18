---
layout: default
title: "Übung 4: Galerkin-Methode"
nav_order: 24
parent: Übungen
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Lösung der Poissongleichung mit der Galerkin-Methode

Die Poissongleichung (inhomogene Laplacegleichung) sei gegeben als

$$
\frac{\partial^2 u(x,y)}{\partial x^2}
+\frac{\partial^2 u(x,y)}{\partial y^2}=h(x,y)
\tag{eq:LaplaceInh}
$$

sei gegeben auf einem quadratischen Gebiet $$\Omega=[0,1]\times [0,1]$$.
Berechnen Sie deren Lösung unter den gegebenen Randbedingungen mittels eines
Galerkinverfahrens. Beachten Sie die Hinweise!

1. Es sei $$h(x,y)=0$$. Setzen Sie als Randbedingungen $$u(0,y)=0$$,
   $$\left.\frac{\partial u(x,y)}{\partial y}\right|_{y=0}=\left.\frac{\partial
   u(x,y)}{\partial y}\right|_{y=1}=0$$ und $$u(1,y)=1$$ an den Rändern fest. Wählen
   die eine geeignete Funktion $$u_0(x,y)$$, die die Randbedinungen erfüllt, machen
   Sie einen Ansatz $$u(x,y)=u_0(x,y)+\sum\limits_i u_i\phi_i(x,y)$$ und lösen Sie
   die Randwertaufgabe mit Hilfe der Galerkinmethode.
1. Wieder sei $$h(x,y)=0$$. Die Randbedingungen lauten  $$u(x=0,y)=u(x,y=0)=0$$,
   $$u(x=1,y)=y$$ und $$u(x,1)=x^2$$.
1. Setzen Sie Dirichlet-Randbedingungen
   $$u(x=0,y)=u(x,y=0)=u(x=1,y)=u(x,y=1)=0$$ an den Rändern fest. Geben Sie eine
   Lösung für den Fall $$h(x,y)=1$$ an und stellen Sie diese graphisch dar.


*Hinweise*
Allgemein setzen wir immer an: $$u(x,y)=u_0(x,y)+\sum\limits_i u_i\phi_i(x,y)$$

-[] Wählen Sie $$u_0$$ so, dass die Randbedingungen erfüllt sind. Wählen Sie
     dann die $$\phi_i(x,y)$$ so, dass diese auf dem Rändern wo Dirichletbedingungen
     vorliegen verschwinden und deren Ableitung dort verschwinden, wo Neumann
     Randbedingungen vorliegen, also z.B. $$\phi_i(x,y)=\sin(m_i\pi x)\cos(n_i\pi
     y)$$. Dann ergibt sich sofort die triviale Lösung für alle $$u_i=0$$, wenn $$u_0$$
     auch die Differentialgleichung erfüllt.
-[] In diesem Fall kann die Randbedingung als geschlossene Funktion angegeben
     werden: $$u_0(x,y)=x^2y$$.
-[] Was ist der Unterschied zum homogenen Randwertproblem?

