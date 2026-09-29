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

$$L[y]=a_n(x)y^n(x)+a_{n-1}y^{n-1}(x)+\dots +a_1(x)y'(x)+a_0(x)y(x)=g(x),$$

wobei die $$a_n(x), a_{n-1}, \dots, a_1(x), a_0(x), g(x)$$ reelle, stetige
Funktionen seien, die auf einem Intervall $$x \in [a,b]$$ erklärt sind.
Desweiteren sei $$a_n(x) \neq 0 \quad \forall x \in [a,b]$$.

Wir definierten bereits ein Anfangswertproblem für eine
Gleichung wie $$L[y]=g(x)$$ durch: 

$$L[y]=g(x); \quad y(a)=b_0, \quad y'(a)=b_1,
\dots, y^{n-1}(a)=b_{n-1}$$, mit $$b_i \in \mathbb{R}$$.

Dieses Anfangswertproblem hat eine eindeutige Lösung.

### Lineares Randwertproblem

Bei linearen Randwertproblemen treten anstelle der Anfangsbedingungen die
linearen Randbedingungen:

$$ \begin{aligned}
U_1[y]&=\alpha_{10}y(a)+\alpha_{11}y'(a)+\dots+\alpha_{1n-1}y^{n-1}(a)
       +\beta_{10}y(b)+\beta_{11}y'(b)+\dots+\beta_{1n-1}y^{n-1}(b)=\gamma_1\\
U_2[y]&=\alpha_{20}y(a)+\alpha_{21}y'(a)+\dots+\alpha_{2n-1}y^{n-1}(a)
       +\beta_{20}y(b)+\beta_{21}y'(b)+\dots+\beta_{2n-1}y^{n-1}(b)=\gamma_2\\
&\dots\\
U_n[y]&=\alpha_{n0}y(a)+\alpha_{n1}y'(a)+\dots+\alpha_{nn-1}y^{n-1}(a)
       +\beta_{n0}y(b)+\beta_{n1}y'(b)+\dots+\beta_{nn-1}y^{n-1}(b)=\gamma_n
\end{aligned} $$

Wobei die Frage nach der Lösbarkeit komplexer ist.

**Beispiel:** Randwertproblem 2. Ordnung

Es sei $$L[y]=y''(x)+y(x)=x$$, mit der allgemeinen Lösung 
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
  mit der Transformation $$\tilde{y}(x)=y(x)-y_0(x)$$ in das äquivalente Problem überführt werden:
  $$L[\tilde{y}]=0, \quad U_1[\tilde{y}]=\gamma_1-U_1[y_0], \dots, U_n[\tilde{y}]=\gamma_n-U_n[y_0]$$ (homogene DGL).
- Ist $$u(x)$$ eine Funktion, die nur die Randbedingungen erfüllt
  ($$U_i[u]=\gamma_i$$), dann kann durch $$\tilde{y}(x)=y(x)-u(x)$$ überführt
  werden in:
  $$L[\tilde{y}]=g(x)-L[u], \quad U_1[\tilde{y}]=0, \dots, U_n[\tilde{y}]=0$$ (homogene Randbedingungen).

**Beispiele zur Homogenisierung:**
- $$\tilde{y}=y-\sin(x)\rightarrow\tilde{y}''(x)+\tilde{y}(x)=x$$; $$\tilde{y}(0)=\tilde{y}(\frac{\pi}{2})=0$$
- $$\tilde{y}=y-\pi\sin(\frac{x}{2})$$\rightarrow
  \tilde{y}''(x)+\tilde{y}(x)=x-\frac{3\pi}{4}\sin(\frac{x}{2})$$;
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
$$L[y]=a_2(x)y''(x)+a_1(x)y'(x)+a_0(x)y(x)=g(x)$$.  
Bei Sturmschen Randbedingungen tritt in jeder Bedingung nur eine Grenze auf:
$$U_1[y]=\alpha_{10}y(a)+\alpha_{11}y'(a)=0, \quad
U_2[y]=\beta_{20}y(b)+\beta_{21}y'(b)=0$$ 
Die Lösung wird über die Greensche Funktion 
$$G(x, \xi)$$ dargestellt: $$y(x)=\int_a^b G(x,\xi)g(\xi)d\xi$$ Dabei
werden $$y_1(x)$$ und $$y_2(x)$$ gesucht, die jeweils nur $$U_1$$ bzw. $$U_2$$
erfüllen. Die Greensche Funktion ergibt sich zu: 
$$G(x,\xi)=\begin{cases}
\frac{y_2(x)y_1(\xi)}{W(\xi)a_2(\xi)} & \text{für } a \le \xi \le x \le b \\
\frac{y_1(x)y_2(\xi)}{W(\xi)a_2(\xi)} & \text{für } a \le x \le \xi \le b
\end{cases}$$ 
mit der Wronski-Determinante
$$W(x)=y_1(x)y'_2(x)-y'_1(x)y_2(x)$$,
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
$$

für eine (unbekannte) Funktion $$u(x,t)$$ und der Anfangsbedingung
$$u(x,t=0)=u_0(x)$$ können systematisch auf ein System gekoppelter GDGLs erster
Ordnung zurückgeführt werden. Diese wichtige Eigenschaft wollen wir
untersuchen.

*N.B.:*

In der PDGL erster Ordnung wurde zur Illustration eine Darstellung mit zwei
Variablen $$x$$ und $$t$$ gewählt. Allgemein können wir schreiben:

$$
\sum\limits_i P_i(\{x_i\};u)\frac{\partial u(\{x_i\})}{\partial x_i}=
R(\{x_i\};u)
$$

Hier wurde als Notation $$u(\{x_i\})=u(x_0, x_1, x_2, \ldots)$$ genutzt, also die
geschweiften Klammern bezeichnen alle Variablen $$x_i$$.

Die partielle Differentialgleichung erster Ordnung können wir auf ein System
von GDGLs transformieren. Dies wird die Methode der Charakteristiken genannt.
Wir können dann die Formalismen (analytisch oder numerisch) zur Lösung von
Systemen von GDGLs anwenden, die wir in der Vorlesung
``Differentialgleichungen'' kennengelernt haben.

Wir gehen folgendermaßen vor:
1. Zunächst parametrisieren wir die unabhängigen Veränderlichen mit einem Parameter $$s$$ gemäß $$x(s)$$ und $$t(s)$$.
1. Wir bilden dann die *totale Ableitung* von $$u(x(s),t(s))$$ nach $$s$$
   
   $$
     \frac{\text{d} u(x(s),t(s))}{\text{d} s}=
     \frac{\partial u(x(s),t(s))}{\partial x}\frac{\text{d} x(s)}{\text{d} s}+
     \frac{\partial u(x(s),t(s))}{\partial t}\frac{\text{d} t(s)}{\text{d} s}.
   $$
1. Durch den Vergleich der Koeffizienten der totalen
   Ableitung mit der PDGL sieht man,
   dass diese DGL genau dann gelöst wird, wenn

   $$ \begin{aligned}
        \frac{dx(s)}{ds}&=P(x,t,u),\label{eq:transode1}\\
        \frac{dt(s)}{ds}&=Q(x,t,u)\quad\text{und}\\
        \frac{du(s)}{ds} &= R(u(s)).\label{eq:transode3}
	\end{aligned}
   $$

   erfüllt ist. Dies beschreibt die Lösung entlang bestimmter Kurven in der
   $$(x,t)$$-Ebene. 

Wir haben damit die PDGL in einen Satz gekoppelter GDGLs erster Ordnung,
umgewandelt.

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
	\frac{\text{d} u(x(s),t(s))}{\text{d} s}=\frac{\partial u}{\partial t}\frac{\text{d} t(s)}{\text{d} s}+\frac{\partial u}{\partial x}\frac{\text{d} x(s)}{\text{d} s}.
   $$
1. Die totale Ableitung ist genau dann identisch zu der partiellen
   Differentialgleichung, die wir lösen wollen, wenn

   $$\begin{aligned}
	\frac{\text{d} x(s)}{\text{d} s} &=c\quad\text{und} \\
	\frac{\text{d} t(s)}{\text{d} s} &=1.
   $$\end{aligned}

   In diesem Fall gilt

	   $$ \frac{\text{d} u(s)}{\text{d} s} = 0$$
1. Die allgemeinen Lösungen für die drei gewöhnlichen
   Differentialgleichungen sind gegeben durch

   $$\begin{aligned}
       x(s) &= cs + \text{const.},\\
       t(s) &= s + \text{const.}\quad\text{und}\\
       u(s) &= \text{const.}
   $$\end{aligned}
1. Mit den Anfangsbedingungen $$t(0)=0$$, $$x(0)=\xi $$ und $$u(x,t=0)=f(\xi)$$
   erhält man $$t=s$$, $$x=ct+\xi $$ und $$u=f(\xi)=f(x-ct)$$,

Die Anfangsbedingung $$f(\xi)$$ wird mit der Geschwindigkeit $$c$$ in die positive
x-Richtung transportiert. Die Lösung für $$u$$ bleibt konstant, da die Ableitung
von $$u$$ Null ist, also behält  $u$ den durch die Anfangsbedingung gegebenen
Wert. Das Feld $$u(x,0)$$ wird also mit einer konstanten Geschwindigkeit $$c$$
verschoben: $$u(x,t)=u(x-ct,0)$$.
