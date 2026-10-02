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
der \emph{numerischen} Lösung von Differentialgleichungen widmen. Dieses
Kapitel zeigt die Grundzüge der numerischen Analyse von Differentialgleichungen
und führt ein paar wichtige Konzepte ein, insbesondere die Reihenentwicklung
und das Residuum. Die Darstellung hier folgt Kapitel 1 aus
\cite{boyd_chebyshev_2000}.

\section{Reihenentwicklung}

In abstrakter Schreibweise suchen wir nach unbekannten Funktionen
$$u(x,y,z,...)$$ die einen Satz von Differentialgleichungen

$$
    \mathcal{L} u(x,y,z,\ldots) = f(x,y,z,\ldots)
    \label{eq:gendgl}
$$

erfüllen. Hierbei ist $$\mathcal{L}$$ ein (nicht zwingend linearer) Operator,
der die Differential- (oder Integral-)operationen enthält.  Zur (numerischen)
Lösung der Differentialgleichung führen wir nun ein wichtiges Konzept ein: Wir
nähern die Funktion $$u$$ durch eine \emph{Reihenentwicklung} an. Wir schreiben

$$
    u_N(x, y, z, \ldots)
    =
    \sum_{n=0}^N a_n \varphi_n(x,y,z,\ldots)
    \label{eq:seriesexpansion}
$$

wobei die $$\varphi_n$$ als ``Basisfunktionen'' bezeichnet werden. Wir werden die Eigenschaften dieser Basisfunktionen in mehr Details im nächsten Kapitel diskutieren.

Die Differentialgleichung können wir nun schreiben als,

$$
    \mathcal{L} u_N(x,y,z,\ldots) = f(x,y,z,\ldots).
$$

Durch diese Darstellung wird erreicht, dass wir nun die Frage nach der unbekannten Funktion $$u$$ durch die Frage nach den unbekannte Koeffizienten $$a_n$$ ersetzt haben.
Den Differentialoperator $$\mathcal{L}$$ müssen wir nur auf die (bekannten) Basisfunktionen $$\varphi_n$$ wirken lassen, und dies können wir analytisch berechnen.

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

\section{Residuum}

Ein wichtiges Konzept ist das des \emph{Residuums}. Unser Ziel ist es, Gl.~\eqref{eq:gendgl} zu lösen. Für die exakte Lösung wäre $$\mathcal{L} u - f\equiv 0$$. Da wir aber nur eine Näherungslösung konstruieren können, wird diese Bedingung nicht exakt erfüllt sein. Wir definieren das Residuum als genau diese Abweichung von der exakten Lösung, nämlich

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
Numerische Verfahren für die \emph{Optimierung} sind ein zentraler Kern der
numerischen Lösung von Differentialgleichungen und damit der
Simulationstechniken. Es gibt unzählige Optimierungsverfahren, die in
unterschiedlichen Situationen besser oder schlechter funktionieren. Wir werden
hier zunächst solche Optimierer als "Black Box" behandeln. Zum Ende der
Lehrveranstaltung werden wir zur Frage der Optimierung zurückkehren und einige
bekannte Optimierungsverfahren diskutieren. Der Begriff
\emph{Minimierungsverfahren} wird oft synonym zu Optimierungsverfahren
verwendet. Eine gute Übersicht über Optimierungsverfahren bietet das Buch von
\cite{nocedal_numerical_2006}.
</div>

\section{Ein erstes Beispiel}
\label{sec:first_example}

\video{https://uni-freiburg.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=025ad4dc-b395-4980-8fdc-ac84016870c8}

Wir wollen nun diese abstrakten Ideen an einem Beispiel konkretisieren und ein paar wichtige Begriffe einführen. Wir schauen uns das eindimensionale Randwertproblem,

$$
    \frac{\text{d}^2 u}{\text{d} x^2} - (x^6 + 3x^2)u = 0,
    \label{eq:odeexample}
$$

mit den Randbedingungen $$u(-1)=u(1)=1$$ an. (D.h. $$x\in[-1,1]$$ ist die Domäne auf der wir die Lösung suchen.) Der abstrakte Differentialoperator $$\mathcal{L}$$ nimmt in diesem Fall die konkrete Form

$$
    \mathcal{L} = \frac{\text{d}^2 }{\text{d} x^2} - (x^6 + 3x^2)
$$

an.
Die exakte Lösung dieses Problems ist gegeben durch

$$
    u(x) = \exp\left[(x^4-1)/4\right].
$$


Wir raten nun eine Näherungslösung als Reihenentwicklung für diese Gleichung. Diese Näherungslösung sollte bereits die Randbedingungen erfüllen. Die Gleichung

$$
    u_2(x) = 1 + (1-x^2)(a_0 + a_1 x + a_2 x^2)
    \label{eq:approxexample}
$$

ist so konstruiert, dass die Randbedingungen erfüllt sind. Wir können diese als

$$
    u_2(x) = 1 + a_0 (1-x^2) + a_1 x (1-x^2) + a_2 x^2 (1-x^2)
$$

umschreiben, um die Basisfunktionen $$\varphi_i(x)$$ zu exponieren. Hier $$\varphi_0(x)=1-x^2$$, $$\varphi_1(x)= x (1-x^2)$$ und $$\varphi_2(x) = x^2 (1-x^2)$$. Da diese Basisfunktionen auf der gesamten Domäne $$[-1,1]$$ ungleich Null sind, heißt diese Basis eine \emph{spektrale} Basis. (Mathematisch: Der Träger der Funktion entspricht der Domäne.)

Im nächsten Schritt müssen wir das Residuum

$$
    R(x; a_0, a_1, a_2) = \frac{\text{d}^2 u_2}{\text{d} x^2} - (x^6 + 3x^2)u_2
$$

minimieren. Hierfür wählen wir eine Strategie, die als \emph{Kollokation} bezeichnet wird: Wir verlangen, dass an drei ausgewählten Punkten das Residuum exakt verschwindet:

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

Aus der Kollokationsbedingung bekommen wir nun ein lineares Gleichungssystem mit drei Unbekannten:

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

Abbildung~\ref{fig:first_example} zeigt die ``numerische'' Lösung $$u_2(x)$$ im Vergleich mit der exakten Lösung $$u(x)$$.


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
