---
layout: default
title: Funktionenräume
nav_order: 4
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

# Funktionenräume

## Numerische Lösungsstrategien

Wir legen jetzt das Transportproblem für eine Weile zur Seite und wollen uns
der *numerischen* Lösung von Differentialgleichungen widmen. Dieses
Kapitel zeigt die Grundzüge der numerischen Analyse von Differentialgleichungen
und führt ein paar wichtige Konzepte ein, insbesondere die Reihenentwicklung
und das Residuum. Die Darstellung hier folgt Kapitel 1 aus
\cite{boyd_chebyshev_2000}.

### Reihenentwicklung

In abstrakter Schreibweise suchen wir nach unbekannten Funktionen
$$u(x,y,z,...)$$ die einen Satz von Differentialgleichungen

$$
    \mathcal{L} u(x,y,z,\ldots) = f(x,y,z,\ldots)
    \label{eq:gendgl}
$$

erfüllen. Hierbei ist $$\mathcal{L}$$ ein (nicht zwingend linearer) Operator,
der die Differential- (oder Integral-)operationen enthält.  Zur (numerischen)
Lösung der Differentialgleichung führen wir nun ein wichtiges Konzept ein: Wir
nähern die Funktion $$u$$ durch eine *Reihenentwicklung* an. Wir schreiben

$$
    u_N(x, y, z, \ldots)
    =
    \sum_{n=0}^N a_n \varphi_n(x,y,z,\ldots)
    \label{eq:seriesexpansion}
$$

wobei die $$\varphi_n$$ als "Basisfunktionen" bezeichnet werden. Wir werden die
Eigenschaften dieser Basisfunktionen in mehr Details im nächsten Kapitel
diskutieren.

Die Differentialgleichung können wir nun schreiben als,

$$
    \mathcal{L} u_N(x,y,z,\ldots) = f(x,y,z,\ldots).
$$

Durch diese Darstellung wird erreicht, dass wir nun die Frage nach der
unbekannten Funktion $$u$$ durch die Frage nach den unbekannte Koeffizienten
$$a_n$$ ersetzt haben.  Den Differentialoperator $$\mathcal{L}$$ müssen wir nur
auf die (bekannten) Basisfunktionen $$\varphi_n$$ wirken lassen, und dies
können wir analytisch berechnen.

Was verbleibt ist die Bestimmung der Koeffizienten $$a_n$$.
Diese Koeffizienten sind Zahlen, und diese Zahlen können von einem Computer
berechnet werden. Gleichung~\eqref{eq:seriesexpansion} ist selbstverständlich
eine Näherung. Für gewisse Basisfunktionen kann gezeigt werden, dass diese
"vollständig" sind und damit bestimmte Klassen von Funktionen exakt abbilden
können. Dies stimmt aber nur unter der Bedingung, dass die Reihe
Gl.~\eqref{eq:seriesexpansion} bis $$N\to\infty$$ geführt wird. Für alle
praktischen Anwendungsfälle (so wie Implementierungen in Computercode), muss
diese Reihenentwicklung jedoch abgebrochen werden. Eine "gute"
Reihenentwicklung approximiert die exakte Lösung bereits bei niedrigem $$N$$ mit
kleinem Fehler. Wir müssten bei dieser Aussage natürlich noch spezifizieren,
wie wir Fehler quantifizieren möchten. Numerisch suchen wir dann genau nach den
Koeffizienten $$a_n$$, die den Fehler minimieren.

Die Wahl guter Basisfunktion ist nichttrivial. Wir werden hier hauptsächlich
"finite Elemente" als Basisfunktionen nutzen und andere Arten kurz ansprechen.
Bevor wir tiefer in dieses Thema einsteigen, brauchen wir noch weitere Konzepte
für das Verständnis der numerischen Analyse.

### Residuum

Ein wichtiges Konzept ist das des *Residuums*. Unser Ziel ist es,
Gl.~\eqref{eq:gendgl} zu lösen. Für die exakte Lösung wäre $$\mathcal{L} u -
f\equiv 0$$. Da wir aber nur eine Näherungslösung konstruieren können, wird
diese Bedingung nicht exakt erfüllt sein. Wir definieren das Residuum als genau
diese Abweichung von der exakten Lösung, nämlich

$$
    R(x,y,z,\ldots; a_0, a_1, \ldots, a_N)
    =
    \mathcal{L} u_N(x,y,z,\ldots) - f(x,y,z,\ldots).
    \label{eq:residual}
$$

Das Residuum ist damit eine Art Maß für den Fehler den wir machen. Die
Strategie zur numerischen Lösung der Differentialgleichung
Gl.~\eqref{eq:gendgl}, ist es nun, die Koeffizienten $$a_n$$ so zu bestimmen,
dass das Residuum Gl.~\eqref{eq:residual} minimal wird. Wir haben damit die
Lösung der Differentialgleichung auf ein Optimierungsproblem abgebildet. Die
unterschiedlichen numerischen Verfahren, die wir in den nächsten Kapiteln
diskutieren werden, entscheiden sich hier hauptsächlich in der spezifischen
Optimierungsstrategie.

<div class="graybox">
Numerische Verfahren für die *Optimierung* sind ein zentraler Kern der
numerischen Lösung von Differentialgleichungen und damit der
Simulationstechniken. Es gibt unzählige Optimierungsverfahren, die in
unterschiedlichen Situationen besser oder schlechter funktionieren. Wir werden
hier zunächst solche Optimierer als "Black Box" behandeln. Zum Ende der
Lehrveranstaltung werden wir zur Frage der Optimierung zurückkehren und einige
bekannte Optimierungsverfahren diskutieren. Der Begriff
*Minimierungsverfahren* wird oft synonym zu Optimierungsverfahren
verwendet. Eine gute Übersicht über Optimierungsverfahren bietet das Buch von
\cite{nocedal_numerical_2006}.
</div>

### Ein erstes Beispiel
\label{sec:first_example}

\video{https://uni-freiburg.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=025ad4dc-b395-4980-8fdc-ac84016870c8}

Wir wollen nun diese abstrakten Ideen an einem Beispiel konkretisieren und ein
paar wichtige Begriffe einführen. Wir schauen uns das eindimensionale
Randwertproblem,

$$
    \frac{\text{d}^2 u}{\text{d} x^2} - (x^6 + 3x^2)u = 0,
    \label{eq:odeexample}
$$

mit den Randbedingungen $$u(-1)=u(1)=1$$ an. (D.h. $$x\in[-1,1]$$ ist die
Domäne auf der wir die Lösung suchen.) Der abstrakte Differentialoperator
$$\mathcal{L}$$ nimmt in diesem Fall die konkrete Form

$$
    \mathcal{L} = \frac{\text{d}^2 }{\text{d} x^2} - (x^6 + 3x^2)
$$

an.
Die exakte Lösung dieses Problems ist gegeben durch

$$
    u(x) = \exp\left[(x^4-1)/4\right].
$$


Wir raten nun eine Näherungslösung als Reihenentwicklung für diese Gleichung.
Diese Näherungslösung sollte bereits die Randbedingungen erfüllen. Die
Gleichung

$$
    u_2(x) = 1 + (1-x^2)(a_0 + a_1 x + a_2 x^2)
    \label{eq:approxexample}
$$

ist so konstruiert, dass die Randbedingungen erfüllt sind. Wir können diese als

$$
    u_2(x) = 1 + a_0 (1-x^2) + a_1 x (1-x^2) + a_2 x^2 (1-x^2)
$$

umschreiben, um die Basisfunktionen $$\varphi_i(x)$$ zu exponieren. Hier
$$\varphi_0(x)=1-x^2$$, $$\varphi_1(x)= x (1-x^2)$$ und $$\varphi_2(x) = x^2
(1-x^2)$$. Da diese Basisfunktionen auf der gesamten Domäne $$[-1,1]$$ ungleich
Null sind, heißt diese Basis eine *spektrale* Basis. (Mathematisch: Der
Träger der Funktion entspricht der Domäne.)

Im nächsten Schritt müssen wir das Residuum

$$
    R(x; a_0, a_1, a_2) = \frac{\text{d}^2 u_2}{\text{d} x^2} - (x^6 + 3x^2)u_2
$$

minimieren. Hierfür wählen wir eine Strategie, die als *Kollokation*
bezeichnet wird: Wir verlangen, dass an drei ausgewählten Punkten das Residuum
exakt verschwindet:

$$
    R(x_i; a_0, a_1, a_2)=0
    \quad\text{für}\quad
    x_0=-1/2, x_1=0\;\text{und}\;x_2=1/2.
$$


<div class="graybox">
Das Verschwinden des Residuums bei \(x_i\) bedeutet nicht, dass auch
\(u_2(x_i)\equiv u(x_i)\), also dass bei \(x_i\) unsere approximative Lösung
der exakten Lösung entspricht. Wir sind immer noch auf einen begrenzten Satz
von Funktionen, nämlich die Funktionen die durch Gl.~\eqref{eq:approxexample}
erfasst werden, beschränkt.
</div>

Aus der Kollokationsbedingung bekommen wir nun ein lineares Gleichungssystem
mit drei Unbekannten:

$$
\begin{aligned}
    R(x_0; a_0, a_1, a_2) \equiv& -\frac{659}{256} a_0 + \frac{1683}{512} a_1 - \frac{1171}{1024} a_2 - \frac{49}{64} = 0 \\
    R(x_1; a_0, a_1, a_2) \equiv& -2(a_0-a_2) = 0 \\
    R(x_2; a_0, a_1, a_2) \equiv& -\frac{659}{256} a_0 - \frac{1683}{512} a_1 - \frac{1171}{1024} a_2 - \frac{49}{64} = 0 \\
\end{aligned}
$$

Die Lösung dieser Gleichungen ergibt

$$
    a_0 = -\frac{784}{3807}, \quad a_1 = 0 \quad \text{und} \quad a_2 = a_0.
$$

Abbildung~\ref{fig:first_example} zeigt die "numerische" Lösung $$u_2(x)$$ im
Vergleich mit der exakten Lösung $$u(x)$$.


<figure>
  <img src="{{ site.baseurl }}/figs/numerical_example.png" 
           alt="NumericalExample">
  <figcaption align="center">Abbildung 4.1: Analytische Lösung 
    \(u(x)\) und "numerische" approximative Lösung \(u_2(x)\) 
    der GDGL~\eqref{eq:odeexample}.
  </figcaption>
</figure>

In dem hier dargestellten numerischen Beispiel können sowohl die
Basisfunktionen als auch die Strategie für die Minimierung des Residuums
variiert werden. Im Laufe dieser Lehrveranstaltung werden wir als
Basisfunktionen die finiten Elemente etablieren und als Minimierungsstrategie
die Galerkin-Methode nutzen. Hierzu müssen wir zunächst Eigenschaften möglicher
Basisfunktionen diskutieren.

<div class="graybox">
Das hier dargestellte Beispiel ist ein einfacher Fall einer
*Diskretisierung*. Wir sind von einer kontinuierlichen Funktion auf die
diskreten Koeffizienten \(a_0\), \(a_1\), \(a_2\) übergegangen.
</div>

## Konzept des Funktionenraums

<div class="graybox">
Bevor wir tiefer in die numerische Lösung von partiellen
Differentialgleichungen einsteigen, müssen wir hier ein leicht abstraktes
Konzept einführen: Das Konzept der *Funktionenräume*, bzw. konkreter des
*Hilbertraums}. Funktionenräume sind nützlich, weil sie die
Reihenentwicklung formalisieren und durch das Konzept der Basisfunktionen einen
einfachen Zugang zu den Koeffizienten einer Reihenentwicklung liefern.
</div>

### Vektoren

Zur Einführung erinnern wir an die üblichen kartesischen Vektoren. Einen Vektor
$\v{a}=(a_0, a_1, a_2)$ können wir als Linearkombination aus Basisvektoren
$\hat{e}_0$, $\hat{e}_1$ und $\hat{e}_2$,

$$
    \v{a} = a_0 \hat{e}_0 + a_1 \hat{e}_1 + a_2 \hat{e}_2,
$$

schreiben. Die Einheitsvektoren $\hat{e}_0$, $\hat{e}_1$ und $\hat{e}_2$ sind
natürlich die Vektoren, welche das kartesische Koordinatensystem aufspannen.
(In vorherigen Kapiteln wurde auch die Notation $\hat{x}\equiv\hat{e}_0$,
$\hat{y}\equiv\hat{e}_1$ und $\hat{z}\equiv\hat{e}_2$ genutzt.) Die Zahlen
$a_0$, $a_1$ und $a_2$ sind die Komponenten oder *Koordinaten} des
Vektors, aber auch die Koeffizienten der Einheitsvektoren. In diesem Sinne sind
sie identisch zu den Entwicklungskoeffizienten der Reihenentwicklung, mit dem
Unterschied, dass die $\hat{e}_i$ orthogonal sind, also

$$
    \hat{e}_i\cdot\hat{e}_j = \delta_{ij}
$$

wobei $\delta_{ij}$ das Kronecker-$\delta$ ist. Zwei kartesische Vektoren
$\v{a}$ und $\v{b}$ sind orthogonal, wenn das Skalarprodukt zwischen ihnen
verschwindet:

$$
    \v{a}\cdot\v{b} = \sum_i a_i b_i = 0
    \label{eq:vecscalar}
$$


Mit Hilfe der Basisvektoren und dem Skalarprodukt können wir direkt die
Komponenten erhalten: $a_i = \v{a}\cdot\hat{e}_i$. Dies ist eine direkte
Konsequenz der Orthogonalität der Basisvektoren $\hat{e}_i$.

### Funktionen

Im vorhergegangen Abschnitt steht die Behauptung, dass die Basisfunktionen aus
Kapitel 5 nicht orthogonal sind. Hierzu brauchen wir eine Idee für
Orthogonalität von Funktionen. Mit einer Definition eines Skalarprodukts
zwischen zwei *Funktionen} könnten wir dann Orthogonalität als
Verschwinden dieses Skalarprodukts definieren.

Wir führen nun Skalarprodukt auf Funktionen(räume) ein, das diese Eigenschaften
auch erfüllt. Gegeben zwei Funktionen $g(x)$ und $f(x)$ auf dem Interval
$x\in[a,b]$, *definieren} wir das Skalarprodukt als

$$
    (f,g) = \int_a^b \text{d} x\, f^*(x) g(x),
    \label{eq:funcscalar}
$$

wobei $f^*(x)$ die komplex-konjugierte von $f(x)$ ist. 
Dieses inneres Produkt oder Skalarprodukt ist eine Abbildung mit den Eigenschaften

- Positiv definit: $(f,f)\ge 0$ und $(f,f)=0\Leftrightarrow f=0$
- Sesquilinear: $(\alpha f+\beta g,h)=\alpha^*(f,h)+\beta^*(g,h)$
- Hermitesch: $(f,g)=(g,f)^*$

Die Skalarprodukte Gl.~\eqref{eq:vecscalar} und \eqref{eq:funcscalar} erfüllen
beide diese Eigenschaften.

<div class="graybox">
Das Skalarprodukt zwischen zwei Funktionen wird oft allgemeiner mit einer
Gewichtsfunktion $w(x)$ definiert,

$$
  (f,g) = \int_a^b \text{d} x\, f^*(x) g(x) w(x).
$$

Die Frage nach Orthogonalität zwischen Funktionen kann damit nur respektive
einer bestimmten Definition des Skalarprodukts geklärt werden. So sind z.B. die
Tschebyschow-Polynome respektive der Gewichtsfunktion $w(x)=(1-x^2)^{-1/2}$
orthogonal. Innerhalb dieser Lehrveranstaltung werden wir nur den Fall $w(x)=1$
benötigen.
</div>

### Basisfunktionen
\label{sec:basis-functions}

Kommen wir nun zurück zur Reihenentwicklung,

$$
    f_N(x) = \sum_{n=0}^N a_n \varphi_n(x).
    \label{eq:series2}
$$

Die Funktionen $\varphi_i(x)$ heißen *Basisfunktionen}. Eine notwendige
Eigenschaft der Basisfunktionen ist deren lineare Unabhängigkeit. Die
Funktionen sind linear unabhängig, wenn keine der Basisfunktionen selbst als
Linearkombination, also in der Form der Reiheentwicklung
Gl.~\eqref{eq:series2}, der anderen Basisfunktionen geschrieben werden kann.
D.h. es muss erfüllt sein, dass

$$
    \sum_{n=0}^{N}a_n \varphi_n(x) = 0
$$

dann und nur dann wenn alle $a_n=0$.
Linear unabhängige Elemente bilden eine Basis.

Diese Basis heißt vollständig, wenn alle relevanten Funktionen (= Elemente des
zu Grunde liegenden Vektorraums) sich durch die
Reihenentwicklung~\eqref{eq:series2} abbilden lassen. (Beweise der
Vollständigkeit von Basisfunktionen sind komplex und außerhalb des Fokus dieser
Lehrveranstaltung.) Die Koeffizienten $a_n$ heißen Koordinaten oder
Koeffizienten. Die Anzahl der Basisfunktionen bzw. der Koordinaten $N$ nennt
man die *Dimension} des Vektorraums.

<div class="graybox">
Ein *Vektorraum} ist eine Menge, auf der die Operationen der Addition
und Skalarmultiplikation mit den üblichen Eigenschaften, wie der Existenz von
neutralen und inversen Elementen und Assoziativ-, Kommutativ- und
Distributivgesetzen, definiert sind. Ist dieser Raum auf Funktionen definiert,
dann spricht man auch von einem *Funktionenraum}. Existiert zusätzlich ein
Skalarprodukt wie Gl.~\eqref{eq:funcscalar}, dann spricht man von einem
*Hilbertraum}.
<div>

Besonders nützliche Basisfunktionen sind orthogonal. Mit Hilfe des
Skalarprodukts können wir nun Orthogonalität für diese Funktionen definieren.
Zwei Funktionen $f$ und $g$ sind orthogonal wenn das Skalarprodukt
verschwindet, $(f, g) = 0$. Ein Satz gegenseitig orthogonaler Basisfunktionen
erfüllt

$$
    (\varphi_n, \varphi_m) = \nu_{n} \delta_{nm},
$$

wobei $\delta_{nm}$ das Kronecker-$\delta$ ist. Für $\nu_n\equiv(\varphi_n,
\varphi_n)=1$ heißt die Basis *orthonormal}.

Die Orthogonalität ist nützlich, weil sie uns einen Weg aufzeigt, mit dem wir
die Koeffizienten der Reihenentwicklung~\eqref{eq:series2} bekommen können:

$$
 (\varphi_n, f_N)
 =
 \sum_{i=0}^N a_i (\varphi_n, \varphi_i)
 =
 \sum_{i=0}^N a_i \nu_i \delta_{ni}
 =
 a_n \nu_n
$$

bzw.

$$
 a_n = \frac{(\varphi_n, f_N)}{(\varphi_n, \varphi_n)}.
 \label{eq:coordinates}
$$

D.h. die Koordinaten sind gegeben durch die Projektion (das Skalarprodukt) der
Funktion auf die Basisvektoren. Wir erinnern uns daran, dass auch für
kartesische Vektoren gilt: $a_n = \v{a}\cdot\hat{e}_n$. (Der Normierungsfaktor
entfällt hier, weil $\hat{e}_n\cdot\hat{e}_n=1$.) Die Koordinaten, die durch
Gl.~\eqref{eq:coordinates} gegeben sind, sind in genau dem gleichen Kontext zu
sehen.

### Fourier-Basis
\label{sec:fouirer-basis}

\video{https://uni-freiburg.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=6e2bcafd-24b2-4ee5-b58c-ac840157f7bc}

Ein berühmter und wichtiger Satz von Basisfunktionen ist die
*Fourier-Basis},

$$
 \varphi_n(x) = \exp\left( i q_n x \right),
 \label{eq:fourier-basis}
$$

auf dem Interval $x\in[0,L]$ mit $q_n = 2\pi n/L$ und $n\in\mathbb{Z}$. Die
Fourier-Basis ist periodisch auf diesem Interval und in
Abb.~\ref{fig:fourierbasis} gezeigt. Es kann einfach gezeigt werden, dass

$$
 (\varphi_n, \varphi_m) = L \delta_{nm},
$$

also dass die Fourier-Basis orthogonal ist. Die Koeffizienten $a_n$ der
Fourier-Reihe,

$$
 f_N(x) = \sum_{n=-N}^N a_n \varphi_n(x),
 \label{eq:fourierseries}
$$

können damit für eine Reihe $f_N(x)$ direkt als

$$
 a_n=\frac{1}{L}(\varphi_n, f_N)=\frac{1}{L}\int_0^L \text{d} x\, f_N(x) \exp\left(-i q_n x\right)
$$

bestimmt werden. Dies ist die bekannte Formel für die Koeffizienten der
Fourier-Reihe. Man beachte, dass die Summe in Gl.~\eqref{eq:fourierseries} von
$-N$ bis $N$ läuft und man $2N+1$ Koeffizienten erhält.

<figure>
  <img src="{{ site.baseurl }}/figs/fourierbasis.png" alt="FourierBasis">
  <figcaption align="center">Abbildung 4.2: Realteil der
  Fourier-Basisfunktionen, Gl.~\eqref{eq:fourier-basis}, für $n=1,2,3,4$. Die
  Basisfunktionen höherer Ordnung oszillieren mit einer kleineren Periode und
  repräsentieren höhere Frequenzen.
  </figcaption>
</figure>

<div class="graybox">
Konzeptuell beschreibt die Fourier-Basis unterschiedliche
Frequenzkomponenten, während die Basis der im nächsten Abschnitt beschriebenen
finiten Elemente unterschiedliche Raumbereiche beschreibt.
</div>

### Finite Elemente
\label{sec:finite-element-basis}

\video{https://uni-freiburg.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=ec080e9a-ff09-4366-8784-ac840166145c}

Wir werden hier hauptsächlich mit der Basis der finiten Elemente arbeiten. Im
Gegensatz zur Fourier-Basis, die auf der gesamten Domäne nur an isolierten
Punkten gleich Null wird, ist die Finite-Elemente-Basis im Raum lokalisiert und
für große Bereiche der Domäne Null. Sie zerlegt damit die Domäne in räumliche
Abschnitte.

In ihrer einfachsten Form besteht die Basis aus lokalisierten abschnittsweise
linearen Funktionen, der "Zelt"-Funktion,

$$
    \varphi_n(x) = \left\{
    \begin{array}{ll}
       \frac{x-x_{n-1}}{x_n - x_{n-1}} & \text{für}\; x\in[x_{n-1},x_n]\\
       \frac{x_{n+1-x}}{x_{n+1} - x_n} & \text{für}\; x\in[x_n,x_{n+1}] \\
       0 & \text{sonst}
    \end{array}
    \right.
    \label{eq:finite-element-basis}
$$

Hierbei sind die $x_n$ die Stützstellen (auch Gitterpunkte oder Knoten - engl.
"node"), zwischen denen die Zelte aufgespannt sind. Die Funktionen sind so
konstruiert, dass $\int_0^L \text{d} x\,\varphi_n(x)=(x_{n+1}-x_{n-1})/2$.
Diese Basis ist die einfachste Form der finite Elemente-Basis und in
Abb.~\ref{fig:febasis} gezeigt. Für höhere Genauigkeit werden auch Polynome
höherer Ordnung eingesetzt.

<figure>
  <img src="{{ site.baseurl }}/figs/febasis.png" 
           alt="FEBasis">
  <figcaption align="center">Abbildung 4.3: Die Basis der finiten Elemente in
  ihrer einfachsten, linearen Inkarnation. Jede Basisfunktion ist ein "Zelt",
  dass über ein gewisses Interval zwischen $0$ und $1$ und wieder zurück
  verläuft, siehe auch Gl.~\eqref{eq:finite-element-basis}.} \label{fig:febasis}
  </figcaption>
</figure>

Ein wichtiger Hinweis an dieser Stelle ist, dass die Basis der finiten Elemente
*nicht} orthogonal ist. In unserem eindimensionalen Fall verschwindet das
Skalarprodukt nicht für die nächsten Nachbarn. Dies ist deshalb der Fall, weil
bei zwei Nachbarn jeweils eine steigende und eine fallende Flanke überlappt.
Man erhält

$$
\begin{aligned}
    M_{nn} \equiv (\varphi_n, \varphi_n) &= \frac{1}{3}(x_{n+1}-x_{n-1}) \\
    M_{n,n+1} \equiv (\varphi_n, \varphi_{n+1}) &= \frac{1}{6}(x_{n+1}-x_n) \\
    M_{nm} \equiv (\varphi_n, \varphi_m) &= 0 \quad\text{für}\;|n-m|>1
\end{aligned}
$$

für die Skalarprodukte.

Trotzdem können wir diese Relationen nutzen, um die Koeffizienten einer
Reihenentwicklung, 
$$
    f_N(x) = \sum_{n=0}^N a_n \varphi_n(x)
$$

zu berechnen. Man erhält

$$
    \begin{split}
        (\varphi_n, f_N(x)) &= a_{n-1} (\varphi_n, \varphi_{n-1}) + a_n (\varphi_n, \varphi_n) + a_{n+1} (\varphi_n, \varphi_{n+1}) \\
        &= M_{n,n-1} a_{n-1} + M_{nn} a_n + M_{n,n+1} a_{n+1}.
    \end{split}
$$

Dies können wir als

$$
    (\varphi_n, f_N(x)) = \left[ \t{M}\cdot \v{a} \right]_n 
$$

schreiben, wobei $[\v{v}]_n=v_n$ die $n$te Komponente des Vektors, welcher
durch die beiden eckigen Klammer $[\cdot]_n$ eingeschlossen wird, bezeichnet.
Die Matrix $\t{M}$ ist *dünnbesetzt} (engl. "sparse"). Für eine
orthogonale Basis, wie beispielsweise die Fourier-Basis in
Abschnitt~\ref{sec:fouirer-basis}, ist diese Matrix diagonal. Für eine Basis
mit identischen Abständen $x_{n+1}-x_n=1$ der Stützstellen $x_n$ hat die Matrix
die folgende Form

$$
    \t{M} = \begin{pmatrix}
        2/3 & 1/6 & 0 & 0 & 0 & 0 & \cdots \\
        1/6 & 2/3 & 1/6 & 0 & 0 & 0 & \cdots \\
        0 & 1/6 & 2/3 & 1/6 & 0 & 0 & \cdots \\
        0 & 0 & 1/6 & 2/3 & 1/6 & 0 & \cdots \\
        0 & 0 & 0 & 1/6 & 2/3 & 1/6 & \cdots \\
        0 & 0 & 0 & 0 & 1/6 & 2/3 & \cdots \\
        \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \ddots
    \end{pmatrix}.
$$

Um die Koeffizienten $a_n$ zu finden, muss also ein (dünnbesetztes) lineares
Gleichungssystem gelöst werden. Wir werden $\t{M}$ später unter dem Namen
*Massematrix} wieder treffen.

<div class=§graybox">
Basissätze, die nur an individuellen Punkten von Null verschieden sind, nennt
man *spektrale} Basissätze. Insbesondere ist die Fourier-Basis ein
spektraler Basissatz für periodische Funktionen. Grundsätzlich bilden die
*orthogonalen Polynome} wichtige spektrale Basissätze die auch in der
Numerik Anwendung finden. So sind beispielsweise die Tschebyschow-Polynome gute
Basissätze für auf abgeschlossenen Intervallen definierte nicht-periodische
Funktionen. Die Basis der finiten Elemente ist keine spektrale Basis.

