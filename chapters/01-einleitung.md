---
layout: default
title: Einleitung
nav_order: 2
parent: Vorlesung
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

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
  <img src="{{ site.baseurl }}/figs/ExtendedScheme.png" alt="Simulationsschema">
  <figcaption align="center">Abbildung 1.1: Die vertikale Anordnung der Kästen
repräsentiert die Längenskale, welche auf der rechten Seite gezeigt ist. In den
Kästen selbst stehen Simulationsmethode welche auf diesen Skalen Anwendung
finden. In dieser Lehrveranstaltung beschäftigen wir uns mit der
Diskretisierung von Feldern und wählen einen spezifischen Anwendungsfall, der
in die lokale Bilanz hineinfällt.
  </figcaption>
</figure>

Die Abbildung 1.1 zeigt in der vertikalen Anordnung von
\emph{Längenskalen} und deren Zuordnung zu verschiedenen Beschreibungsebenen.
Auf der kürzesten Längenskala ist meist eine quantenmechanische Beschreibung
notwendig. Dies bedeutet, wenn wir die Phänomene in \r{A} auflösen wollen,
befinden wir uns auf der Beschreibungsebene der Quantenmechanik und alle
zugrundeliegenden Modelle sind von quantenmechanischer Natur. D.h. wir haben es
hier im nichtrelativistischen Fall mit der Schrödingergleichung zu tun. Diese
ist in verschiedenen Methoden implementiert, wie z.B. der
\emph{Dichtefunktionaltheorie}, einer Vielteilchenbeschreibung des
quantenmechanischen elektronischen Systems. Bei dieser Art der
Vielteilchenbeschreibung handelt es sich, im Gegensatz zur
\emph{Molekulardynamik} als Methode auf einer grö{ß}eren Längenskala, nicht um
eine Beschreibung von Punktteilchen, sondern um gekoppelte Felder, was den
Aufwand im Vergleich zu einer reinen Punktmechanik wesentlich erhöht. In der
Punktmechanik haben wir es mit drei Orts- und drei Geschwindigkeitsvariablen
für jedes der $$n$$ wechselwirkenden Teilchen zu tun, während wir in einer
quantenmechanischen Vielteilchenbeschreibung es mit einem Feld mit je drei $$n$$
Ortsvariablen zu tun haben, nämlich $$\Psi(\vec{r}_1,\vec{r}_2,\dots,\vec{r}_n;t)$$. 

Auf der Ebene der semiklassischen und klassischen Mechanik, auch als kinetische
Ebene bezeichnet, werden die Modelle entweder durch die Molekulardynamik
beschrieben oder durch die Bewegungsgleichung der
Einteilchen-Wahrscheinlichkeits\-dichte im Phasenraum $$f(\vec{r},\vec{p})$$ - mit
den unabhängigen Variablen Ort $$\vec{r}$$ und Impuls $$\vec{p}$$. Im zweiten Fall
haben wir eine Funktion $$f(\vec{r}(t),\vec{p}(t),t)$$ die von Ort, Impuls und der
Zeit sowohl explizit, als auch implizit über $$\vec{r}(t)$$ und $$\vec{p}(t)$$ abhängt.
Nehmen wir an, wir müssen $$f(\vec{r}(t),\vec{p}(t),t)$$ durch diskrete Stützstellen
interpolieren.  Dies sind bei einer geringen Auflösung von 10 Punkten pro
Variabler schon bereits 10.000.000 Interpolationspunkte. Dies ist vielleicht
handhabbar, die Auflösung ist aber nicht besonders gut. Und daher ist dieses
Unterfangen eher unnütz.  Wir wollen nicht verschweigen, dass es durchaus
Methoden zur numerischen Lösung der beiden oben beschriebenen Probleme gibt,
auf diese werden aber in dieser Veranstaltung nicht näher eingegangen.

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
