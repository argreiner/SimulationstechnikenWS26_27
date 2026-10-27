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

Wir stellen uns einen Raum der Länge $$L$$ vor und es ist $$x\in[0, L]$$.
*   Bei der Länge $$x=0$$ ist der Raum durch eine Wand begrenzt, die eine feste
    Temperatur $$T_w$$ hat.
*   Bei $$x=L$$ ist der Raum mit einer Fensterfläche abgeschlossen, an der Wärme
    durch Konvektion an die Außenluft abgegeben wird.

### 1. Mathematische Formulierung

**Die Differentialgleichung:**
Für die stationäre Wärmeleitung ohne interne Wärmequellen ($$g(x)=0$$)
vereinfacht sich die Gleichung zu:

$$\kappa \frac{d^2T}{dx^2} = 0$$

Hier ist $$\kappa$$ die Wärmeleitfähigkeit der Raumluft, $$a_1=0, a_0=0$$ und
$$g(x)=0$$.

**Die Randbedingungen:**
1.  **Dirichlet-Randbedingung bei $$x=0$$ (Innenwand):** Die Temperatur wird
    durch die Heizung im Raum konstant gehalten, $$T(0) = T_w$$

2.  **Robin-Randbedingung bei $$x=L$$ (Fenster/Außenfläche):**
    Der Wärmestrom, der die Wand verlässt, muss gleich dem an die Außenluft
    abgegebenen Wärmestrom durch Konvektion sein.

$$-\kappa\frac{dT}{dx}\bigg|_{x=L} = K(T(L) - T_a)$$

$$\kappa T'(L) + K T(L) = K T_a$$,

wobei $$K$$ der *Wärmeübergangskoeffizient* ist und
$$T_a=0^\circ$$C$$=273.15K$$ die Außentmeperatur.

### 2. Aufgaben
Wählen Sie die Wärmeleitfähigkeit der Raumluft zu $$\kappa=0.026W/(mK)$$, die
Länge des Raumes zu $$L=5m$$ und die Temperatur der Wand zu
$$T_w=20^\circ$$C$$=293.15K$$.  

Das Fenster sei ein modernes Mehrscheibenfenster mit einem K-Wert von
$$K=1.0W/m^2/K$$. Nehmen Sie an das Fenster habe eine Fläche von $$A=1m^2$$. 
Wieviel Wärmeleistung geht durch die konvektive Randbedingung verloren?
1. Berechnen Sie die Lösung analytisch!
1. Berechnen Sie die Lösung mittels scipy.integrate.solve_bvp!
1. Berechnen Sie die Lösung mittels eines Finiten Differenzen Verfahrens!
1. Stellen Sie die Lösungen mit matplotlib.pyplot in einem Graph dar.
2. Wie realistisch ist dieses Modell?

## Abgabe bis 9.11.26 um 0000h auf ILIAS
