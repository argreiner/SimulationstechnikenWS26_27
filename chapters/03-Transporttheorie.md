---
layout: default
title: Transporththeorie
nav_order: 3
parent: Vorlesung
---
# Transporttheorie

Diffusiver Transport ist einfach zugänglich über das Bild des "Random Walk",
einer zufälligen stochastischen Bewegung von Teilchen. Solche zufälligen
Bewegungsprozesse wurden zuerst von dem Botaniker *Robert Brown*
(1773-1858) beschrieben und tragen den Namen *Brownsche Bewegung* oder
*Brownsche Molekularbewegung*. Robert Brown wusste damals allerdings nicht
von Molekülen und dachte zu seinen Lebzeiten, dass diese Bewegung auf aktive
Prozesse (der "Lebenskraft" der Pollen) zurückzuführen sei. Heute wissen wir,
dass diese Bewegung durch thermische Fluktuationen verursacht wird, also
Moleküle die zufällig auf die Pollen treffen und diese in eine Richtung stoßen.
Diese Erklärung benötigt die Existenz von Atomen und wurde erst 1905 von Albert
Einstein hoffähig gemacht (siehe hierzu A. Einstein, Über die von der
molekularkinetischen Theorie der Wärme geforderte Bewegung von in ruhenden
Flüssigkeiten suspendierten Teilchen. Ann. Phys., 17:549, 1905).

Brownsche Molekularbewegung führt zu diffusivem Transport.
Abbildung~\ref{fig:brownian} zeigt ein einfaches qualitatives
Gedankenexperiment. Die Konfiguration in Abb.~\ref{fig:brownian}a zeigt eine
Lokalisierung der ``Pollen'' in der linken Hälfte der gezeigten Domäne. Durch
deren zufällige Bewegung (als Beispiel gezeigt an der roten Linie in
Abb.~\ref{fig:brownian}a) werden einige der Pollen die gestrichelte Grenzlinie
in die rechte Hälfte überschreiten und auch wieder zurück kommen. Nach einer
gewissen Zeit lässt sich der Anfangszustand nicht mehr identifizieren und die
Pollen verteilen sich in der gesamten Domäne (Abb.~\ref{fig:brownian}b). Die
Konzentration ist nun konstant. Die Pollen bewegen sich zwar weiter, aber in
Mittel bewegt sich die gleiche Zahl Pollen nach links wie nach rechts. Im Fall
der in Abb.~\ref{fig:brownian}a gezeigt ist, ist diese Symmetrie gebrochen.

<figure>
  <img src="{{ site.baseurl }}/figs/Brownian_Motion.png" alt="BrownianMotion">
  <figcaption align="center">Abbildung 3.1: Illustration eines
  Diffusionsprozesses. Die ``Pollen'' in (a) bewegen sich zufällig in der
  gezeigten Domäne. Nach einer gewissen Zeit (b) ist der anfängliche
  Konzentrationsunterschied zwischen dem linken und rechten Teil der Domäne
  ausgeglichen. 
  </figcaption>
</figure>

### ***Beispiel***: Random walk 

<figure>
  <img src="{{ site.baseurl }}/figs/Brown1D.png" alt="Brownian1D">
  <figcaption align="center">Abbildung 3.2: Zufallsbewegung in einer Dimension
  ist gegeben durch Übergangswahrscheinlichkeiten $$p$$ (für eine Bewegung nach
  links) und $$q$$ für eine Bewegung nach rechts.  
  </figcaption>
</figure>

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
\frac{\partial P(x,t)}{\partial t}=D\frac{\partial^2 P(x,t)}{\partial x^2},
$$ 

die wohlbekannte Diffusionsgleichung resultiert.

## Teilchenbetrachtung oder Kontinuum
<figure>
  <img src="{{ site.baseurl }}/figs/continuity.png" alt="Kontinuitaet">
  <figcaption align="center">Abbildung 3.3:  Teilchen können das Volumen V nur
durch die Seitenwände verlassen. Die Änderung der Teilchenzahl N über ein
Zeitintervall $$\tau$$ ist daher durch die Anzahl der Teilchen gegeben, die durch
die Wände fließen. Hierzu brauchen wir die Teilchenströme j. Die Anzahl der
Teilchen, welche durch eine Oberfläche fließen ist dann gegeben durch j Aτ ,
wobei A die Fläche der Seitenwand ist. </figcaption>
</figure>
 

