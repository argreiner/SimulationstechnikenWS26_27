---
layout: default
title: Einleitung
nav_order: 1
parent: Home
---

# Einleitung

Die *Simulation* beschäftigt sich mit der numerischen (computergestützten)
Lösung von *Modellen*.  Es gibt unterschiedliche Klassen von Modellen. Modelle
werden mathematisch üblicherweise - aber nicht nur - mit Hilfe von
*Differentialgleichungen* beschrieben. In diesen Fällen ist Simulation die
numerische Lösung von gewöhnlichen oder partiellen Differentialgleichungen.  In
dieser Lehrveranstaltung werden wir vornehmlich die Lösung von partiellen
Differentialgleichungen mit Hilfe der *Methode der finiten Elemente*
besprechen.

### Lernziele dieses Kapitels:
- [ ] Definition von Simulation verstehen.
- [ ] Unterscheidung zwischen deterministischen und stochastischen Modellen.

## Modellbildung
Ein Modell ist eine Nachbildung eines realen oder gedachten Systems.
Wie ordnen zunächst die Modelle nach Längeskale und mathematischer Beschreibung:
<figure>
  <img src="{{ site.baseurl }}/figs/Scheme.png" alt="Simulationsschema">
  <figcaption align="center">Abbildung 1.1: Die vertikale Anordnung der Kisten
repräsentiert die Längenskale, welche auf der rechten Seite gezeigt ist. In
den Kästen selbst stehen Simulationsmethode welche auf diesen Skalen Anwendung
finden. In dieser Lehrveranstaltung beschäftigen wir uns mit der
Diskretisierung von Feldern und wählen einen spezifischen Anwendungsfall, der
in die lokale Bilanz hineinfällt.
  </figcaption>
</figure>
 
### ***Beispiel*** $$p=q=1/2$$

Wir nehmen an, das Teilchen springe zwangsläufig von einem Platz zum
benachbarten in einem diskreten, endlichen und konstanten Zeitschritt $$\Delta
t=\tau$$ und zwar mit der Wahrscheinlichkeit $$q$$ nach rechts und mit $$p$$
nach links. Dann ist die Wahrscheinlichkeit ein Teilchen zur Zeit $$t+\tau$$ am
Ort $$x$$ zu finden, wenn zur Zeit $$t$$ mit einer Wahrscheinlichkeit
$$P(x-h,t)$$ ein Teilchen bei der Position $$x-h$$ zu finden war und mit der
Wahrscheinlichkeit $$P(x+h,t)$$ eines bei $$x+h$$, gegeben durch 

$$
P(x,t+\tau)=p\cdot P(x+h,t)+q\cdot P(x-h,t)
$$ 

Für $$p=q=1/2$$ erhalten wir

$$
P(x,t+\tau)=\frac{1}{2}P(x+h,t)+\frac{1}{2}P(x-h,t)
$$ 

Diese Gleichung hat die folgende äquivalente Form 

$$ 
\frac{P(x,t+\tau)-P(x,t)}{\tau}=
\frac{h^2}{2\tau}\frac{P(x+h,t)-2P(x,t)+P(x-h,t)}{h^2}
$$ 

Für $$\tau\rightarrow 0$$ und gleichzeitig $$h\rightarrow 0$$ unter der
Bedingung, daß

$$
\lim_{h\rightarrow 0\atop \tau\rightarrow 0}\frac{h^2}{2\tau}=D
$$ 

Dies beudeutet, daß nach dem Grenzübergang 

$$ 
\frac{\partial P(x,t)}{\partial t}=D\frac{\partial^2 P(x,t)}{\partial x^2}
$$ 

die wohlbekannte Diffusionsgleichung.
