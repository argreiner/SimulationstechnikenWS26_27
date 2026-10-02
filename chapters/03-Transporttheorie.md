---
layout: default
title: Transporththeorie
nav_order: 3
parent: Vorlesung
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
<style>
  .graybox {
    background:#f6f6f6;          /* sehr helles Grau */
    padding:0.9em;
    border-radius:4px;
    margin:1em 0;                /* Abstand zu anderen Elementen */
  }
</style>

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
  Diffusionsprozesses. Die "Pollen" in (a) bewegen sich zufällig in der
  gezeigten Domäne. Nach einer gewissen Zeit (b) ist der anfängliche
  Konzentrationsunterschied zwischen dem linken und rechten Teil der Domäne
  ausgeglichen. 
  </figcaption>
</figure>

### ***Beispiel***: Random walk 

<figure>
  <img src="{{ site.baseurl }}/figs/Brown1D.png" alt="Brownian1D">
  <figcaption align="center">Abbildung 3.2: Zufallsbewegung in einer Dimension
  ist gegeben durch Übergangswahrscheinlichkeiten \(p\) (für eine Bewegung nach
  links) und \(q\) für eine Bewegung nach rechts.  
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

## Teilchen oder Kontinuum

<figure>
  <img src="{{ site.baseurl }}/figs/continuity.png" alt="Kontinuitaet">
  <figcaption align="center">Abbildung 3.3:  Teilchen können das Volumen V nur
  durch die Seitenwände verlassen. Die Änderung der Teilchenzahl N über ein
  Zeitintervall \(\tau\) ist daher durch die Anzahl der Teilchen gegeben, die durch
  die Wände fließen. Hierzu brauchen wir die Teilchenströme \(\mathbf{j}\). Die Anzahl der
  Teilchen, welche durch eine Oberfläche fließen ist dann gegeben durch \(j\cdot A\cdot\tau\) ,
  wobei \(A\) die Fläche der Seitenwand ist. 
</figcaption>
</figure>
 
Die Gleichungen~\eqref{eq:diffusion} und \eqref{eq:driftdiffusion} vermischen
zwei Konzepte, die wir hier jetzt getrennt behandeln wollen: Die Erhaltung der
Anzahl der Teilchen (Kontinuität) und der Prozess, welcher zu einem
Teilchenstrom führt (Diffusion oder Drift). Die Teilchenzahl ist einfach
deshalb erhalten, weil wir keine Atome aus dem Nichts erzeugen oder in das
Nichts vernichten können. Wir wissen also, wenn wir eine gewissen Anzahl
Teilchen $$N_{\text{tot}}$$ in unserem Gesamtsystem haben, dass diese Anzahl

$$
    N_{\text{tot}} = \int \text{d}^3r \, c(\mathbf{r})
$$

sich nicht über die Zeit ändern kann: $$\text{d} N_{\text{tot}}/\text{d} t=0$$.

Für einen kleinen Ausschnitt mit Volumen $$V$$ aus diesem Gesamtvolumen kann sich
die Teilchenzahl ändern, weil diese über die Wände des Probevolumens fließen
können (siehe Abb.~\ref{fig:continuity}). Die Änderung dieser Teilchenzahl ist
zum einen gegeben durch

$$
  \dot{N}
  =
  \frac{\partial}{\partial t} \int_V \text{d}^3r \, c(\mathbf{r}, t)
  =
  \int_V \text{d}^3r \, \frac{\partial c}{\partial t}.
  \label{eq:nchange}
$$

Die Änderung $$\dot{N}$$ muss aber auch durch die Anzahl der Partikel, die über
die Seitenwände abfließen, gegeben sein. Für einen Würfel
(Abb.~\ref{fig:continuity}) mit sechs Wänden gilt

$$
\begin{aligned}
  \dot{N}
  =
  &
  -
  j_{\text{rechts}} A_{\text{rechts}}
  -
  j_{\text{links}} A_{\text{links}}
  \\
  &
  -
  j_{\text{oben}} A_{\text{oben}}
  -
  j_{\text{unten}} A_{\text{unten}}
  \\
  &
  -
  j_{\text{vorne}} A_{\text{vorne}}
  -
  j_{\text{hinten}} A_{\text{hinten}}
\end{aligned}
    \label{eq:dotN}
$$

wenn die Wände klein genug sind, so dass $$j$$ nahezu konstant über $$A$$ ist. (Die
Stromdichte $$j$$ hat die Einheit Anzahl Partikel/Zeit/Fläche.)

Hier bezeichnet der skalare Strom $$j$$ den Strom, der aus der Fläche heraus
fließt. Für eine allgemeine vektorielle Stromdichte $$\mathbf{j}$$, welche die Stärke
und Richtung des Teilchenstroms angibt, ist $$j_i = \mathbf{j}_i \cdot\hat{n}_i$$
wobei $$\hat{n}_i$$ der Normalenvektor auf die Wand $$i$$ ist. Der Strom durch die
Wand ist also nur die Komponente von $$\mathbf{j}$$, die parallel zur
Oberflächennormale steht. Mit diesem Argument können wir die Änderung der
Teilchenzahl allgemein als

$$
  \dot{N} = -\int_{\partial V} \text{d}^2r \, \mathbf{j}(\mathbf{r})\cdot\hat{n}(\mathbf{r})
  \label{eq:flux}
$$

ausdrücken, wobei $$\partial V$$ die Oberfläche des Volumens $$V$$ bezeichnet. In
dieser Gleichung ist explizit angezeigt, dass selbstverständlich sowohl der
Fluss $$\mathbf{j}$$ als auch die Oberflächennormale $$\hat{n}$$ von der Position
$$\mathbf{r}$$ auf der Oberfläche abhängen.

Alternativ können wir auch die Änderung der Teilchenzahl Gl.~\eqref{eq:dotN} folgendermaßen gruppieren:

$$
\begin{aligned}
  \dot{N}
  =
  &
  -
  (j_{\text{rechts}}
  +
  j_{\text{links}}) A_{\text{rechts/links}}
  \\
  &
  -
  (j_{\text{oben}}
  +
  j_{\text{unten}}) A_{\text{oben/unten}}
  \\
  &
  -
  (j_{\text{vorne}}
  +
  j_{\text{hinten}}) A_{\text{vorne/hinten}}
\end{aligned}
$$

Hierbei haben wir die Tatsache genutzt, dass $$A_{\text{rechts}}=A_{\text{links}}\equiv A_{\text{rechts/links}}$$. Nun ist aber

$$
\begin{aligned}
  j_{\text{rechts}} &= \hat{x} \cdot \mathbf{j}(x+\Delta x/2,y,z) = j_x(x+\Delta x/2,y,z)
  \quad\text{und} \\
  j_{\text{links}} &= -\hat{x} \cdot \mathbf{j}(x-\Delta x/2,y,z) = -j_x(x-\Delta x/2,y,z)
\end{aligned}
$$

da $$\hat{n}=\hat{x}$$ für die rechte Wand aber $$\hat{n}=-\hat{x}$$ für die linke
Wand. Hierbei ist $$\hat{x}$$ der Normalenvektor entlang der $$x$$-Achse des
Koordinatensystems.
Es dreht sich also zwischen der rechten und linken Fläche das Vorzeichen der
Oberflächennormale um. Das gleiche gilt für die Wände oben/unten und
vorne/hinten. Wir können diese Gleichung weiterhin umschreiben als

$$
\begin{aligned}
  \dot{N}
  =
  &
  -
  \frac{j_x(x+\Delta x/2,y,z)
  -
  j_x(x-\Delta x/2,y,z)}{\Delta x} \Delta V
  \\
  &
  -
  \frac{j_y(x,y+\Delta y/2,z)
  -
  j_y(x,y-\Delta y/2,z)}{\Delta y} \Delta V
  \\
  &
  -
  \frac{j_z(x,y,z+\Delta z/2)
  -
  j_z(x,y,z-\Delta z/2)}{\Delta z} \Delta V,
\end{aligned}
\label{eq:dotNdiscr}
$$

da $$\Delta V = \Delta x \Delta y \Delta z$$, ist ebenfalls $$\Delta
V=A_{\text{rechts/links}}\Delta x=A_{\text{oben/unten}}\Delta
y=A_{\text{vorne/hinten}}\Delta z$$.  Wir entwickeln die rechte Seite von
\eqref{eq:dotNdiscr} nach Taylor bis zu Gliedern erster Ordnung in den
$$\Delta x$$, $$\Delta y$$ und $$\Delta z$$  und erhalten

$$
  \dot{N} = (-\nabla\cdot\mathbf{j}(\mathbf{r}) + R)\Delta V,
$$

wobei das Restglied $$R$$ mit quadratischen Termen in den  $$\Delta x$$,
$$\Delta y$$ und $$\Delta z$$ startet.

Durch Aneinanderreihung vieler kleiner Volumina $$\Delta V_i$$ können wir auch
ein makroskopisches Volumenintegral berechnen. An den  aneinander angrenzenden
Flächen der infinitesimal kleinen Würfel im inneren des Volumens, heben sich
die Flüsse im Grenzübergang auf. Auf der Grenzfläche ist der Stromdichtevektor
eindeutig definiert (siehe Abb. \ref{fig:gaussbox}) und da über beide Volumina
integriert wird, gibt es an der Grenzfläche zwei Beiträge mit gleichem Betrag,
aber umgekehrtem Vorzeichen. 


<figure>
  <img src="{{ site.baseurl }}/figs/gaussbox.png" alt="Gaussbox">
  <figcaption align="center">Abbildung 3.4: Zwei aneinandergrenzende
  infinitesimale Würfel. An der gemeinsamen Grenzfläche ist der Fluss in jedem
  Volumenelement dem Betrag nach gleich, hat aber ein umgekehrtes Vorzeichen, da
  die Oberflächennormalenvektoren jeweils in entgegengesetzte Richtung weisen.
  </figcaption>
</figure>

Wenn wir den Grenzübergang für kleine $$\Delta x$$, $$\Delta y$$ und $$\Delta z$$ machen, erhalten wir

$$
  \dot{N} = -\lim_{\Delta V\rightarrow 0\choose n\rightarrow\infty}\sum_i^n \nabla\cdot\mathbf{j}(\mathbf{r_i})\Delta V
  =-\int_{V} \text{d}^3r \, \nabla\cdot\mathbf{j}(\mathbf{r}).
  \label{eq:flux2}
$$

Wir haben hier gerade heuristisch den Gaussschen Satz (engl. "Divergence
Theorem" - siehe auch Gl.~\eqref{eq:divergencetheorem}) hergeleitet, um
Gl.~\eqref{eq:flux} als Volumenintegral auszudrücken. 

<div class="graybox">
Der Gausssche Satz ist ein wichtiges Ergebnis der Vektoranalysis. Er
wandelt ein Integral über ein Volumen \(V\) in ein Integral über die Oberfläche
\(\partial V\) dieses Volumens um. Für ein Vektorfeld \(\mathbf{f}(\mathbf{r})\) gilt:
$$
\int_V \text{d}^3 r\, \nabla\cdot \mathbf{f}(\mathbf{r})
 =
\int_{\partial V} \text{d}^2 r\, \mathbf{f}(\mathbf{r}) \cdot \hat{n}(\mathbf{r})
\label{eq:divergencetheorem}
$$
Hier ist \(\hat{n}(\mathbf{r})\) der Normalenvektor, welcher auf dem Rand
$$\partial V$$ des Volumens \(V\) nach außen zeigt.
 
Setzen wir speziell \(\mathbf{f}(\mathbf{r})=\mathbf{a}\phi(\mathbf{r})\),
wobei \(\mathbf{a}\) ein konstanter Vektor ist, dann erhalten wir
$$
\begin{aligned}
  \int_V \text{d}^3 r\, \nabla\cdot \mathbf{a}\phi(\mathbf{r})&=
  \int_{\partial V} \text{d}^2 r\, \mathbf{a}\phi(\mathbf{r}) \cdot \hat{n}(\mathbf{r})\nonumber\\
  \int_V \text{d}^3 r\, \nabla\phi(\mathbf{r})&=
  \int_{\partial V} \text{d}^2 r\, \phi(\mathbf{r}) \hat{n}(\mathbf{r})
  \label{eq:divergencetheorem2}
\end{aligned}
$$
</div>

Gleichung~\eqref{eq:nchange} und \eqref{eq:flux2} zusammen ergeben

$$
  \int_V \text{d}^3r \, \left\{\frac{\partial c}{\partial t}+\nabla\cdot\mathbf{j}\right\} = 0.
  \label{eq:continuityweak}
$$

Da dies für jedes beliebige Volumen $$V$$ gilt, muss auch

$$
  \frac{\partial c}{\partial t}+\nabla\cdot\mathbf{j} = 0
  \label{eq:continuity}
$$

erfüllt sein. Diese Gleichung trägt den Namen *Kontinuitätsgleichung*. Sie
beschreibt die Erhaltung der Teilchenzahl bzw. der Masse des Systems.

<div class="graybox">
In der hier dargestellten Herleitung haben wir implizit bereits die
*starke* Formulierung und eine *schwache* Formulierung (engl. "weak
formulation" einer Differentialgleichung kennengelernt.
Gleichung~\eqref{eq:continuity} ist die starke Formulierung der
Kontinuitätsgleichung. Diese verlangt, dass die Differentialgleichung für jeden
räumlichen Punkt \(\mathbf{r}\) erfüllt ist. Die entsprechende schwache Formulierung
ist Gl.~\eqref{eq:continuityweak}. Hier wird nur verlangt, dass die Gleichung
in einer Art Mittelwert, hier als Integral über ein Probevolumen \(V\), erfüllt
ist. Innerhalb des Volumens muss die starke Form nicht erfüllt sein, aber das
Integral über diese Abweichungen (die wir später als "Residuum" bezeichnen
werden) muss verschwinden. Die schwache Formulierung ist für endliche
Probevolumina \(V\) damit eine Näherung. In der Methode der finiten Elemente löst
man eine schwache Gleichung für eine gewissen (approximative) Ansatzfunktion
exakt. Die schwache Formulierung wird daher im Verlauf dieser Veranstaltung
wichtig werden. 
</div>

Wir können weiterhin noch verlangen, dass innerhalb unseres Probevolumens
"Teilchen" produziert werden. In der aktuellen Interpretation der Gleichung
wären dies z.B. chemische Reaktionen, die einen Teilchentyp in einen anderen
umwandeln. Eine identische Gleichung gilt für den Wärmetransport. Hier wäre ein
Quellterm die Produktion von Wärme, z.B. durch ein Heizelement. Gegeben ein
Quellenstrom $$Q$$ (mit Einheit Anzahl Partikel/Zeit/Volumen), kann die
Kontinuitätsgleichung auf 

$$
  \frac{\partial c}{\partial t}+\nabla\cdot\mathbf{j} = Q
  \label{eq:continuitywithsource}
$$

erweitert werden. Die Kontinuitätsgleichung mit Quellterm wird auch manchmal
als *Bilanzgleichung* bezeichnet.

<div class="graybox">
    Gleichung~\eqref{eq:continuitywithsource} beschreibt die zeitliche
    Veränderung der Konzentration \(c\). Eine verwandte Frage ist die nach der Lösung
    dieser Gleichung nach sehr langer Zeit - wenn sich ein dynamisches
    Gleichgewicht eingestellt hat. Dieses Gleichgewicht ist dadurch gekennzeichnet,
    dass \(\partial c/\partial t=0\). Die Gleichung
    $$
       \nabla\cdot\mathbf{j} = Q
    $$
    ist die *stationäre* Variante der Kontinuitätsgleichung.
</div>

### Drift

Kommen wir zurück zu Transportprozessen, zunächst zu Drift. Wenn sich alle
Teilchen in unserem Probevolumen in mit der Geschwindigkeit $$\mathbf{v}$$ bewegen,
dann führt das zu einem Teilchenstrom

$$
  \mathbf{j}_{\text{Drift}} = c \mathbf{v}.
  \label{eq:drift}
$$

Eingesetzt in die Kontinuitätsgleichung~\eqref{eq:continuity} ergibt dies den
Drift-Beitrag zur Drift-Diffusions-Gleichung~\eqref{eq:driftdiffusion}.

### Diffusion

Aus unserem obigen Gedankenexperiment wird klar, dass der Diffusionstrom immer
in Richtung der niedrigen Konzentration, also in entgegengesetzte Richtung des
Gradienten $$\nabla c$$ der Konzentration, gehen muss. Der entsprechende Strom
ist gegeben durch

$$
 \mathbf{j}_{\text{Diffusion}} = - D \nabla c.
 \label{eq:stationary}
$$

Eingesetzt in die Kontinuitätsgleichung~\eqref{eq:continuity} ergibt dies die
Diffusionsgleichung~\eqref{eq:diffusion}.

Die gesamte Drift-Diffusionsgleichung hat daher die Form

$$
 \frac{\partial c}{\partial t} 
 + \nabla\cdot\left(-D\nabla c + c\mathbf{v}\right)=0.
 \label{eq:drift-diffusion-full}
$$

Im Gegensatz zu Gleichungen~\eqref{eq:diffusion} und \eqref{eq:driftdiffusion}
gilt diese Gleichung auch wenn die Diffusionskonstante $$D$$ oder
Drift-Geschwindigkeit $$\mathbf{v}$$ räumlich variiert.

<div class="graybox">
Wir haben hier die Transporttheorie im Sinne einer Teilchenkonzentration \(c\)
eingeführt. Die Kontinuitätsgleichung beschreibt jedoch allgemein die
*Erhaltung* einer bestimmten Größe, in unserem Fall der Teilchenzahl (oder
äquivalent der Masse). Andere physikalisch erhaltene Größen sind der Impuls und
die Energie. Die Kontinuitätsgleichung für den Impuls führt zur Navier-Stokes
Gleichung. Die Kontinuitätsgleichung für die Energie führt zur
Wärmeleitungsgleichung. Für das Beispiel dieser Veranstaltung ist nur die
Erhaltung der Masse relevant. 
</div>
