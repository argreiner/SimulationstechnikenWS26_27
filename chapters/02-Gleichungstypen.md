---
layout: default
title: Partielle Differentialgleichungen
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

# Partielle Differentialgleichungen
In diesem Kapitel knüpfen wir an die Veranstaltung Differentialgleichungen an
und gehen über zu Anfangs- und Randwertproblemen partieller
Differentialgleichungen. Partielle Differentialgleichungen (PDGLs) sind
Differentialgleichungen mit mehr als einer unabhängigen Variablen.  

### Lernziele dieses Kapitels:
- [ ] Typen partieller Differentialgleichungen
- [ ] Analytische Lösung partieller Differentialgleichungen


**Beispiel:** Zeitabhängiges Wärmetransportproblem in einer Raumdimension  

Dieses modellieren wir mit einer Diffusionsgleichung für die lokale Temperatur
des Systems. Die Temperatur wird daher als Funktion zweier unabhängiger
Variablen, der Zeit $$t$$ und der räumlichen Position $$x$$, dargestellt:
$$T(x, t)$$. Die Zeitentwicklung der Temperatur ist gegeben durch
$$
\frac{\partial T(x,t)}{\partial t}=\kappa\frac{\partial^2 T(x,t)}{\partial x^2},
\label{eq:heateq}
$$
wobei $$\kappa$$ den Wärmeleitungskoeffizienten bezeichnet. Diese Gleichung wurde
von Joseph Fourier (*1768, $$\dagger$$1830) entwickelt, der wir im Laufe dieser
Veranstaltung wieder begegnen werden.

Die unabhängigen Veränderlichen sind $$x$$ und $$t$$. 
Mit der Definition eines Wärmestroms $$j(x,t)=-\kappa \frac{\partial T}{\partial
x}$$ erhalten wir eine Kontinuitätsgleichung $$\frac{\partial T}{\partial t} +
\frac{\partial j}{\partial x} = 0 \Rightarrow \frac{\partial T}{\partial
t} = \kappa \frac{\partial^2 T}{\partial x^2}$$.

Um diese Gleichung lösen zu können benötigen wir Anfangsbedingungen
$$T(0,x)=T_0(x)$$, die $$T$$ zu einem Startzeitpunkt auf dem ganzen
Simulationsgebiet $$\Omega$$ festlegen und Randbedingungen $$T_a$$ die $$T$$
auf dem Rand $$\Gamma(\Omega)$$ festlegen und in unserem Beispiel in einer
Raumdimension bei $$x=\{0,L\}$$.

Die allgemeine Form der Randbedingungen (Robin-Randbedingung) lautet:
$$\kappa \frac{\partial T}{\partial x} + \sigma(T - T_a) = 0$$
$$\sigma$$ bezeichne den Wärmeübergangskoeffizienten nach außen.

**Grenzfälle:**
- $$\sigma=0$$: System vollständig isoliert $$\Rightarrow \frac{\partial \theta}{\partial x} = 0$$ (**Neumann-Randbedingung**).
- $$\sigma \gg \kappa$$: Temperatur am Rand ist fix $$\Rightarrow \theta = \theta_a$$ (**Dirichlet-Randbedingung**).

## Partielle Differentialgleichungen erster Ordnung
Quasilineare PDGLs erster Ordnung, also Gleichungen der Form

$$
   P(x,t;u)\frac{\partial u(x,t)}{\partial x}+
Q(x,t;u)\frac{\partial u(x,t)}{\partial t}=
R(x,t;u), \label{eq:PDE1Oquasi}
\tag{2.13}
$$

für eine (unbekannte) Funktion $$u(x,t)$$ und der Anfangsbedingung
$$u(x,t=0)=u_0(x)$$ können systematisch auf ein System gekoppelter GDGLs erster
Ordnung zurückgeführt werden. Diese wichtige Eigenschaft wollen wir
untersuchen.

*N.B.:*

In (2.13) wurde zur Illustration eine Darstellung mit zwei
Variablen $$x$$ und $$t$$ gewählt. Allgemein können wir schreiben:

$$
\sum\limits_i P_i(\{x_i\};u)\frac{\partial u(\{x_i\})}{\partial x_i}=
R(\{x_i\};u)
$$

Hier wurde als Notation $$u(\{x_i\})=u(x_0, x_1, x_2, \ldots)$$ genutzt, also die
geschweiften Klammern bezeichnen alle Variablen $$x_i$$.

(2.13) können wir auf ein System von GDGLs transformieren. Dies wird die
Methode der Charakteristiken genannt.  Wir können dann die Formalismen
(analytisch oder numerisch) zur Lösung von Systemen von GDGLs anwenden, die wir
in der Vorlesung *Differentialgleichungen* kennengelernt haben.

Wir gehen folgendermaßen vor:
1. Zunächst parametrisieren wir die unabhängigen Veränderlichen in (2.13) mit
einem Parameter $$s$$ gemäß $$x(s)$$ und $$t(s)$$.
1. Wir bilden dann die *totale Ableitung* von $$u(x(s),t(s))$$ nach $$s$$
   
   $$
     \frac{\text{d} u(x(s),t(s))}{\text{d} s}=
     \frac{\partial u(x(s),t(s))}{\partial x}\frac{\text{d} x(s)}{\text{d} s}+
     \frac{\partial u(x(s),t(s))}{\partial t}\frac{\text{d} t(s)}{\text{d} s}.
     \tag{2.15}
   $$
1. Durch den Vergleich der Koeffizienten der totalen
   Ableitung (2.15) mit der PDGL (2.13) sieht man,
   dass diese DGL genau dann gelöst wird, wenn

   $$ \begin{aligned}
        \frac{dx(s)}{ds}&=P(x,t,u),\label{eq:transode1} (2.16)\\
        \frac{dt(s)}{ds}&=Q(x,t,u)\quad\text{und} (2.17)\\
        \frac{du(s)}{ds} &= R(u(s)) (2.18)
	\end{aligned}
   $$

   erfüllt ist. Dies beschreibt die Lösung entlang bestimmter Kurven in der
   $$(x,t)$$-Ebene. 

Wir haben damit die PDGL in einen Satz gekoppelter GDGLs erster Ordnung
(2.16-18) umgewandelt.

*Beispiel:* Die Transportgleichung

$$
\frac{\partial u(x,t)}{\partial t}+c\frac{\partial u(x,t)}{\partial x}=0
$$

mit der Anfangsbedingung $$u(x,t=0)=u_0(x)$$ soll gelöst werden. Wir gehen nach
obigem Rezept vor:

1. Wir parameterisieren die Variablen $$x$$ und $$t$$ mit Hilfe einer neuen
   Variable $$s$$, also $$x(s)$$ und $$t(s)$$. Wir suchen nun nach einem Ausdruck, mit
   dem wir $$x(s)$$ und $$t(s)$$ bestimmen können.
1. Wir stellen nun die Frage, wie sich die Funktion $$u(x(s),t(s))$$ verhält.
   Diese Funktion beschreibt die Änderung eines Anfangswertes $$u(x(0),t(0))$$ mit
   der Variable $$s$$. Die totale Ableitung wird zu 

   $$ 
	\frac{\text{d} u(x(s),t(s))}{\text{d} s}=\frac{\partial u}{\partial t}\frac{\text{d} t(s)}{\text{d} s}
                                                 +\frac{\partial u}{\partial x}\frac{\text{d} x(s)}{\text{d} s}.
   $$
1. Die totale Ableitung ist genau dann identisch zu der partiellen
   Differentialgleichung, die wir lösen wollen, wenn

   $$
     \begin{aligned}
	\frac{\text{d} x(s)}{\text{d} s} &=c\quad\text{und} \\
	\frac{\text{d} t(s)}{\text{d} s} &=1.
     \end{aligned}
   $$

   In diesem Fall gilt 

   $$\frac{\text{d} u(s)}{\text{d} s} = 0$$

1. Die allgemeinen Lösungen für die drei gewöhnlichen
   Differentialgleichungen sind gegeben durch

   $$
     \begin{aligned}
       x(s) &= cs + \text{const.},\\
       t(s) &= s + \text{const.}\quad\text{und}\\
       u(s) &= \text{const.}
     \end{aligned}
   $$
1. Mit den Anfangsbedingungen $$t(0)=0$$, $$x(0)=\xi $$ und $$u(x,t=0)=f(\xi)$$
   erhält man $$t=s$$, $$x=ct+\xi $$ und $$u=f(\xi)=f(x-ct)$$,

Die Anfangsbedingung $$f(\xi)$$ wird mit der Geschwindigkeit $$c$$ in die positive
x-Richtung transportiert. Die Lösung für $$u$$ bleibt konstant, da die Ableitung
von $$u$$ Null ist, also behält  $u$ den durch die Anfangsbedingung gegebenen
Wert. Das Feld $$u(x,0)$$ wird also mit einer konstanten Geschwindigkeit $$c$$
verschoben: $$u(x,t)=u(x-ct,0)$$.

### Partielle Differentialgleichungen zweiter Ordnung

Beispiele von PDGLs zweiter Ordnung sind die...
- ...Wellengleichung:

$$
	\frac{\partial^2 u}{\partial t^2}-\frac{\partial^2 u}{\partial x^2}=0
$$

- ...Diffusionsgleichung (mit der wir uns hier näher beschäftigen werden):

$$
	\frac{\partial u}{\partial t}-\frac{\partial^2 u}{\partial x^2}=0
$$

- ...Laplacegleichung (die wir auch näher kennen lernen werden):

$$
	\frac{\partial^2 u}{\partial x^2}+\frac{\partial^2 u}{\partial y^2}=0
$$

Die zweite Ordnung bezieht sich hier auf die zweite Ableitung. Diese Beispiel
sind für zwei Variablen formuliert, aber diese Differentialgleichungen können
auch für mehr Freiheitsgrade aufgeschrieben werden.

Für zwei Variablen lautet die allgemeine Form linearer PDGLs zweiter Ordnung,

$$
	a(x,y) \frac{\partial^2 u}{\partial x^2}+
	b(x,y)\frac{\partial^2 u}{\partial x\partial y}+
	c(x,y)\frac{\partial^2 u}{\partial y^2}=
        F\left(x,y;u,\frac{\partial u}{\partial x},\frac{\partial u}{\partial y}\right),
$$

wobei $$F$$ selbst natürlich auch linear in den Argumenten sein muss, wenn die
gesamte Gleichung linear sein soll.  Wir nehmen nun eine Klassifizierung von
PDGLs 2. Ordnung vor, stellen aber vorweg, dass diese Klassifizierung nicht
erschöpfend ist und dass sie nur punktweise gilt. Letzteres heißt, dass die
PDGL an unterschiedlichen Raumpunkten in eine andere Klassifizierung fallen
kann.

Wir nehmen zunächst an, dass $$F=0$$ und $$a$$, $$b$$, $$c$$ konstant seien.
Dann erhalten wir:

$$
	a \frac{\partial^2 u}{\partial x^2}+
	b \frac{\partial^2 u}{\partial x\partial y}+
	c \frac{\partial^2 u}{\partial y^2}=0
  \tag{2.31}
$$

Wir schreiben diese Gleichung um als die quadratische Form

$$
    \begin{pmatrix}
	    \partial/\partial x \\ \partial/\partial y
	    \end{pmatrix}
	    \cdot
	    \begin{pmatrix}
	    a & b/2 \\
	    b/2 & c
	    \end{pmatrix}
        \cdot
	    \begin{pmatrix}
	    \partial/\partial x \\ \partial/\partial y
	\end{pmatrix}
	u
	=
    \nabla
    \cdot
    \mathbf{C}
    \cdot
    \nabla
    u
	=0
  \tag{2.32}
$$

Die Koeffizientenmatrix $$\mathbf{C}$$ können wir nun diagonalisieren. Dies für zu

$$
    \mathbf{C} = \mathbf{U} \cdot \begin{pmatrix} \lambda_1 & 0 \\ 0 &
    \lambda_2 \end{pmatrix}\cdot \mathbf{U}^T,
  \tag{2.33}
$$

wobei $$\mathbf{U}$$ auf Grund der Symmetrie von $$\mathbf{C}$$ unitär ist,
$$\mathbf{U}^T \cdot\mathbf{U}=\mathbb{1}$$. Die geometrische Interpretation
der Operation $$\mathbf{U}$$ ist eine Rotation. Wir führen nun transformierte
Koordinaten $$x^\prime$$ und $$y^\prime$$ ein, so dass

$$
    \nabla
    =
    \mathbf{U}
    \cdot
    \nabla^\prime
$$

mit $$\nabla^\prime\partial/\partial x^\prime, \partial/\partial y^\prime)$$. Mit anderen
Worten, die Transformationsmatrix ist gegeben als

$$
    \mathbf{U} = \begin{pmatrix}
    \partial x^\prime/\partial x & \partial y^\prime/\partial x \\
    \partial x^\prime/\partial y & \partial y^\prime/\partial y
    \end{pmatrix}.
$$

Die Gleichung (2.31) wird zu

$$
    \lambda_1 \frac{\partial^2 u}{\partial x^{\prime2}} 
    + \lambda_2 \frac{\partial^2 u}{\partial y^{\prime2}} = 0.
    \tag{2.36}
$$

Wir haben die Koeffizienten der Differentialgleichung diagonalisiert. Für eine
beliebige zweifach differenzierbare Funktion $$f(z)$$, ist

$$
u(x^\prime, y^\prime) = f\left(\sqrt{\lambda_2} x^\prime + i\sqrt{\lambda_1} y\prime\right)
$$

die Lösung der (2.36).

Wir unterscheiden nun drei Fälle:
- Der Fall $$\det\mathbf{C}=\lambda_1\lambda_2=ac-b^4/4=0$$ mit $$b\ne 0$$ und $$a\ne 0$$
  führt zu einer parabolischen PDGL. Diese PDGL heißt parabolisch, weil die
  quadratische Form (2.32) bzw. (2.33) eine
  Parabel beschreibt. (Dies ist natürlich eine Analogie. Man muss die
  Differentialoperatoren durch Koordinaten ersetzen damit diese funktioniert.)
  Ohne Beschränkung der Allgemeinheit sei $$\lambda_2=0$$. 

  Dann bekommen wir

  $$
    \frac{\partial^2 u}{\partial x^{\prime2}}=0.
  $$

  Dies ist die kanonische Form einer parabolischen PDGL.
- Der Fall $$\det\mathbf{C}=\lambda_1 \lambda_2=ac-b^2/4>0$$ führt zu einer
  elliptischen PDGL. Diese PDGL heißt elliptisch, weil die quadratische Form
  (2.32) bzw. (2.33) für eine konstante rechte Seite eine Ellipse beschreibt.
  (Für $$\lambda_1=\lambda_2$$ ist es ein Kreis.) Wir formen nun die Gleichung
  für den elliptischen Fall auf eine standardisierte Form um und führen die
  skalierten Koordinaten $$x^\prime=\sqrt{\lambda_1} x^{\prime\prime}$$ und
  $$y^\prime=\sqrt{\lambda_2} y^{\prime\prime}$$ ein. Dann wird aus (2.36) die
  kanonische elliptische PDGL

  $$
    \frac{\partial^2 u}{\partial x^{\prime\prime2}}+
    \frac{\partial^2 u}{\partial y^{\prime\prime2}}=0.
    \tag{2.39}
  $$

  Die kanonische elliptische PDGL ist daher die Laplace-Gleichung (2.39) 
  (hier im Zweidimensionalen). Lösungen der
  Laplace-Gleichung heißen *harmonische Funktionen*.
- Der Fall $$\det\mathbf{C}=\lambda_1\lambda_2=ac-b^2/4<0$$ ergibt die so
  genannte hyperbolische PDGL. Diese PDGL heißt hyperbolisch, weil die
  quadratische Form (2.32) bzw. (2.33) für eine konstante rechte Seite eine
  Hyperbel beschreibt.  Ohne Beschränkung der Allgemeinheit fordern wir nun
  $$\lambda_1>0$$ und $$\lambda_2<0$$. Dann können wir wieder skalierte Koordinaten
  $$x^\prime=\sqrt{\lambda_1}x^{\prime\prime}$$ und
  $$y^\prime=\sqrt{-\lambda_2}y^{\prime\prime}$$ einführen, so dass

  $$
  \frac{\partial^2 u}{\partial x^{\prime\prime2}} - 
  \frac{\partial^2 u}{\partial y^{\prime\prime2}}
  =
  \begin{pmatrix}
  \partial u/\partial x^{\prime\prime} \\
  \partial u/\partial y^{\prime\prime}
  \end{pmatrix}
  \cdot
  \begin{pmatrix}
      1 & 0 \\
      0 & -1
  \end{pmatrix}
  \cdot
  \begin{pmatrix}
      \partial u/\partial x^{\prime\prime} \\
      \partial u/\partial y^{\prime\prime}
  \end{pmatrix}
  =
  0.
  \tag{2.40}
  $$

  Wir können nun durch eine weitere Koordinatentransformation, nämlich eine
  Rotation um $$45^\circ$$, die Koeffizientenmatrix in (2.40) auf eine Form
  bringen, in der die Diagonalelemente $$0$$ und die Nebendiagonalelemente $$1$$
  sind. Dies ergibt die Differentialgleichung

$$
  \frac{\partial^2 u}{\partial x^{\prime\prime\prime} 
  \partial y^{\prime\prime\prime}}=0,
$$

  wobei $$x^{\prime\prime\prime}$$ und $$y^{\prime\prime\prime}$$ die
  entsprechend rotierten Koordinaten sind.  Diese Gleichung ist die kanonische
  Form einer hyperbolischen PDGL und äquivalent zu (2.31) in den neuen Variablen
  $$x^{\prime\prime\prime}$$ und $$y^{\prime\prime\prime}$$.

Für höherdimensionale Probleme müssen wir uns die Eigenwerte der
Koeffizientenmatrix $$\mathbf{C}$$ anschauen. Die PDGL heißt *parabolisch*, wenn
es einen Eigenwert gibt der verschwindet, aber alle anderen Eigenwerte entweder
größer oder kleiner als Null sind. Die PDGL heißt *elliptisch*, wenn alle
Eigenwerte entweder größer Null oder kleiner Null sind. Die PDGL heißt
*hyperbolisch*, wenn es genau einen negativen Eigenwert gibt und alle anderen
positiv sind oder es genau einen positiven Eigenwert gibt und alle anderen
negativ sind. Es ist klar, dass für PDGLs mit mehr als zwei Variablen, diese
drei Klassen von PDGLs nicht erschöpfend sind und es Koeffizientenmatrizen
gibt, die aus diesem Klassifizierungschema fallen. Für Probleme mit genau zwei
Variablen führt diese Klassifzierung zu den Bedingungen für die Determinanten
der Koeffizientenmatrix die oben genannt wurden.

Diese drei Typen linearer PDEs 2. Ordnung lassen sich für manche
Problemstellungen auch analytisch lösen. Wir geben im Folgenden ein Beispiel
hierzu.

<div class="graybox">
*Beispiel: Die eindimensionale Wellengleichung*

$$
 \frac{\partial^2 u}{\partial x^2}-\frac{1}{c^2}\frac{\partial^2 u}{\partial t^2}=0
$$

durch Separation der Variablen. Dafür machen wir den Ansatz $$u(x,t)=X(x)T(t)\), was zu

$$
 \frac{1}{X}\frac{\partial^2 X}{\partial x^2}=
           \frac{1}{c^2}\frac{1}{T}\frac{\partial^2 T}{\partial t^2}
 \tag{2.43}
$$

führt. In (2.43) hängt die linke Seite nur von der Variablen \(x\) ab, während
die rechte Seite nur von \(t\) abhängt. Für beliebige \(x\) und \(t\) kann diese
Gleichung nur erfüllt werden, wenn beide Seiten gleich einer Konstanten sind
und wir erhalten somit

$$
 \frac{1}{X}\frac{\partial^2 X}{\partial x^2}=
   -k^2=\frac{1}{c^2}\frac{1}{T}\frac{\partial^2 T}{\partial t^2}\,\mathrm{.}
$$

Dies ergibt die folgenden zwei Gleichungen

$$\frac{\partial^2 X}{\partial x^2}+k^2X=0$$

mit der Lösung \(X(x)=e^{\pm ikx}\) und

$$\frac{\partial^2 T}{\partial t^2}+\omega^2T=0$$

mit der Lösung \(T(t)=e^{\pm i\omega t}\), wobei wir \(\omega^2=c^2k^2\) gesetzt
haben.  Dieses Beispiel braucht zur Ergänzung Anfangsbedingungen, damit wir
eine Lösung finden können.
</div>

Im folgenden Beispiel motivieren wir die Fundamentallösung oder Greensche
Funktion mit Hilfe der Laplace- und Fouriertransformation.

<div class="graybox">
**Beispiel: Fundamentallösung der Diffusionsgleichung**

Wir wenden uns in diesem Beispiel der Untersuchung der eindimensionalen
Diffusionsgleichung zu. Wir wollen die Herleitung ihrer Fundamentallösung
etwas genauer betrachten und uns einige Anwendung anschauen.
Gegeben die Diffusionsgleichung in der Form

$$ 
  \frac{\partial u}{\partial t}-D\frac{\partial^2 u}{\partial x^2}=h(x,t)
  \label{eqndiffusion}
$$

wobei \(D\) die Diffusionskonstante bezeichne und die Inhomogenität \(h(x,t)\)
eine bekannte Funktion sei. Man denke sich diese als raumzeitliche Quelle für
\(u(x,t)\).

Zunächst wollen wir \(h(x,t)=0\) annehmen und die Anfangsbedingungen
\(u(x,0)=f(x)\) festlegen. Nun wenden wir eine Fouriertransformation bezüglich
der Varaiablen \(x\) an, der Raum sei unbegrenzt.  Bezüglich der Zeit \(t\)
wenden wir eine Laplacetransformation an, da wir ein Anfangswertproblem
vorliegen haben. Wir erhalten

$$
  sU(k,s)-F(k)+k^2U(k,s)=0
\label{eqntransfdiff}
$$

In transformierten Variablen erhalten wir die Lösung 

$$ U(k,s)=\frac{F(k)}{s+k^2} $$

Die Funktion \(G(k,s)=(s+k^2)^{-1}\) ist die Antwortfunktion des Systems im
Wellenzahlraum und im Frequenzbereich.
Die inverse Laplacetransformation ergibt

$$ U(k,t)=e^{-k^2t}F(k) $$

Wir nennen \(G(k,t)=e^{-k^2t}\) die Antwortfunktion im Raum der Wellenzahlen und
im Zeitbereich.  Um die Antwortfunktion zu bekommen, haben wir \(F(k)=1\)
gewählt, was äquivalent dazu ist, dass wir \(f(x)=\delta(x)\) setzen. Der
letzte Schritt verlangt eine inverse Fouriertransformation und führt zu

$$
  u(x,t)=\frac{1}{2\pi}\int_{-\infty}^\infty e^{-k^2t}e^{ikx}dk
\label{eqninvfourierdiff}
$$

Quadratische Ergänzung im Exponenten führt zu

$$
	-k^2t+ikx=-\left(k\sqrt{t}-\frac{ix}{2\sqrt{t}}\right)^2-\frac{x^2}{4t}
	\label{eqncomplsquare}
$$

Daher erhalten wir

$$
u(x,t)=\frac{e^{-\frac{x^2}{4t}}}{2\pi}\int_{-\infty}^\infty 
        e^{-\left(k\sqrt{t}+\frac{ix}{2\sqrt{t}}\right)^2}dk
      =\frac{e^{-\frac{x^2}{4t}}}{\sqrt{4\pi t}}
$$

Die Antwortfunktion oder Greensche Funktion oder Fundamentallösung der
Diffusionsgleichung ist daher

$$
	g(x,t)=\frac{1}{\sqrt{4\pi t}}e^{-\frac{x^2}{4t}}
	\label{eqngreendiff}
$$
</div>
