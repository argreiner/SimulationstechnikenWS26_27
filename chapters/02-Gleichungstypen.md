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
In diesem Kapitel knüpfen wir an die Veranstaltung Differentialgleichungen an.
Dort wurden die gewöhnlichen Differentialgleichungen und Anfangswertprobleme
ausführlich behandelt. Wir gehen nun über zu Randwertproblemen und machen uns
weiterhin Gedanken über partielle Differentialgleichungen.
### Lernziele dieses Kapitels:
- [ ] Numerische Lösung gewöhnlicher Differentialgleichungen
- [ ] Randwertproblem vs Anfangswertproblem
- [ ] Typen partieller Differentialgleichungen


## Lineare Randwertprobleme bei gwöhnlichen Differentialgleichungen
### Anfangswertproblem 

Wir betrachten eine lineare Differentialgleichung $$n$$-ter Ordnung:

$$L[y]=a_n(x)y^n(x)+a_{n-1}y^{n-1}(x)+\dots +a_1(x)y^\prime(x)+a_0(x)y(x)=g(x),$$

wobei die $$a_n(x), a_{n-1}, \dots, a_1(x), a_0(x), g(x)$$ reelle, stetige
Funktionen seien, die auf einem Intervall $$x \in [a,b]$$ erklärt sind.
Desweiteren sei $$a_n(x) \neq 0 \quad \forall x \in [a,b]$$.

Wir definierten bereits ein Anfangswertproblem für eine
Gleichung wie $$L[y]=g(x)$$ durch: 

$$L[y]=g(x); \quad y(a)=b_0, \quad y^\prime(a)=b_1,
\dots, y^{n-1}(a)=b_{n-1}$$, mit $$b_i \in \mathbb{R}$$.

Dieses Anfangswertproblem hat eine eindeutige Lösung.

### Lineares Randwertproblem

Bei linearen Randwertproblemen treten anstelle der Anfangsbedingungen die
linearen Randbedingungen:

$$ \begin{aligned}
U_1[y]&=\alpha_{10}y(a)+\alpha_{11}y^\prime(a)+\dots+\alpha_{1n-1}y^{n-1}(a)
       +\beta_{10}y(b)+\beta_{11}y^\prime(b)+\dots+\beta_{1n-1}y^{n-1}(b)=\gamma_1\\
U_2[y]&=\alpha_{20}y(a)+\alpha_{21}y^\prime(a)+\dots+\alpha_{2n-1}y^{n-1}(a)
       +\beta_{20}y(b)+\beta_{21}y^\prime(b)+\dots+\beta_{2n-1}y^{n-1}(b)=\gamma_2\\
&\dots\\
U_n[y]&=\alpha_{n0}y(a)+\alpha_{n1}y^\prime(a)+\dots+\alpha_{nn-1}y^{n-1}(a)
       +\beta_{n0}y(b)+\beta_{n1}y^\prime(b)+\dots+\beta_{nn-1}y^{n-1}(b)=\gamma_n
\end{aligned} $$

Wobei die Frage nach der Lösbarkeit komplexer ist. Eine spezielle Art von
Randwertproblemen wird durch die Sturm'schen Randbedingungen gegeben. Hierbei
kommt in jeder Randbedingung jeweils nur eine Intervallgrenze vor.

**Beispiel:** Randwertproblem 2. Ordnung

Es sei $$L[y]=y^{\prime\prime}(x)+y(x)=x$$, mit der allgemeinen Lösung 
$$y(x)=c_1\cos(x)+c_2\sin(x)+x$$, wobei $$c_1,c_2 \in \mathbb{R}$$.

Wir betrachten drei unterschiedliche Fälle:
- $$y(0)=0$$ und $$y(\frac{\pi}{2})=1 \Rightarrow c_1=0$$ 
  und $$c_2=\frac{2-\pi}{2}$$. Lösung: $$y(x)=\frac{2-\pi}{2}\sin(x)+x$$.
- $$y(0)=0$$ und $$y(\pi)=\pi \Rightarrow c_1=0$$ 
  und $$c_2$$ ist frei wählbar. Lösung: $$y(x)=c_2\sin(x)+x$$ (einparametrische Schar).
- $$y(0)=0$$ und $$y(\pi)=1 \Rightarrow$$ keine Lösung möglich, 
  da $$c_1=0$$ und $$c_1=\pi-1$$ gleichzeitig erfüllt sein müssten.

### Homogenisierung des Randwertproblems
- Nehmen wir an, $$y_0(x)$$ sei eine spezielle Lösung der inhomogenen
  Differentialgleichung $$L[y]=g(x)$$. Dann kann das Randwertproblem:
  $$L[y]=g(x), \quad U_1[y]=\gamma_1, \dots, U_n[y]=\gamma_n$$
  mit der Transformation $$\tilde{y}(x)=y(x)-y_0(x)$$ in das äquivalente
  Problem überführt werden: $$L[\tilde{y}]=0, \quad
  U_1[\tilde{y}]=\gamma_1-U_1[y_0], \dots, U_n[\tilde{y}]=\gamma_n-U_n[y_0]$$
  (homogene DGL).
- Ist $$u(x)$$ eine Funktion, die nur die Randbedingungen erfüllt
  ($$U_i[u]=\gamma_i$$), dann kann durch $$\tilde{y}(x)=y(x)-u(x)$$ überführt
  werden in:
  $$L[\tilde{y}]=g(x)-L[u], \quad U_1[\tilde{y}]=0, \dots, U_n[\tilde{y}]=0$$ (homogene Randbedingungen).

**Beispiele zur Homogenisierung:**
- $$\tilde{y}=y-\sin(x)\rightarrow\tilde{y}^{\prime\prime}(x)+\tilde{y}(x)=x$$; 
  $$\tilde{y}(0)=\tilde{y}(\frac{\pi}{2})=0$$
- $$\tilde{y}=y-\pi\sin(\frac{x}{2})\rightarrow
  \tilde{y}^{\prime\prime}(x)+\tilde{y}(x)=x-\frac{3\pi}{4}\sin(\frac{x}{2})$$;
  $$\tilde{y}(0)=\tilde{y}(\pi)=0$$

### Lösbarkeit von Randwertproblemen
Wir betrachten das homogenisierte Randwertproblem $$L[y]=h(x), \quad U_1[y]=0,
\dots, U_n[y]=0$$.  Für $$L[y]=0$$ bildet $$y_1(x), \dots, y_n(x)$$ das
Fundamentalsystem. Die allgemeine Lösung $$y(x)=\sum c_i y_i(x)$$ muss die
Randbedingungen erfüllen: 

$$ 
\begin{aligned}
c_1U_1[y_1] + \dots + c_nU_1[y_n] &= 0\\
...\\
c_1U_n[y_1] + \dots + c_nU_n[y_n] &= 0
\end{aligned} 
$$

Damit die $$c_i$$ bestimmt werden können, muss die Koeffizientendeterminante
des Systems betrachtet werden. Für $$L[y]=h(x)$$ wird die partikuläre Lösung
$$y_p$$ addiert, wodurch sich die rechte Seite des Gleichungssystems zu
$$-U_i[y_p]$$ ändert.

### Dirichlet'sche Randbedingungen
Gegeben eine lineare DGL 2. Ordnung mit konstanten Koeffizienten:
$$\frac{d^2y(x)}{dx^2}+a\frac{dy(x)}{dx}+by(x)=g(x)$$
Exponentialansatz $$y(x)=e^{\lambda x}$$ führt zur charakteristischen Gleichung
$$\lambda^2+a\lambda+b=0$$. Bei zwei Lösungen $$\lambda_1, \lambda_2$$ ergibt
sich die allgemeine homogene Lösung:

$$y(x)=c_1 e^{\lambda_1 x}+c_2 e^{\lambda_2 x}$$

Für Randbedingungen $$y(0)=\alpha$$ und $$y(L)=\beta$$ ergibt sich das System:

$$
\begin{pmatrix}
y_1(0)&y_2(0)\\ 
y_1(L)&y_2(L)
\end{pmatrix} 
\begin{pmatrix}
c_1\\ 
c_2
\end{pmatrix} = 
\begin{pmatrix}
\alpha \\ \beta
\end{pmatrix}
$$

Falls $$g \neq 0$$, wird die partikuläre Lösung $$y_p(x)$$ überlagert, wobei $$y_p(x)$$ beispielsweise als:
$$y_p(x)=e^{\lambda_2 x}\int_0^x e^{(\lambda_1-\lambda_2)\eta}\int_0^{\eta}e^{-\lambda_1 \xi}g(\xi)d\xi d\eta$$
dargestellt werden kann.

### Sturmsche Randbedingungen bei DGL 2. Ordnung
Wir betrachten 
$$L[y]=a_2(x)y^{\prime\prime}(x)+a_1(x)y^\prime(x)+a_0(x)y(x)=g(x)$$.  
Bei Sturmschen Randbedingungen tritt in jeder Bedingung nur eine Grenze auf:
$$U_1[y]=\alpha_{10}y(a)+\alpha_{11}y^\prime(a)=0, \quad
U_2[y]=\beta_{20}y(b)+\beta_{21}y^\prime(b)=0$$ 
Die Lösung wird über die Greensche Funktion 
$$G(x, \xi)$$ dargestellt: $$y(x)=\int_a^b G(x,\xi)g(\xi)d\xi$$ Dabei
werden $$y_1(x)$$ und $$y_2(x)$$ gesucht, die jeweils nur $$U_1$$ bzw. $$U_2$$
erfüllen. Die Greensche Funktion ergibt sich zu: 
$$G(x,\xi)=\begin{cases}
\frac{y_2(x)y_1(\xi)}{W(\xi)a_2(\xi)} & \text{für } a \le \xi \le x \le b \\
\frac{y_1(x)y_2(\xi)}{W(\xi)a_2(\xi)} & \text{für } a \le x \le \xi \le b
\end{cases}$$ 
mit der Wronski-Determinante
$$W(x)=y_1(x)y^\prime_2(x)-y^\prime_1(x)y_2(x)$$,
die auf jeden Fall verschieden von Null ist, da $$y_1(x)$$ und $$y_2(x)$$ ein
Fundamentalsystem von Lösungen bilden sollen.

## Partielle Differentialgleichungen
Partielle Differentialgleichungen (PDGLs) sind Differentialgleichungen mit mehr
als einer unabhängigen Variablen.  

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

### Partielle Differentialgleichungen erster Ordnung
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
  a\frac{\partial^2 u}{\partial x^2}+b\frac{\partial^2 u}{\partial x\partial y}+
  c\frac{\partial^2 u}{\partial y^2}=0 \tag{2.31)
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

*Beispiel:* Die eindimensionale Wellengleichung

$$
	\frac{\partial^2 u}{\partial x^2}-\frac{1}{c^2}\frac{\partial^2 u}{\partial t^2}=0
$$

durch Separation der Variablen. Dafür machen wir den Ansatz $u(x,t)=X(x)T(t)$, was zu

$$
	\frac{1}{X}\frac{\partial^2 X}{\partial x^2}=
           \frac{1}{c^2}\frac{1}{T}\frac{\partial^2 T}{\partial t^2}
  \tag{2.43}
$$

führt. In (2.43) hängt die linke Seite nur von der Variablen $$x$$ ab, während
die rechte Seite nur von $$t$$ abhängt. Für beliebige $$x$$ und $$t$$ kann diese
Gleichung nur erfüllt werden, wenn beide Seiten gleich einer Konstanten sind
und wir erhalten somit

$$
        \frac{1}{X}\frac{\partial^2 X}{\partial x^2}=
           -k^2=\frac{1}{c^2}\frac{1}{T}\frac{\partial^2 T}{\partial t^2}\,\mathrm{.}
$$

Dies ergibt die folgenden zwei Gleichungen

$$\frac{\partial^2 X}{\partial x^2}+k^2X=0$$

mit der Lösung $$X(x)=e^{\pm ikx}$$ und

$$\frac{\partial^2 T}{\partial t^2}+\omega^2T=0$$

mit der Lösung $$T(t)=e^{\pm i\omega t}$$, wobei wir $$\omega^2=c^2k^2$$ gesetzt
haben.  Dieses Beispiel braucht zur Ergänzung Anfangsbedingungen, damit wir
eine Lösung finden können.
