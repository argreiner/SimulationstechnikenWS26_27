---
layout: default
title: Transporththeorie
nav_order: 3
parent: Vorlesung
---
# Transporttheorie

### ***Beispiel***: Random walk 

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
  <figcaption align="center">Abbildung 1.2:  Teilchen können das Volumen V nur
durch die Seitenwände verlassen. Die Änderung der Teilchenzahl N über ein
Zeitintervall $$\tau$$ ist daher durch die Anzahl der Teilchen gegeben, die durch
die Wände fließen. Hierzu brauchen wir die Teilchenströme j. Die Anzahl der
Teilchen, welche durch eine Oberfläche fließen ist dann gegeben durch j Aτ ,
wobei A die Fläche der Seitenwand ist. </figcaption>
</figure>
 

