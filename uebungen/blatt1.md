---
layout: default
title: "Übung 1: Die Diffusionsgleichung als System gewöhnlicher Differentialgleichungen"
nav_order: 21
parent: Übungen
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Die Diffusionsgleichung als System gewöhnlicher Differentialgleichungen

## Mathematische Fomulierung

Gegeben sei die Diffusionsgleichung

$$ \frac{\partial P(x,t)}{\partial\text{t}}=\kappa\frac{\partial^2P(x,t)}{\partial x^2}$$

auf einem räumliche Intervall $$[0,1]$$m und der Anfangsbedingung
$$P(x,0)=1\text{, für }x\in[0.25, 0.75]\text{ und }P(x,0)=0$$ sonst.
Wählen Sie $$\kappa=1\text{m}^2\text{s}^{-1}$$.

## Aufgaben
1. Zerlegen Sie den räumlichen Anteil der Diffusionsgleichung in eine
   Fourierreihe mit *numpy.fft*. Wählen Sie dazu ein Gitter mit 100 Interallen,
   also $$N=101$$ Diskretisierungspunkte und repräsentieren Sie die
   Anfangsbedingung im Raum der einzelnen Wellenzahlen $$k_i$$.
1. Lösen Sie das so erhaltene System von nicht gekoppelten
   Differentialgleichungen 1. Ordnung
1. Stellen Sie den zeitlichen Verlauf von $$P(x,t)$$ graphisch dar.
1. Stellen Sie den Verlauf der Partialwellenamplituden der Fourierreihe
   graphisch dar.
