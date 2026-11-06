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
Diese Auafgabe bearbeiten wir über 2 Wochen hinweg. Ziel ist es die Anwendung der 

a. Finiten Differenzen Methode zu üben,
a. die explizite mit der impliziten Zeitintegration zu vergleichen und
a. verschiedene Randbedingungen anzuwenden.

## Mathematische Fomulierung

Wir nehmen an $$p\ne q$$. In diesem Fall haben wir $$P(x,t+\tau)=pP(x+h,t)+qP(x-h,t)$$
und somit folgt

$$
\frac{P(x,t+\tau)-P(x,t)}{\tau}=\frac{h^2}{\tau}\frac{pP(x+h,t)-P(x,t)+qP(x-h,t)}{h^2}
$$

Wir schreiben

$$
p=\frac{1}{2}+\varepsilon\quad\mbox{ und }\quad q=\frac{1}{2}-\varepsilon
\mbox{ ; mit }0\le|\varepsilon|\le\frac{1}{2}
$$

In den Grenzfällen $\tau\rightarrow 0$ und $h\rightarrow 0$ fordern wir 

$$
\lim_{h\rightarrow 0\atop \tau\rightarrow 0}\frac{h^2}{2\tau}=D \mbox{ and
}\lim_{h\rightarrow 0\atop \tau\rightarrow 0}\frac{h(p-q)}{\tau}=v
$$ 

## Aufgaben
1. Welche partielle Differentialgleichung erhalten wir nach dem Grenzübergang?
1. Für $$p=q$$ erhalten wir die Diffusionsgleichung, wie bereits in Aufgabe 1.
   Nehmen Sie dieselben Parameterwerte, dieselbe Anfangsbedingung und dieselbe
   Diskretisierung, wie in 1. und diskretisieren Sie den räumlichen Anteil mit
   einer Finiten Differenzen Methode. Sie erhalten ein System gekoppelter
   gewöhnlicher Differentialgleichungen 1. Ordnung.
1. Die Zeitableitung soll mit einer einfachen Vorwärtsdifferenz diskretisiert
   werden $$\dot{P}=(P(t+\Delta t)-P(t))/(\Delta t)$$. Der räumliche Anteil 
   wird zum Zeitpunkt $$t$$ ausgewertet: explizite Zeitintegration. Er steht
   also auf der rechten Seite des resultierenden linearen Gleichungssystems.
   Lösen Sie die Diffusionsgleichung mit folgenden Randbedingungen:
 - Dirichlet'sche Randbedingung: $$P(0,t)=P(1,t)=0$$
 - Dirichlet'sche und Neumann'sche Randbedingungen: $$P(0,t)=0$$, $$P'(1,t)=0$$
 - Robin'sche Randbedingungen: $$P(0,t)=0$$, $$P'(1,t)+P(1,t)=P_1$$
1. Dasselbe wie in der vorigen Teilaufgabe nur mit dem Unterschied, dass Sie den
   räumlichen Anteil zum neuen Zeitpunkt auswerten:
1. Stellen Sie die Lösung graphish dar.
1. Diskutieren Sie den Unterschied zur Lösung in der ersten Aufgabe und
   zwischen der impliziten und expliziten Zeitintegration!

## Abgabe bis 23.11.26 um 0000h auf ILIAS

