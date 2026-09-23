---
layout: default
title: "Übung 2: Lineares Randwertproblem"
nav_order: 22
parent: Übungen
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Lineares Randwertproblem mit der **1D-stationären Wärmeleitungsgleichung**.

Wir stellen uns eine Wand der Dicke $$L$$ vor (das Intervall ist $$[0, L]$$).
*   Bei $$x=0$$ ist der Raum mit einer verbunden, die eine feste Temperatur $$T_W$$ hat.
*   Bei $$x=L$$ ist der Raum mit einer Fensterfläche abgeschlossen, an der Wärme
    durch Konvektion an die Außenluft abgegeben wird.

### 1. Mathematische Formulierung

**Die Differentialgleichung:**
Für die stationäre Wärmeleitung ohne interne Wärmequellen ($$g(x)=0$$) vereinfacht sich die Gleichung zu:

$$\kappa \frac{d^2T}{dx^2} = 0$$

Hier ist $$a_2(x) = \kappa $$ die Wärmeleitfähigkeit der Raumluft, $$a_1=0, a_0=0$$ und $$g(x)=0$$.

**Die Randbedingungen:**
1.  **Dirichlet-Randbedingung bei $x=0$ (Innenwand):** Die Temperatur wird
    durch die Heizung im Raum konstant gehalten, $$T(0) = T_{Raum}$$

2.  **Robin-Randbedingung bei $x=L$ (Fenster/Außenfläche):** Nach dem
    **Newtonschen Abkühlungsgesetz** muss der Wärmestrom, der die Wand verlässt,
    gleich dem an die Außenluft abgegebenen Wärmestrom durch Konvektion sein.

$$-\kappa\frac{dT}{dx}\bigg|_{x=L} = K(T(L) - T_{außen})$$

$$\kappa T'(L) + K T(L) = K T_{außen}$$

*(Wobei $$K$$ der Wärmeübergangskoeffizient ist).*

### 2. Aufgabe
Skalieren Sie auf $$L=1$$ und $$\kappa[W/(mK)]=1[P/(L\cdot T_{Raum}]=$$ und
$$T_{Raum}=1$$. Wobei $$P$$ die Leistungseinheit ist. Damit haben wir
$$T=\Theta\cdot T_{Raum}$$ und $$x=\xi\cdot L$$. Somit lautet das
Randwertproblem

$$\frac{d^2\Theta}{d\xi^2} = 0$$

und mit $$ K/\kappa = h$$

$$\Theta(0) = 1$$ und $$\Theta'(1) + h \Theta(1) = h T_{außen}/T_{Raum}$$
