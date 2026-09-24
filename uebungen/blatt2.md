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
*   Bei der Länge $$x=0$$ ist der Raum mit einer Wand verbunden, die eine feste
    Temperatur $$T_w$$ hat.
*   Bei $$x=L$$ ist der Raum mit einer Fensterfläche abgeschlossen, an der Wärme
    durch Konvektion an die Außenluft abgegeben wird.

### 1. Mathematische Formulierung

**Die Differentialgleichung:**
Für die stationäre Wärmeleitung ohne interne Wärmequellen ($$g(x)=0$$) vereinfacht sich die Gleichung zu:

$$\kappa \frac{d^2T}{dx^2} = 0$$

Hier ist $$a_2(x) = \kappa $$ die Wärmeleitfähigkeit der Raumluft, $$a_1=0, a_0=0$$ und $$g(x)=0$$.

**Die Randbedingungen:**
1.  **Dirichlet-Randbedingung bei $$x=0$$ (Innenwand):** Die Temperatur wird
    durch die Heizung im Raum konstant gehalten, $$T(0) = T_w$$

2.  **Robin-Randbedingung bei $$x=L$$ (Fenster/Außenfläche):** Nach dem
    **Newtonschen Abkühlungsgesetz** muss der Wärmestrom, der die Wand verlässt,
    gleich dem an die Außenluft abgegebenen Wärmestrom durch Konvektion sein.

$$-\kappa\frac{dT}{dx}\bigg|_{x=L} = K(T(L) - T_a)$$

$$\kappa T'(L) + K T(L) = K T_a$$,

wobei $$K$$ der *Wärmeübergangskoeffizient* ist und
$$T_a=0^\circ$$C$$=273.15K$$ die Außentmeperatur.

### 2. Aufgabe
Wählen Sie die Wärmeleitfähigkeit der Raumluft zu $$\kappa=0.026[W/(mK)]$$, die
Länge des Raumes zu $$L=5m$$ und die Temperatur der Wand zu
$$T_w=20^\circ$$C=293.15K$$.  

Skalieren Sie auf $$L=1[\ell]=1\cdot 5m$$ und $$\kappa=1[P/(L\cdot T_w]=0.026[W/(mK)]$$ und
$$T_w=1[T]=293,15K$$, wobei $$[\ell]$$ die Längeneinheit, $$[T]$$ die Temperatureinheit
und $$[P]$$ die Leistungseinheit ist. Damit haben wir $$T=\Theta\cdot T_w$$,
$$x=\xi\cdot[\ell]$$. Damit wird die Leistung $$P= 0.026[W/(mK)]\cdot
[\ell]\cdot [T]$$ gmessen in Vielfachen $$1465.75$$W. 

Somit lautet das Randwertproblem

$$\frac{d^2\Theta}{d\xi^2} = 0$$

und mit $$ K/\kappa = h$$

$$\Theta(0) = 1$$ und $$\Theta'(1) + h \Theta(1) = h T_{außen}/T_{Raum}=.932
h$$. Das Fenster sei ein modernes Mehrscheibenfenster mit einem K-Wert von
$$K=1.0W/m^2/K$$. Ersetzen Sie $$h$$ mit Hilfe dieses Vorwissens.

Nehmen Sie an das Fenster habe eine Fläche von $$A=1m^2$$. Wieviel
Wärmeleistung geht durch die konvektive Randbedingung verloren?
