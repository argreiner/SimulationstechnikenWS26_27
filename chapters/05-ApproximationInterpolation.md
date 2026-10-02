---
layout: default
title: Approximation und Interpolation
nav_order: 5
parent: Vorlesung
---

<!-- <script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script> -->

<!-- 1️⃣ MathJax‑Bibliothek laden -->
<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"
        id="MathJax-script"
        async></script>

<!-- 2️⃣ (optional) Konfiguration – hier definieren wir $…$ als Inline‑Delimiter>
<script>
window.MathJax = {
  tex: {
    inlineMath: [['$', '$'], ['\\(', '\\)']],   // <-- wichtig!
    displayMath: [['$$','$$'], ['\\[','\\]']],
    tags: 'ams'                                 // \label, \eqref, \tag … funktionieren
  },
  loader: {load: ['[tex]/autoload']},
  startup: {ready: () => MathJax.startup.defaultReady()}
};
</script> -->


<style>
  .graybox {
    background:#f6f6f6;          /* sehr helles Grau */
    padding:0.9em;
    border-radius:4px;
    margin:1em 0;                /* Abstand zu anderen Elementen */
  }
</style>


# Approximation und Interpolation

<div class="graybox">
Wir wenden nun die Idee der Basisfunktionen an, um Funktionen zu
approximieren. Hierfür kommen wir zu dem Konzept des Residuums zurück. Ziel der
Funktionsapproximation ist es, dass die approximierte Funktion das Residuum
minimiert. Aufbauend auf diesen Ideen besprechen wir dann im nächsten Kapitel
die Approximation von Differentialgleichungen.
</div>

## Residuum

Im vorherigen Abschnitt haben wir beschrieben, wie mit Basisfunktionen eine
Reihenentwicklung aufgebaut werden kann. Eine typische Reihenentwicklung
enthält eine endliche Zahl an Elementen $$N+1$$ und hat die Form

$$
    f_N(x) = \sum_{n=0}^N a_n \varphi_n(x),
$$

wobei die $$\varphi_n(x)$$ die im vorherigen Kapitel eingeführten Basisfunktionen
sind.

Wir wollen uns nun der Frage nähern, wie wir ein beliebige Funktion $$f(x)$$ über
eine solche Basisfunktionsentwicklung annähern können. Hierzu definieren wir
das Residuum

$$
    R(x) = f_N(x) - f(x),
$$

welches an jedem Punkt $$x$$ verschwindet wenn $$f_N(x)\equiv f(x)$$ Für eine
Approximation wollen wir dieses Residuum "minimieren". (Mit minimieren ist
hier gemeint, es möglichst nah an Null zu bringen.) Wir suchen also die
Koeffizienten $$a_n$$ der Reihenentwicklung, welche die Funktion $$f(x)$$ im Sinne
einer Minimierung des Residuums approximiert.

An dieser Stelle sei noch bemerkt, dass die Basisfunktionen auf dem gleichen
Raum für die Zielfunktion $$f(x)$$ definiert sein müssen. Für die Approximation
einer periodischen Funktion $$f(x)$$ sollte auch ein periodischer Basissatz
verwandt werden.

## Kollokation

\video{https://uni-freiburg.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=0a7985a2-0753-4d29-83fe-aca8010a16f2}

Als erste Minimierungsstrategie wird hier die *Kollokation* eingeführt. In
diese Methode wird verlangt, dass das Residuum an ausgewählten
Kollokationspunkten $$y_n$$ verschwindet,
$$
    R(y_n) = 0 \quad\text{bzw.}\quad f_N(y_n) = f(y_n).
$$
Die Anzahl der Kollokationspunkte muss hier der Anzahl der Koeffizienten in der
Reihenentwicklung entsprechen. Die Wahl der idealen Kollokationspunkte $$y_n$$
selbst ist nicht-trivial, und wir werden hier nur spezifische Fälle besprechen.

Als erstes Beispiel diskutieren wir hier eine Entwicklung mit $$N$$ finiten
Elementen. Als Kollokationspunkte wählen wir die Stützstellen der Basis,
$$y_n=x_n$$ An diesen Stützstellen ist nur eine der Basisfunktionen ungleich
Null, $$\varphi_n(y_n)=1$$ und $$\varphi_n(y_k)=0$$ falls $$n\not=k$$ Damit führt
die Bedingung
$$
    R(y_n) = 0
$$
trivial zu
$$
    a_n = f(y_n).
$$
Die Koeffizienten $$a_n$$ sind also durch den Funktionswert der zu
approximierenden Funktion am Kollokationspunkt gegeben. Die Approximation ist
damit eine stückweise lineare Funktion zwischen den Funktionswerten von $$f(x)$$

Als zweites Beispiel diskutieren wir hier eine Fourier-Reihe mit entsprechenden
$$2N+1$$ Fourier-Basisfunktionen, 
$$
    \varphi_n(x) = \exp\left( i q_n x \right).
$$
Im Rahmen einer Kollokationsmethode, verlangen wir, dass das Residuum auf $$2N+1$$ äquidistanten Punkten verschwindet, $$R(y_n)=0$$ mit
$$
    y_n = n L / (2N+1).
$$
Die Bedingung dafür lautet dann
$$
    \sum_{k=-N}^{N} a_k \exp\left(i q_k y_n\right)
    =
    \sum_{k=-N}^{N} a_k \exp\left(i 2\pi \frac{k n}{2N+1}\right)
    =
    f(y_n).
    \label{eq:fourier-collocation}
$$
Gleichungen~\eqref{eq:fourier-collocation} können nun nach $$a_k$$ aufgelöst
werden. Wir nutzen dazu, dass für äquidistanter Kollokationspunkte die
Fourier-Matrix $$W_{kn}=\exp(i2\pi kn/(2N+1))$$ (bis auf einen Faktor) unitär
ist, d.h. ihr Inverses ist durch die Adjungierte gegeben: $$sum_n W_{kn}
W_{nl}^* = (2N+1)\delta_{kl}$$
Wir können also Gl.~\eqref{eq:fourier-collocation} mit $$W_{nl}^*$$ multiplizieren und über $$n$$ summieren. Dies ergibt
$$
    \sum_{n=-N}^{N}
    \sum_{k=-N}^{N}
    a_k \exp\left[i 2\pi \frac{(k - l) n}{2N+1}\right]
    =
    \sum_{k=-N}^{N}
    N
    a_k
    \delta_{kl}
    =
    N a_l
$$
%    =
%    \sum_{n=-N}^{N}
%    f(y_n)
%    \exp\left(-i 2\pi \frac{l n}{2N+1}\right),
wobei
$$
    \sum_{n=-N}^{N}
    \exp\left[i 2\pi \frac{(k - l) n}{2N+1}\right]
    =
    (2N+1)\delta_{kl}
$$
genutzt wurde. Damit können die Koeffizienten als
$$
    a_l
    =
    \frac{1}{2N+1}
    \sum_{n=-N}^{N}
    f\left(\frac{nL}{2N+1}\right)
    \exp\left(-i 2\pi \frac{l n}{2N+1}\right),
$$
bestimmt werden. Dies ist die *diskrete Fourier-Transformation* der auf
den Kollokationspunkten diskretisierten Funktion $$f(y_n)$$

Als einfaches Beispiel zeigen wir hier Approximation der Beispielfunktion
$$f(x)=\sin(2\pi x)^3 + \cos(6\pi(x^2-1/2))$$ mit Hilfe der Fourier-Basis und der
finiten Elemente. Abbildung~\ref{fig:example-collocation} zeigt diese
Approximation für $$2N+1=5$$ und $$2N+1=11$$ Basisfunktionen mit äquidistanten
Kollokationspunkten.

<figure>
  <img src="{{ site.baseurl }}/figs/col5.png" alt="Collocation5">
  <img src="{{ site.baseurl }}/figs/col11.png" alt="Collocation11">
  <figcaption align="center"> Abbildung 5.1: Approximation der auf dem Interval
   \([0,1]\) periodischen Funktion \(f(x)=\sin(2\pi x)^3 + \cos(6\pi(x^2-1/2))\) mit
   einer Fourier-Basis und finiten Elementen. Es wurde jeweils \(5\) (oben) und \(11\)
   (unten) Basisfunktionen genutzt. Die Koeffizienten wurden mit der
   Kollokationsmethode bestimmt. Die runden Punkte zeigen die Kollokationspunkte.
   Beide Approximationen laufen exakt durch diese Kollokationspunkte. (Der rechte
   Kollokationspunkt ist auf Grund der Periodizität identisch zum linken.) Die
   Approximation mit \(N=5\) Basisfunktionen kann die beiden rechten Oszillationen
   der Zielfunktion \(f(x)\) in beiden Fällen nicht abbilden.
  </figcaption>
</figure>

Die Abbildung zeigt, dass alle Approximationen, wie von der
Kollokationsbedingung verlangt, exakt durch die Kollokationspunkte laufen.
Zwischen den Kollokationspunkten *interpolieren* die beiden Ansätze
unterschiedlich. Die finiten Elementen führen zu einer linearen Interpolation
zwischen den Punkten. Die Fourier-Basis ist komplizierter. Der Kurvenverlauf
zwischen den Kollokationspunkten wird *Fourier-Interpolation* genannt.

## Gewichtete Residuen
\label{sec:weighted-residuals}

Wir möchten nun die Kollokationsmethode verallgemeinern. Hierzu führen wir das
Konzept der *Testfunktion* ein. Anstelle zu verlangen, dass das Residuum
an individuellen Punkten verschwindet, verlangen wir, dass das Skalarprodukt
$$
    (v, R) = 0
    \label{eq:test-function}
$$
mit einer Funktion $$v(x)$$ verschwindet. Wenn Gl.~\eqref{eq:test-function} für
jede beliebigen Testfunktion $$v(x)$$ verschwindet, dann ist die "schwache"
Formulierung Gl.~\eqref{eq:test-function} identisch zur starken Formulierung
$$R(x)=0$$ Gleichung~\eqref{eq:test-function} heißt "schwache" Formulierung,
weil die Bedingung nur im integralen Sinne erfüllt ist. Insbesondere wird in
Kapitel~9 gezeigt, dass diese schwache Formulierung zu einer schwachen
*Lösung* (engl. "weak solution") führt, die die ursprüngliche (starke)
PDGL nicht in jedem Punkt erfüllen kann. Die Bedingung~\eqref{eq:test-function}
wird oft unter dem Begriff der *gewichteten Residuen* subsumiert.

Ein spezieller Satz an Testfunktion führt direkt zur Kollokationsmethode. Wir wählen den Satz von $$N$$ Testfunktionen
$$
  v_n(x) = \delta(x-y_n)
  \label{eq:colloctest}
$$
wobei $$delta(x)$$ die Diracsche $$delta$$-Funktion ist und $$y_n$$ die
Kollokationspunkte. Die Bedingung $$v_n,R)=0$$ für alle $$n\in[0,N-1]$$ führt
direkt zur Kollokationsbedingung $$R(y_x)=0$$

<div class="graybox">
Die Diracsche \(delta\) Funktion sollte aus Vorlesungen zur Signalverarbeitung
bekannt sein. Die wichtigste Eigenschaft dieser Funktion ist die
Filtereigenschaft,
$$
  \int_{-\infty}^{\infty} \dif x\, f(x) \delta(x-x_0) = f/(x_0),
$$
also das Integral über das Produkt der \(\delta\)-Funktion ergibt den
Funktionswert, bei dem das Argument der \(\delta\)-Funktion verschwindet. Hieraus
folgen alle weiteren Eingenschaften, z.B.
$$
  \int\dif x\, \delta(x) = \Theta(x),
$$
wobei \(\theta(x)\) die (Heaviside-)Stufenfunktion ist.
</div>

## Galerkin-Methode

\video{https://uni-freiburg.cloud.panopto.eu/Panopto/Pages/Embed.aspx?id=697b4e0d-37c0-45e6-a958-aca8010a16c3}

Die Galerkin-Methode basiert auf der Idee, als Testfunktionen die
Basisfunktionen $$\varphi_n$$ der Reihenentwicklung zu verwenden. Dies führt zu
den $$N$$ Bedingungen
$$
    (\varphi_n, R) = 0,
    \label{eq:galerkinortho}
$$
bzw.
$$
    (\varphi_n, f_N) = (\varphi_n, f).
$$

Für einen orthogonalen Satz von Basisfunktionen erhält man direkt
$$
    a_n = \frac{(\varphi_n, f)}{(\varphi_n, \varphi_n)}.
$$
Dieser Ansatz wurde bereits in Abschnitt~\ref{sec:basis-functions} diskutiert.

Für einen nicht-orthogonalen Basissatz, z.B. der Basis der finiten Elemente,
erhält man ein lineares Gleichungssystem,
$$
    \sum_{m=0}^N (\varphi_n,\varphi_m) a_m = (\varphi_n, f),
    \label{eq:galerkin-coefficients}
$$
wobei die Matrix $$A_{nm}=(\varphi_n,\varphi_m)$$ für die finiten Elemente
dünnbesetzt ist.

Wir wollen nun wieder zu unserer Beispielfunktion $$f(x)=\sin(2\pi x)^3 +
\cos(6\pi(x^2-1/2))$$ zurückkommen. Abbildung~\ref{fig:example-collocation}
zeigt die Approximation dieser Funktion mit Fourier und finite Elemente
Basissätzen und der Galerkin-Methode. Es gibt keine Kollokationspunkte und die
Approximation mit Hilfe der finiten Elemente stimmt auch nicht an den
Stützstellen exakt mit der zu approximierenden Funktion überein. Die Funktion
wird nur im integralen Sinne approximiert.

<figure>
  <img src="{{ site.baseurl }}/figs/gal5.png" alt="Galerkin5">
</figure>
<figure>
  <img src="{{ site.baseurl }}/figs/gal11.png" alt="Galerkin11">
  <figcaption align="center">Abbildung 5.2: Approximation der auf dem Interval
   $$[0,1]$$ periodischen Funktion $$f(x)=\sin(2\pi x)^3 + \cos(6\pi(x^2-1/2))$$ mit
   einer Fourier-Basis und finiten Elementen. Es wurde jeweils $$5$$ (oben) und $$11$$
   (unten) Basisfunktionen genutzt. Die Koeffizienten wurde mit Hilfe der
   Galerkinmethode bestimmt. Die Approximation mit $$5$$ Basisfunktionen kann die
   beiden rechten Oszillationen der Zielfunktion $$f(x)$$ in beiden Fällen nicht
   abbilden.
  </figcaption>
</figure>

<div class="graybox">
Die Galerkin-Bedingung (siehe auch Gl.~\eqref{eq:galerkinortho})
$$
    (\varphi_n, R) = 0,
$$
bedeutet, dass das Residuum *orthogonal* zu allen Basisfunktionen ist.
Anders ausgedrückt, im Residuum können nur noch Beiträge zur Funktion
vorkommen, die nicht mit dem gegeben Basissatz abgebildet werden können. Das
heißt aber auch, dass wir durch Erweiterung des Basissatzes unsere Lösung
systematisch verbessern können.
</div>

## Minimales Fehlerquadrat

Ein alternativer Ansatz zur Approximation ist es, das Fehlerquadrat des
Residuums, $$(R, R)$$, zu minimieren. Für eine allgemeine Reihenentwicklung mit
$$N$$ Basisfunktionen erhält man
$$
    \begin{split}
        (R, R)
        &=
        (f, f) + (f_N, f_N) - (f_N, f) - (f, f_N) \\
        &=
        (f, f) + \sum_{n=0}^N \sum_{m=0}^N a_n^* a_m (\varphi_n, \varphi_m) - \sum_{n=0}^N a_n^* (\varphi_n, f) - \sum_{n=0}^N a_n (f, \varphi_n).
    \end{split}
$$
Diese Fehlerquadrat ist dann minimiert, wenn
$$
    \frac{\partial (R,R)}{\partial a_k} = \sum_{n=0}^N a_n^* (\varphi_n, \varphi_k) - (f, \varphi_k) = 0
$$
und
$$
    \frac{\partial (R,R)}{\partial a^*_k} = \sum_{n=0}^N a_n (\varphi_k, \varphi_n) - (\varphi_k, f) = 0.
$$
Dieser Ausdruck ist identisch zu Gl.~\eqref{eq:galerkin-coefficients} der Galerkin-Methode.
