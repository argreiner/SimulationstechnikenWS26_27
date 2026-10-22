---
layout: default
title: "Übung 3: Random Walk und die Diffusionsgleichung"
nav_order: 23
parent: Übungen
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Random walk

## Mathematische Fomulierung

Wir nehmen an $$p\ne q$$. In Fall haben wir $$P(x,t+\tau)=pP(x+h,t)+qP(x-h,t)$$
und somit folgt

'''latex
\[ \frac{P(x,t+\tau)-P(x,t)}{\tau}=\frac{h^2}{\tau}\frac{pP(x+h,t)-P(x,t)+qP(x-h,t)}{h^2}\]
'''
Wir schreiben

$$ p=\frac{1}{2}+\varepsilon\quad\mbox{ und }\quad q=\frac{1}{2}-\varepsilon
	\mbox{ ; mit }0\le|\varepsilon|\le\frac{1}{2}$$

In den Grenzfällen $$\tau\rightarrow 0$$ und $$h\rightarrow 0$$ fordern wir 

$$
\lim_{h\rightarrow 0\atop \tau\rightarrow 0}\frac{h^2}{2\tau}=D \mbox{ and
}\lim_{h\rightarrow 0\atop \tau\rightarrow 0}\frac{h(p-q)}{\tau}=v
$$ 

## Aufgaben
1. Welche partielle Differentialgleichung erhalten wir nach dem Grenzübergang?
1. Für $$p=q$$ erhalten wir die Diffusionsgleichung, wie bereits in Aufgabe 1.
   Nehmen Sie dieselben Parameterwerte, dieselbe Anfangsbedingung und dieselbe
   Diskretisierung, wie in 1.  Nehmen Sie als Randbedingung $$P(0,t)=P(1,t)=0$$
   und diskretisieren Sie den räumlichen Anteil mit einer Finiten Differenzen
   Methode. Sie erhalten ein System gekoppelter gewöhnlicher
   Differentialgleichungen 1. Ordnung. Lösen Sie dieses und stellen Sie die Lösung
   graphish dar.
