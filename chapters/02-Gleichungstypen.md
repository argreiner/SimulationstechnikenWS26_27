---
layout: default
title: Gleichungstypen
nav_order: 3
parent: Vorlesung
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Gleichungstypen

Die meisten Phänomene denen wir in den Ingenieurwissenschaften begegnen,
werden sehr gut durch Differentialgleichungen beschrieben. Wir erinnern
uns an die diskreten Netzwerkmodelle aus Elektrotechnik und
Systemtheorie. Sie werden z.B. durch ein System linearer gewöhnlicher
Differentialgleichungen (engl. “ordinary differential equations”) mit
der Zeit als unabängiger Veränderlicher beschrieben. Wir erinnern uns
auch an den Diffusionsprozess, wie z.B. den Wärmetransport in einem
Bauteil auf einem Kühlkörper, das einer Wärmequelle ausgesetzt ist.
Dieses Phänomen wird am Besten mit einer partiellen
Differentialgleichung (engl. “partial differential equation”)
beschrieben. In diesem Kapitel beschäftigen wir uns mit einer abstrakten
Klassifikation von Differentialgleichungen. Der Diffusionsprozess wird
in mehr Detail im nächsten Kapitel wiederholt.

## Gewöhnliche Differentialgleichungen

Wir erinnern uns an die Klassifizierung (Eigenschaften) der
*gewöhnlichen* Differentialgleichungen (GDGLs) und erkennen die
verschiedenen Typen von Differentialgleichungen. Bei all diesen
Differentialgleichungen sind wir immer an einer Lösung für einen
bestimmten Anfangswert (oder Randwert) interessiert, also z.B.
*x*(*t* = 0) = *x*<sub>0</sub> etc. Dieser Anfangswert ist immer Teil
der Definition der Differentialgleichung.

### Linear und nichtlinear

Eine lineare Differentialgleichung ist beispielsweise
$$\begin{equation}
    m\ddot{x}(t)+c\dot{x}(t)+kx=f(t)
    \label{eq:linear}
\end{equation}$$
die den gedämpften und getriebenen harmonischen Oszillator beschreibt,
während
$$\begin{equation}
    \frac{\dif^2x}{\dif t^2}+\mu(x^2-1)\frac{\dif x}{\dif t}+x= 0
    \label{eq:nichtlinear}
\end{equation}$$
eine nichtlineare Bewegungsgleichung für *x* ist. Sie beschreibt den so
genannten Van-der-Pol Oszillator. Die Nichtlinearität ist hier dadurch
zu erkennen, dass *x*<sup>2</sup> die Ableitung $\dif x/\dif t$
multipliziert.

Die Ableitung erster oder höherer Ordnung ist eine lineare Operation, da
$$\begin{equation}
    \frac{\dif^n}{\dif x^n} \lambda f(x) = \lambda \frac{\dif^n}{\dif x^n} f(x)
\end{equation}$$
für eine Konstante *λ* und
$$\begin{equation}
    \frac{\dif^n}{\dif x^n} \left\[f(x) + g(x)\right\] = \frac{\dif^n}{\dif x^n} f(x) + \frac{\dif^n}{\dif x^n} g(x).
\end{equation}$$
Zeitliche Ableitungen werden mit einem Punkt angezeigt,
$$\begin{equation}
    \dot{x}(t)=\frac{\dif}{\dif t} x(t).
\end{equation}$$
Für Funktionen einer Variable wird die Ableitung oft mit einem Strich
angezeigt,
$$\begin{equation}
    f'(x)=\frac{\dif}{\dif x} f(x).
\end{equation}$$
Für Funktionen mehrere Variablen ist das nicht mehr möglich. Hier werden
wir daher immer explizit den Differentialoperator verwenden.

### Ordnung

Die Ordnung einer Differentialgleichung ist gegeben durch die höchste
Ableitung die in der Gleichung auftaucht. So sind
Gl. <a href="#eq:linear" data-reference-type="eqref"
data-reference="eq:linear">[eq:linear]</a> und
Gl. <a href="#eq:nichtlinear" data-reference-type="eqref"
data-reference="eq:nichtlinear">[eq:nichtlinear]</a> Beispiele für
Differentialgleichungen zweiter Ordnung.

### Systeme

Ein System von Differentialgleichungen 1. Ordnung bilden z.B. die
Gleichungen
$$\begin{align}
    \frac{\dif x}{\dif t} =& x(m - n y), \label{eq:sys1} \\
    \frac{\dif y}{\dif t} =& - y(\gamma - \delta x), \label{eq:sys2}
\end{align}$$
die bekannten Räuber-Beute-Gleichungen oder auch
Lotka-Volterra-Gleichungen.
Gleichungen <a href="#eq:sys1" data-reference-type="eqref"
data-reference="eq:sys1">[eq:sys1]</a> und
<a href="#eq:sys2" data-reference-type="eqref"
data-reference="eq:sys2">[eq:sys2]</a> sind weiterhin nichtlinear.

Differentialgleichungen höherer Ordnung können in ein System von
Gleichungen 1. Ordnung umgeschrieben werden. Im Beispiel des gedämpften
harmonische Oszillators,
$$\begin{equation}
    m\ddot{x}(t)+c\dot{x}(t)+kx=f(t),
\end{equation}$$
ersetzen wir *ẋ* = *y* und erhalten dadurch zwei Gleichungen erster
Ordnung anstatt der ursprünglichen Gleichung zweiter Ordnung, nämlich
$$\begin{align}
    \dot{x} =& y \\
    m\dot{y} =& -cy-kx+f(t)
\end{align}$$

## Partielle Differentialgleichungen

Partielle Differentialgleichungen (PDGLs) sind Differentialgleichungen
mit mehr als einer unabhängigen Variablen. Als Beispiel stellen wir uns
ein zeitabhängiges Wärmetransportproblem in einer Dimension vor. Dieses
wird mit einer Diffusionsgleichung für die lokale Temperatur des Systems
dargestellt. Die Temperatur wird daher als Funktion zweier unabhängiger
Variablen, der Zeit *t* und der räumlichen Position *x*, dargestellt:
*T*(*x*, *t*). Die Zeitentwicklung der Temperatur ist gegeben durch
$$\begin{equation}
\frac{\partial T(x,t)}{\partial t}=\kappa\frac{\partial^2 T(x,t)}{\partial x^2},
\label{eq:heateq}
\end{equation}$$
wobei *κ* den Wärmeleitungskoeffizienten bezeichnet. Diese Gleichung
wurde von Joseph Fourier (\*1768, †<!-- -->1830) entwickelt, dem wir im
Laufe dieser Veranstaltung wieder begegnen werden.

In Gl. <a href="#eq:heateq" data-reference-type="eqref"
data-reference="eq:heateq">[eq:heateq]</a> bezeichnet ∂/∂*t* die
*partielle Ableitung*. Dies ist die Ableitung nach einem der Argumente
(hier *t*), also die Variation der Funktion, wenn alle anderen Argumente
konstant gehalten werden. Bei GDGLs tauchen im Gegensatz zu PDGLs nur
Ableitung nach einer Variable (üblicherweise der Zeit *t*) auf, die dann
mit dem Differentialoperator $\dif/\dif t$ bezeichnet werden.

### Erste Ordnung

Quasilineare PDGLs erster Ordnung, also Gleichungen der Form
$$\begin{equation}
   P(x,t;u)\frac{\partial u(x,t)}{\partial x}+
Q(x,t;u)\frac{\partial u(x,t)}{\partial t}=
R(x,t;u), \label{eq:PDE1Oquasi}
\end{equation}$$
für eine (unbekannte) Funktion *u*(*x*, *t*) und der Anfangsbedingung
*u*(*x*, *t* = 0) = *u*<sub>0</sub>(*x*) können systematisch auf ein
System gekoppelter GDGLs erster Ordnung zurückgeführt werden. Diese
wichtige Eigenschaft wollen wir untersuchen.

In Gl. <a href="#eq:PDE1Oquasi" data-reference-type="eqref"
data-reference="eq:PDE1Oquasi">[eq:PDE1Oquasi]</a> wurde zur
Illustration eine Darstellung mit zwei Variablen *x* und *t* gewählt.
Allgemein können wir schreiben:
$$\begin{equation}
\sum\limits_i P_i(\\x_i\\;u)\frac{\partial u(\\x_i\\)}{\partial x_i}=
R(\\x_i\\;u)
\end{equation}$$
Hier wurde als Notation
*u*({*x*<sub>*i*</sub>}) = *u*(*x*<sub>0</sub>, *x*<sub>1</sub>, *x*<sub>2</sub>, …)
genutzt, also die geschweiften Klammern bezeichnen alle Freiheitsgrade
*x*<sub>*i*</sub>.

Gleichung <a href="#eq:PDE1Oquasi" data-reference-type="eqref"
data-reference="eq:PDE1Oquasi">[eq:PDE1Oquasi]</a> können wir auf ein
System von GDGLs transformieren. Dies wird die Methode der
Charakteristiken genannt. Wir können dann die Formalismen (analytisch
oder numerisch) zur Lösung von Systemen von GDGLs anwenden, die wir in
der Vorlesung “Differentialgleichungen” kennengelernt haben.

Wir gehen folgendermaßen vor:

1.  Zunächst parametrisieren wir die unabhängigen Veränderlichen in
    Gl. <a href="#eq:PDE1Oquasi" data-reference-type="eqref"
    data-reference="eq:PDE1Oquasi">[eq:PDE1Oquasi]</a> mit einem
    Parameter *s* gemäß *x*(*s*) und *t*(*s*).

2.  Wir bilden dann die *totale Ableitung* von *u*(*x*(*s*), *t*(*s*))
    nach *s*
    $$\begin{equation}
        \frac{\dif u(x(s),t(s))}{\dif s}=
        \frac{\partial u(x(s),t(s))}{\partial x}\frac{\dif x(s)}{\dif s}+
        \frac{\partial u(x(s),t(s))}{\partial t}\frac{\dif t(s)}{\dif s}.
        \label{eq:totalderiv}
    \end{equation}$$

3.  Durch den Vergleich der Koeffizienten der totalen
    Ableitung <a href="#eq:totalderiv" data-reference-type="eqref"
    data-reference="eq:totalderiv">[eq:totalderiv]</a> mit der
    PDGL <a href="#eq:PDE1Oquasi" data-reference-type="eqref"
    data-reference="eq:PDE1Oquasi">[eq:PDE1Oquasi]</a> sieht man, dass
    diese DGL genau denn gelöst wird, wenn
    $$\begin{align}
            \frac{dx(s)}{ds}&=P(x,t,u),\label{eq:transode1}\\
            \frac{dt(s)}{ds}&=Q(x,t,u)\quad\text{und}\\
            \frac{du(s)}{ds} &= R(u(s)).\label{eq:transode3}
    \end{align}$$
    erfüllt ist. Dies beschreibt die Lösung entlang bestimmter Kurven in
    der (*x*, *t*)-Ebene.

Wir haben damit die PDGL in einen Satz gekoppelter GDGLs erster Ordnung,
Gl. <a href="#eq:transex1" data-reference-type="eqref"
data-reference="eq:transex1">[eq:transex1]</a>-<a href="#eq:transex3" data-reference-type="eqref"
data-reference="eq:transex3">[eq:transex3]</a> umgewandelt.

Die Transportgleichung
$$\begin{equation}
\frac{\partial u(x,t)}{\partial t}+c\frac{\partial u(x,t)}{\partial x}=0
\label{eq:transportexample}
\end{equation}$$
mit der Anfangsbedingung *u*(*x*, *t* = 0) = *u*<sub>0</sub>(*x*) soll
gelöst werden. Wir gehen nach obigem Rezept vor:

1.  Wir parameterisieren die Variablen *x* und *t* mit Hilfe einer neuen
    Variable *s*, also *x*(*s*) und *t*(*s*). Wir suchen nun nach einem
    Ausdruck, mit dem wir *x*(*s*) und *t*(*s*) bestimmen können.

2.  Wir stellen nun die Frage, wie sich die Funktion
    *u*(*x*(*s*), *t*(*s*)) verhält. Diese Funktion beschreibt die
    Änderung eines Anfangswertes *u*(*x*(0), *t*(0)) mit der Variable
    *s*. Die totale Ableitung wird zu
    $$\begin{equation}
        \frac{\dif u(x(s),t(s))}{\dif s}=\frac{\partial u}{\partial t}\frac{\dif t(s)}{\dif s}+\frac{\partial u}{\partial x}\frac{\dif x(s)}{\dif s}.
    \end{equation}$$

3.  Die totale Ableitung ist genau dann identisch zu der partiellen
    Differentialgleichung, die wir lösen wollen, wenn
    $$\begin{align}
        \frac{\dif x(s)}{\dif s} &=c\quad\text{und} \label{eq:transex1}\\
        \frac{\dif t(s)}{\dif s} &=1.
    \end{align}$$
    In diesem Fall gilt
    $$\begin{equation}
            \frac{\dif u(s)}{\dif s} = 0.\label{eq:transex3}
    \end{equation}$$

4.  Die allgemeinen Lösungen für die drei gewöhnlichen
    Differentialgleichungen <a href="#eq:transex1" data-reference-type="eqref"
    data-reference="eq:transex1">[eq:transex1]</a>-<a href="#eq:transex3" data-reference-type="eqref"
    data-reference="eq:transex3">[eq:transex3]</a> sind gegeben durch
    $$\begin{align}
           x(s) &= cs + \text{const.},\\
           t(s) &= s + \text{const.}\quad\text{und}\\
           u(s) &= \text{const.}
    \end{align}$$

5.  Mit den Anfangsbedingungen *t*(0) = 0, *x*(0) = *ξ* und
    *u*(*x*, *t* = 0) = *f*(*ξ*) erhält man *t* = *s*,
    *x* = *c**t* + *ξ* und *u* = *f*(*ξ*) = *f*(*x* − *c**t*),

Die Anfangsbedingung *f*(*ξ*) wird mit der Geschwindigkeit *c* in die
positive x-Richtung transportiert. Die Lösung für *u* bleibt konstant,
da die Ableitung von *u* Null ist, also behält *u* den durch die
Anfangsbedingung gegebenen Wert. Das Feld *u*(*x*, 0) wird also mit
einer konstanten Geschwindigkeit *c* verschoben:
*u*(*x*, *t*) = *u*(*x* − *c**t*, 0).

### Zweite Ordnung

Beispiele von PDGLs zweiter Ordnung sind die...

- ...Wellengleichung:
  $$\begin{equation}
      \frac{\partial^2 u}{\partial t^2}-\frac{\partial^2 u}{\partial x^2}=0
  \end{equation}$$

- ...Diffusionsgleichung (mit der wir uns hier näher beschäftigen
  werden):
  $$\begin{equation}
      \frac{\partial u}{\partial t}-\frac{\partial^2 u}{\partial x^2}=0
  \end{equation}$$

- ...Laplacegleichung (die wir auch näher kennen lernen werden):
  $$\begin{equation}
      \frac{\partial^2 u}{\partial x^2}+\frac{\partial^2 u}{\partial y^2}=0
  \end{equation}$$

Die zweite Ordnung bezieht sich hier auf die zweite Ableitung. Diese
Beispiel sind für zwei Variablen formuliert, aber diese
Differentialgleichungen können auch für mehr Freiheitsgrade
aufgeschrieben werden.

Für zwei Variablen lautet die allgemeine Form linearer PDGLs zweiter
Ordnung,
$$\begin{equation}
    a(x,y) \frac{\partial^2 u}{\partial x^2}+
    b(x,y)\frac{\partial^2 u}{\partial x\partial y}+
    c(x,y)\frac{\partial^2 u}{\partial y^2}=F\left(x,y;u,\frac{\partial u}{\partial x},\frac{\partial u}{\partial y}\right),
\end{equation}$$
wobei *F* selbst natürlich auch linear in den Argumenten sein muss, wenn
die gesamte Gleichung linear sein soll. Wir nehmen nun eine
Klassifizierung von PDGLs 2. Ordnung vor, stellen aber vorweg, dass
diese Klassifizierung nicht erschöpfend ist und dass sie nur punktweise
gilt. Letzteres heißt, dass die PDGL an unterschiedlichen Raumpunkten in
eine andere Klassifizierung fallen kann.

Wir nehmen zunächst an, dass *F* = 0 und *a*, *b*, *c* konstant seien.
Dann erhalten wir:
$$\begin{equation}
        a\frac{\partial^2 u}{\partial x^2}+b\frac{\partial^2 u}{\partial x\partial y}+
        c\frac{\partial^2 u}{\partial y^2}=0.
    \label{eq:n2ndoconst}
\end{equation}$$
Wir schreiben diese Gleichung um als die quadratische Form
$$\begin{equation}
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
    \t{C}
    \cdot
    \nabla
    u
    =0
    \label{eq:quadform}
\end{equation}$$
Die Koeffizientenmatrix $\t{C}$ können wir nun diagonalisieren. Dies für
zu
$$\begin{equation}
    \t{C} = \t{U} \cdot \begin{pmatrix} \lambda_1 & 0 \\ 0 & \lambda_2 \end{pmatrix}\cdot \t{U}^T,
    \label{eq:diagquadform}
\end{equation}$$
wobei $\t{U}$ auf Grund der Symmetrie von $\t{C}$ unitär ist,
$\t{U}^T \cdot\t{U}=\t{1}$. Die geometrische Interpretation der
Operation $\t{U}$ ist eine Rotation. Wir führen nun transformierte
Koordinaten *x*<sup>′</sup> und *y*<sup>′</sup> ein, so dass
$$\begin{equation}
    \nabla
    =
    \t{U}
    \cdot
    \nabla'
\end{equation}$$
mit ∇<sup>′</sup> = (∂/∂*x*<sup>′</sup>, ∂/∂*y*<sup>′</sup>). Mit
anderen Worten, die Transformationsmatrix ist gegeben als
$$\begin{equation}
    \t{U} = \begin{pmatrix}
    \partial x'/\partial x & \partial y'/\partial x \\
    \partial x'/\partial y & \partial y'/\partial y
    \end{pmatrix}.
\end{equation}$$
Gleichung <a href="#eq:n2ndoconst" data-reference-type="eqref"
data-reference="eq:n2ndoconst">[eq:n2ndoconst]</a> wird zu
$$\begin{equation}
    \lambda_1 \frac{\partial^2 u}{\partial x'^2} + \lambda_2 \frac{\partial^2 u}{\partial y'^2} = 0.
    \label{eq:diag2nd}
\end{equation}$$
Wir haben die Koeffizienten der Differentialgleichung diagonalisiert.
Für eine beliebige zweifach differenzierbare Funktion *f*(*z*), ist
$$\begin{equation}
u(x', y') = f\left(\sqrt{\lambda_2} x' + i\sqrt{\lambda_1} y'\right)
\end{equation}$$
eine Lösung von Gl. <a href="#eq:diag2nd" data-reference-type="eqref"
data-reference="eq:diag2nd">[eq:diag2nd]</a>.

Wir unterscheiden nun drei Fälle:

- Der Fall $\det\t{C}=\lambda_1\lambda_2=ac-b^4/4=0$ mit *b* ≠ 0 und
  *a* ≠ 0 führt zu einer parabolischen PDGL. Diese PDGL heißt
  parabolisch, weil die quadratische Form
  Gl. <a href="#eq:quadform" data-reference-type="eqref"
  data-reference="eq:quadform">[eq:quadform]</a> bzw.
  <a href="#eq:diagquadform" data-reference-type="eqref"
  data-reference="eq:diagquadform">[eq:diagquadform]</a> eine Parabel
  beschreibt. (Dies ist natürlich eine Analogie. Man muss die
  Differentialoperatoren durch Koordinaten ersetzen damit diese
  funktioniert.) Ohne Beschränkung der Allgemeinheit sei
  *λ*<sub>2</sub> = 0. Dann bekommen wir
  $$\begin{equation}
          \frac{\partial^2 u}{\partial x'^2}=0.
          \label{eqnparab}
  \end{equation}$$
  Dies ist die kanonische Form einer parabolischen PDGL.

- Der Fall $\det\t{C}=\lambda_1 \lambda_2=ac-b^2/4\>0$ führt zu einer
  elliptischen PDGL. Diese PDGL heißt elliptisch, weil die quadratische
  Form Gl. <a href="#eq:quadform" data-reference-type="eqref"
  data-reference="eq:quadform">[eq:quadform]</a> bzw.
  <a href="#eq:diagquadform" data-reference-type="eqref"
  data-reference="eq:diagquadform">[eq:diagquadform]</a> für eine
  konstante rechte Seite eine Ellipse beschreibt. (Für
  *λ*<sub>1</sub> = *λ*<sub>2</sub> ist es ein Kreis.) Wir formen nun
  die Gleichung für den elliptischen Fall auf eine standardisierte Form
  um und führen die skalierten Koordinaten $x'=\sqrt{\lambda_1} x''$ und
  $y'=\sqrt{\lambda_2} y''$ ein. Dann wird aus
  Gl. <a href="#eq:diag2nd" data-reference-type="eqref"
  data-reference="eq:diag2nd">[eq:diag2nd]</a> die kanonische
  elliptische PDGL
  $$\begin{equation}
          \frac{\partial^2 u}{\partial x''^2}+\frac{\partial^2 u}{\partial y''^2}=0.
          \label{eqnelliptic}
  \end{equation}$$
  Die kanonische elliptische PDGL ist daher die Laplace-Gleichung,
  Gl. <a href="#eqnelliptic" data-reference-type="eqref"
  data-reference="eqnelliptic">[eqnelliptic]</a> (hier im
  Zweidimensionalen). Lösungen der Laplace-Gleichung heißen *harmonische
  Funktionen*.

- Der Fall $\det\t{C}=\lambda_1\lambda_2=ac-b^2/4\<0$ ergibt die so
  genannte hyperbolische PDGL. Diese PDGL heißt hyperbolisch, weil die
  quadratische Form
  Gl. <a href="#eq:quadform" data-reference-type="eqref"
  data-reference="eq:quadform">[eq:quadform]</a> bzw.
  <a href="#eq:diagquadform" data-reference-type="eqref"
  data-reference="eq:diagquadform">[eq:diagquadform]</a> für eine
  konstante rechte Seite eine Hyperbel beschreibt. Ohne Beschränkung der
  Allgemeinheit fordern wir nun *λ*<sub>1</sub> \> 0 und
  *λ*<sub>2</sub> \< 0. Dann können wir wieder skalierte Koordinaten
  $x'=\sqrt{\lambda_1}x''$ und $y'=\sqrt{-\lambda_2}y''$ einführen, so
  dass
  $$\begin{equation}
          \frac{\partial^2 u}{\partial x''^2} - \frac{\partial^2 u}{\partial y''^2}
          =
          \begin{pmatrix}
              \partial u/\partial x'' \\
              \partial u/\partial y''
          \end{pmatrix}
          \cdot
          \begin{pmatrix}
              1 & 0 \\
              0 & -1
          \end{pmatrix}
          \cdot
          \begin{pmatrix}
              \partial u/\partial x'' \\
              \partial u/\partial y''
          \end{pmatrix}
          =
          0.
          \label{eq:hyb}
  \end{equation}$$
  Wir können nun durch eine weitere Koordinatentransformation, nämlich
  eine Rotation um 45<sup>∘</sup>, die Koeffizientenmatrix in
  Gl. <a href="#eq:hyb" data-reference-type="eqref"
  data-reference="eq:hyb">[eq:hyb]</a> auf eine Form bringen, in der die
  Diagonalelemente 0 und die Nebendiagonalelemente 1 sind. Dies ergibt
  die Differentialgleichung
  $$\begin{equation}
          \frac{\partial^2 u}{\partial x''' \partial y'''}=0,
          \label{eqnd2udxideta0}
  \end{equation}$$
  wobei *x*<sup>‴</sup> und *y*<sup>‴</sup> die entsprechend rotierten
  Koordinaten sind. Diese Gleichung ist die kanonische Form einer
  hyperbolischen PDGL und äquivalent zu
  Gl. <a href="#eq:n2ndoconst" data-reference-type="eqref"
  data-reference="eq:n2ndoconst">[eq:n2ndoconst]</a> in den neuen
  Variablen *x*<sup>‴</sup> und *y*<sup>‴</sup>.

Für höherdimensionale Probleme müssen wir uns die Eigenwerte der
Koeffizientenmatrix $\t{C}$ anschauen. Die PDGL heißt *parabolisch*,
wenn es einen Eigenwert gibt der verschwindet, aber alle anderen
Eigenwerte entweder größer oder kleiner als Null sind. Die PDGL heißt
*elliptisch*, wenn alle Eigenwerte entweder größer Null oder kleiner
Null sind. Die PDGL heißt *hyperbolisch*, wenn es genau einen negativen
Eigenwert gibt und alle anderen positiv sind oder es genau einen
positiven Eigenwert gibt und alle anderen negativ sind. Es ist klar,
dass für PDGLs mit mehr als zwei Variablen, diese drei Klassen von PDGLs
nicht erschöpfend sind und es Koeffizientenmatrizen gibt, die aus diesem
Klassifizierungschema fallen. Für Probleme mit genau zwei Variablen
führt diese Klassifzierung zu den Bedingungen für die Determinanten der
Koeffizientenmatrix die oben genannt wurden.

Diese drei Typen linearer PDEs 2. Ordnung lassen sich für manche
Problemstellungen auch analytisch lösen. Wir geben im Folgenden ein
Beispiel hierzu.

Wir lösen die eindimensionale Wellengleichung.
$$\begin{equation}
    \frac{\partial^2 u}{\partial x^2}-\frac{1}{c^2}\frac{\partial^2 u}{\partial t^2}=0
    \label{eqn1Dwaveeqn}
\end{equation}$$
durch Separation der Variablen. Dafür machen wir den Ansatz
*u*(*x*, *t*) = *X*(*x*)*T*(*t*), was zu
$$\begin{equation}
    \frac{1}{X}\frac{\partial^2 X}{\partial x^2}=\frac{1}{c^2}\frac{1}{T}\frac{\partial^2 T}{\partial t^2}
    \label{eqnseparate}
\end{equation}$$
führt. In Gl. <a href="#eqnseparate" data-reference-type="eqref"
data-reference="eqnseparate">[eqnseparate]</a> hängt die linke Seite nur
von der Variablen *x* ab, während die rechte Seite nur von *t* abhängt.
Für beliebige *x* und *t* kann diese Gleichung nur erfüllt werden, wenn
beide Seiten gleich einer Konstanten sind und wir erhalten somit
$$\begin{equation}
        \frac{1}{X}\frac{\partial^2 X}{\partial x^2}=-k^2=\frac{1}{c^2}\frac{1}{T}\frac{\partial^2 T}{\partial t^2}\\\mathrm{.}
\end{equation}$$
Dies ergibt die folgenden zwei Gleichungen
$$\frac{\partial^2 X}{\partial x^2}+k^2X=0$$
mit der Lösung *X*(*x*) = *e*<sup>±*i**k**x*</sup> und
$$\frac{\partial^2 T}{\partial t^2}+\omega^2T=0$$
mit der Lösung *T*(*t*) = *e*<sup>±*i**ω**t*</sup>, wobei wir
*ω*<sup>2</sup> = *c*<sup>2</sup>*k*<sup>2</sup> gesetzt haben. Dieses
Beispiel braucht zur Ergänzung Anfangsbedingungen, damit wir eine Lösung
finden können.
