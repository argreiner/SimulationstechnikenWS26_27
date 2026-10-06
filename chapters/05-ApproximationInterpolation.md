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
    \tag{5.1}
$$

Gleichungen (5.1) können nun nach $$a_k$$ aufgelöst
werden. Wir nutzen dazu, dass für äquidistanter Kollokationspunkte die
Fourier-Matrix $$W_{kn}=\exp(i2\pi kn/(2N+1))$$ (bis auf einen Faktor) unitär
ist, d.h. ihr Inverses ist durch die Adjungierte gegeben: $$\sum_n W_{kn}
W_{nl}^* = (2N+1)\delta_{kl}$$ Wir können also
Gl. (5.1) mit $$W_{nl}^*$$ multiplizieren und über
$$n$$ summieren. Dies ergibt

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
$$f(x)=\sin(2\pi x)^3 + \cos(6\pi(x^2-1/2))$$ mit Hilfe der Fourier-Basis und
der finiten Elemente. Abbildung 5.1 zeigt diese Approximation für $$2N+1=5$$
und $$2N+1=11$$ Basisfunktionen mit äquidistanten Kollokationspunkten.

<figure>
  <img src="{{ site.baseurl }}/figs/coll5.png" alt="Collocation5">
</figure>
<figure>
  <img src="{{ site.baseurl }}/figs/coll11.png" alt="Collocation11">
  <figcaption align="center">Abbildung 5.1: Approximation der auf dem Interval
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

Wir möchten nun die Kollokationsmethode verallgemeinern. Hierzu führen wir das
Konzept der *Testfunktion* ein. Anstelle zu verlangen, dass das Residuum
an individuellen Punkten verschwindet, verlangen wir, dass das Skalarprodukt

$$
    (v, R) = 0
    \tag{5.2}
$$

mit einer Funktion $$v(x)$$ verschwindet. Wenn Gl. (5.2) für
jede beliebigen Testfunktion $$v(x)$$ verschwindet, dann ist die "schwache"
Formulierung Gl. (5.2) identisch zur starken Formulierung
$$R(x)=0$$. Gleichung (5.2) heißt "schwache" Formulierung,
weil die Bedingung nur im integralen Sinne erfüllt ist. Insbesondere wird in
Kapitel über die Finite Elemente Methode gezeigt, dass diese schwache
Formulierung zu einer schwachen *Lösung* (engl. "weak solution") führt, die die
ursprüngliche (starke) PDGL nicht in jedem Punkt erfüllen kann. Die Bedingung
(5.2) wird oft unter dem Begriff der *gewichteten Residuen* subsumiert.

Ein spezieller Satz an Testfunktion führt direkt zur Kollokationsmethode. Wir
wählen den Satz von $$N$$ Testfunktionen

$$
  v_n(x) = \delta(x-y_n)
  \tag{5.3}
$$

wobei $$\delta(x)$$ die Diracsche $$delta$$-Funktion ist und $$y_n$$ die
Kollokationspunkte. Die Bedingung $$v_n,R)=0$$ für alle $$n\in[0,N-1]$$ führt
direkt zur Kollokationsbedingung $$R(y_x)=0$$

<div class="graybox">
Die Diracsche \(delta\) Funktion sollte aus Vorlesungen zur Signalverarbeitung
bekannt sein. Die wichtigste Eigenschaft dieser Funktion ist die
Filtereigenschaft,

$$
  \int_{-\infty}^{\infty} \text{d} x\, f(x) \delta(x-x_0) = f/(x_0),
$$

also das Integral über das Produkt der \(\delta\)-Funktion ergibt den
Funktionswert, bei dem das Argument der \(\delta\)-Funktion verschwindet. Hieraus
folgen alle weiteren Eingenschaften, z.B.

$$
  \int\text{d} x\, \delta(x) = \Theta(x),
$$

wobei \(\theta(x)\) die (Heaviside-)Stufenfunktion ist.
</div>

## Galerkin-Methode

Die Galerkin-Methode basiert auf der Idee, als Testfunktionen die
Basisfunktionen $$\varphi_n$$ der Reihenentwicklung zu verwenden. Dies führt zu
den $$N$$ Bedingungen

$$
  (\varphi_n, R) = 0,
  \tag{5.4}
$$

bzw.

$$
  (\varphi_n, f_N) = (\varphi_n, f).
$$

Für einen orthogonalen Satz von Basisfunktionen erhält man direkt

$$
  a_n = \frac{(\varphi_n, f)}{(\varphi_n, \varphi_n)}.
$$

Dieser Ansatz wurde bereits im Kapitel über Funktionenräume diskutiert.

Für einen nicht-orthogonalen Basissatz, z.B. der Basis der finiten Elemente,
erhält man ein lineares Gleichungssystem,

$$
  \sum_{m=0}^N (\varphi_n,\varphi_m) a_m = (\varphi_n, f),
  \tag{5.5}
$$

wobei die Matrix $$A_{nm}=(\varphi_n,\varphi_m)$$ für die finiten Elemente
dünnbesetzt ist.

Wir wollen nun wieder zu unserer Beispielfunktion $$f(x)=\sin(2\pi x)^3 +
\cos(6\pi(x^2-1/2))$$ zurückkommen. Abbildung 5.2
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
   \([0,1]\) periodischen Funktion \(f(x)=\sin(2\pi x)^3 + \cos(6\pi(x^2-1/2))\) mit
   einer Fourier-Basis und finiten Elementen. Es wurde jeweils \(5\) (oben) und \(11\)
   (unten) Basisfunktionen genutzt. Die Koeffizienten wurde mit Hilfe der
   Galerkinmethode bestimmt. Die Approximation mit \(5\) Basisfunktionen kann die
   beiden rechten Oszillationen der Zielfunktion \(f(x)\) in beiden Fällen nicht
   abbilden.
  </figcaption>
</figure>

<div class="graybox">
Die Galerkin-Bedingung (siehe auch Gl. (5.4))

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
  (f, f) + \sum_{n=0}^N \sum_{m=0}^N a_n^* a_m (\varphi_n, \varphi_m) -
  \sum_{n=0}^N a_n^* (\varphi_n, f) - \sum_{n=0}^N a_n (f, \varphi_n).
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

Dieser Ausdruck ist identisch zu Gl. (5.5) der Galerkin-Methode.


## Anwendung auf Differentialgleichungen

Die in den vorherigen Abschnitten entwickelten Ideen wenden wir auf die Lösung
von Differentialgleichungen an. In diesem Abschnitt bepsrechen wir lediglich
die Fourier-Basis. Neben der Anwendung dieses Verfahrens, erweitern wir hier
die Lösungsansätze auch auf mehrdimensionale Räume.

### Differentialoperatoren

Für die Lösung von Differentialgleichungen nutzen wir nun exakt die gleichen
Methoden, die wir im vorigen Abscnitt entwickelt haben: Minimierung des
Residuums mit Hilfe der Galerkin-Methode. Unser Residuum hat nun die allgemeine
Form,

$$
  R(x,y,z,\ldots; a_0, a_1, \ldots, a_N)
  =
  \mathcal{L} u_N(x,y,z,\ldots) - f(x,y,z,\ldots),
$$

wobei die unbekannte Funktion $$u_N$$ hier als eine Reihenentwicklung in eine
bestimme Basis $$\varphi_n(x,y,z)$$ dargestellt ist. In der Galerkin-Methode
verlangt man

$$
  (\varphi_n, R) = 0
$$

für jedes $$n$$.

Wir diskutieren zunächst die Fourier-Basis für periodische Funktionen auf $$x\in[0,L]$$ in einer Dimension,

$$
  \varphi_n(x) = \exp(i q_n x)
  \tag{5.6}
$$

mit $$q_n = 2\pi n/L$$. Der Operator $$\mathcal{L}$$ kann beliebige Differentialoperationen enthalten, die auf die Basisfunktionen wirken, beispielsweise

$$
\begin{aligned}
  \frac{d}{dx} \varphi_n(x) &= iq_n \varphi_n(x) \\
  \frac{d^2}{dx^2} \varphi_n(x) &= -q_n^2 \varphi_n(x).
\end{aligned}
$$

D.h. die Ableitungen der (Fourier-)Basisfunktionen ergeben die *gleiche* Basisfunktion und einen algebraischen Faktor. Man sagt auch, die Basisfunktionen *diagonalisieren* den Differentialoperator. (Dies wird für die finiten Elemente, die im nächsten Kapitel besprochen werden, anders sein.)

Diese Eigenschaft ist besonders nützlich, weil zumindest für lineare Differentialgleichungen damit das Residuum wieder eine triviale Reihenentwicklung wird und wir auf Grund der Orthogonalität der Basis die Koeffizienten leicht bestimmen können.

### Poisson-Gleichung in einer Dimension

Als Demonstrator für diese Verhalten nutzen wir die (eindimensionale) Poisson-Gleichung,

$$
  \nabla^2 \Phi
  \equiv
  \frac{\text{d}^2 \Phi}{\text{d} x^2}
  =
  - \frac{\rho}{\varepsilon}.
  \tag{5.7}
$$

Hier ist $$\rho$$ eine Ladungsdichte und $$\Phi$$ das elektrostatische Potential.
Das Residuum ist daher

$$
  R(x)=\frac{\text{d}^2 \Phi}{\text{d} x^2} + \frac{\rho}{\varepsilon},
  \tag{5.8}
$$

und die Lösung von Gl. (5.7) ist gegeben durch $$R(x)=0$$.

Formal schreiben wir nun das Potential als die Reihenentwicklung

$$
  \Phi(x) \approx \Phi_N(x) = \sum_{n=-N}^N a_n \varphi_n(x),
$$

wobei wir die Summationsgrenzen im folgenden nicht weiter explizit angeben werden.
Wir entwickeln auch die rechte Seite der Gl. (5.7) in eine Reihe mit den gleichen Basisfunktionen,

$$
  \rho_N(x) = \sum_{n=-N}^N b_n \varphi_n(x).
  \tag{5.9}
$$

Eingesetzt in Gl. (5.8) erhalten wir

$$
  R_N(x) = - \sum_n a_n q_n^2 \varphi_n(x) + \frac{1}{\varepsilon} \sum_n b_n \varphi_n(x). 
$$

Wir multiplizieren dies nun von links mit den Basisfunktionen, $$(\varphi_k, R_N)$$ (Galerkinmethode) und erhalten auf Grund der Orthogonalität der Basisfunktionen die Gleichungen

$$
 (\varphi_k, R_N) = - L q_k^2 a_k + L b_k/\varepsilon.
$$

(Der Faktor $$L$$ erscheint, weil die Basisfunktionen nicht normalisiert sind.) Die Bedingung $$(\varphi_k, R_N)=0$$ führt zu $$a_k = b_k/(q_k^2 \varepsilon)$$. Die approximative Lösung der Poisson-Gleichung ist damit gegeben durch

$$
  \Phi_N(x) = \sum_n \frac{b_n}{q_n^2 \varepsilon} \varphi_n(x).
  \tag{5.10}
$$

Dies ist die Fourier-Reihe der Lösung.

### Übergang zur Fourier-Transformation

Die Fourier-Basis Gl. (5.6) ist auf einem finiten Gebiet der Länge $$L$$
periodisch. Wenn wir die Länge $$L$$ gegen unendlich gehen lassen, bekommen wir
eine Formulierung für nicht-periodische Funktionen. Dies führt direkt zur
*Fourier-Transformation*.

Wir schreiben die Reihenentwicklung als

$$
  \Phi_N(x) = \sum_{n=-N}^N a_n \varphi_n(x) = \sum_{n=-N}^N a_n \exp\left( i q_n x \right) = 
              \sum_{n=-N}^N \frac{\Delta q}{2\pi}\,\tilde{\Phi}(q_n) \exp\left( i q_n x \right)
    \tag{5.11}
$$

mit $$\Delta q = q_{n+1}-q_n = 2\pi/L$$ und umskalierten Koeffizienten
$$\tilde{\Phi}(q_n)=L a_n$$. Hier wurde auf der rechten Seite von
Gl. (5.11) lediglich der Faktor $$1=L \Delta q/2\pi$$
eingefügt. Dies hilft nun, den Limes $$L\to\infty$$ und $$N\to\infty$$ zu bilden.
In diesem Fall wird $$\Delta q \to dq$$ und die Summe zum Integral. Man erhält

$$
    \Phi(x) = \int_{-\infty}^\infty \frac{\text{d} q}{2\pi}\,\tilde{\Phi}(q) \exp\left( i q x \right),
    \tag{5.12}
$$

die Fourier-Rück*transformation*.

Die (Hin-)Transformation erhält man über ein ähnliches Argument. Wir wissen nun, dass

$$
    \tilde{\Phi}(q_n)
    =
    L a_n
    =
    L \frac{(\varphi_n, \Phi_N)}{(\varphi_n, \varphi_n)}
    =
    (\varphi_n, \Phi_N)
    =
    \int_0^L \text{d} x \, \Phi_N(x) \exp\left( -i q_n x \right).
$$

Im Grenzfall $$L\to\infty$$ und $$N\to\infty$$ wird dies zu

$$
    \tilde{\Phi}(q)
    =
    \int_{-\infty}^\infty \text{d} x \, \Phi(x) \exp\left( -i q x \right),
    \tag{5.13}
$$

der Fourier-Transformation. Die Fourier-Transformation ist nützlich, um
analytische Lösungen für partielle Differentialgleichungen auf unendlichen
Gebieten zu erhalten.

<div class="graybox">
Eine Tilde \(\tilde{f}(q)\) bezeichnet die Fourier-Transformierte einer Funktion
\(f(x)\). Die Fourier-Transformierte ist eine Funktion des Wellenvektors \(q\). Im
Gegensatz dazu erhalten wir bei der Fourier-Reihe abzählbare Koeffizienten
\(a_n\). Der Grund hierfür ist die Periodizität des betrachteten Gebiets.
</div>

### Poisson-Gleichung in mehreren Dimensionen

Ähnlich wie wir eine approximierte Lösung für eine Differentialgleichung mit
Hilfe einer Reihenentwicklung konstruiert haben, können wir nun den Ansatz
Gl. (5.12) nutzen, um analytische Lösungen zu erhalten. In
diesem Abschnitt wird dies mit Hilfe der Poisson-Gleichung in drei Dimensionen
demonstriert.

In drei Dimensionen lautet die Poisson-Gleichung

$$
  \nabla^2 \Phi
  \equiv
  \frac{\partial^2 \Phi}{\partial x^2} + \frac{\partial^2 \Phi}{\partial y^2} + \frac{\partial^2 \Phi}{\partial z^2}
  =
  - \frac{\rho}{\varepsilon}.
  \tag{5.14}
$$

Im Gegensatz zu Gl. (5.7) taucht hier nun die partielle
Ableitung $$\partial$$ auf, weil $$\Phi(x,y,z)$$ nun von drei Variablen (den
kartesischen Koordinaten) abhängt.

Die Verallgemeinerung der Fourier-Basis und damit auch der
Fourier-Transformation auf drei Dimensionen ist trivial. Man erhält eine Basis,
in dem man Basisfunktionen in die kartesischen Richtungen ($$x$$, $$y$$ und $$z$$)
multipliziert. Üblicherweise braucht man nun drei Indices für die
Koeffizienten, die jeweils die Basis in $$x$$, $$y$$ und $$z$$ bezeichnen. Man erhält
als Reihenentwicklung

$$
\begin{split}
  \Phi_{NMO}(x,y,z) =& \sum_{n=-N}^N \sum_{m=-M}^M \sum_{o=-O}^O a_{nmo} \varphi_n(x) \varphi_m(y) \varphi_o(z) \\
  \equiv& \sum_{n=-N}^N \sum_{m=-M}^M \sum_{o=-O}^O a_{nmo} \varphi_{nmo}(x,y,z)
\end{split}
$$

mit (möglicherweise unterschiedlicher) Entwicklungsordnung $$N$$, $$M$$ und $$O$$.
Der Basissatz ist hier gegeben durch die Menge der Funktionen
$$\varphi_{nmo}(x,y,z)=\varphi_n(x)\varphi_m(y)\varphi_o(z)$$. Orthogonalität
dieses Basissatzes geht trivialerweise aus der Orthogonalität der
eindimensionalen Basisfunktionen $$\varphi_n(x)$$ hervor. Die Verallgemeinerung
der Fourier-Transformation folgt hieraus direkt. Die Fourier-Rücktransformation
schreibt sich als

$$
  \Phi(x,y,z) = \int_{-\infty}^\infty \frac{\text{d}^3 q}{(2\pi)^3}\,
                \tilde{\Phi}(q_x, q_y, q_z) \exp\left( i q_x x + i q_y y + i q_z z\right),
  \tag{5.15}
$$

wobei die Fouriertransformierte $$\tilde{\Phi}$$ jetzt natürlich von drei
Wellenvektoren $$q_x$$, $$q_y$$ und $$q_z$$ abhängt. Der Differentialoperator
$$\text{d}^3 q=\text{d} q_x \text{d} q_y \text{d} q_z$$ ist eine Kurznotation für
die dreidimensionale Integration.

Wir können nun Gl. (5.15) in die PDGL
Gl. (5.14) einsetzen und erhalten

$$
   R(\mathbf{r})
   =
   \int_{-\infty}^\infty \frac{\text{d}^3 q}{(2\pi)^3}\,
   \left[
   \left(-q_x^2 - q_y^2 - q_z^2\right) \tilde{\Phi}(\mathbf{q}) 
   +
   \frac{\tilde{\rho}(\mathbf{q})}{\varepsilon}
   \right]
   \exp\left( i \mathbf{q}\cdot\mathbf{r} \right)
   = 0
$$

mit $$\mathbf{r}=(x,y,z)$$ und $$\mathbf{q}=(q_x,q_y,q_z)$$.  Diese Gleichung muss für jedes
$$x,y,z$$ erfüllt sein und damit muss das Argument der Integration verschwinden,
also

$$
   -q^2 \tilde{\Phi}(\mathbf{q}) 
   +
   \frac{\tilde{\rho}(\mathbf{q})}{\varepsilon} = 0.
   \tag{5.16}
$$


<div class="graybox">
Ein alternatives Argument erhält man, wenn man die Fourier-Transformation von
\(R(x,y,z)\) hinschreibt:

$$
  R(q_x', q_y', q_z')
  =
  \int \text{d}^3 r \, R(\mathbf{r}) \exp\left( -i q_x x - i q_y y - i q_z z \right).
$$

Diese enthält Terme der Form

$$
  \int_{-\infty}^\infty \text{d} x\, \exp\left(i (q_x - q_x') x\right) = 2\pi \delta (q_x - q_x'),
$$

welche Ausdruck der Orthogonalität der Basisfunktionen sind. Da die
Basisfunktionen nun mit einem Kontinuierlichen \(q_x\) (anstelle eines diskreten
\(n\)) "parameterisiert" sind, erhält man eine Diracsche \(\delta\)-Funktion
anstelle des Kronecker-\(\delta\) in der Orthogonalitätsrelation.
</div>

Gleichung (5.16) kann einfach analytisch gelöst werden.
Man erhält

$$
   \tilde{\Phi}(\mathbf{q}) 
   =
   \frac{\tilde{\rho}(\mathbf{q})}{\varepsilon q^2}
   \tag{5.17}
$$

mit $$q=|\mathbf{q}|$$. Dies ist äquivalent zur Lösung
Gl. (5.10) für die Poisson-Gleichung auf einem
periodischen Gebiet. Die Schwierigkeit besteht nun da drin, für ein gegebenes
$$\rho(x,y,z)$$ die Hin- und Rücktransformation auszuwerten.

***Beispiel:***

*Hier Laplacegleichung 2D aus Spiegel*

Als Beispiel betrachten wir nun die Lösung für eine Punktladung $$Q$$ am
Ursprung,

$$
  \rho(x,y,z) = Q \delta(x) \delta(y) \delta(z).
$$

Die Fourier-Transformierte der Ladungsdichte $$\rho$$ erhält man aus
Gl. (5.13),

$$
  \tilde{\rho}(q_x,q_y,q_z) = Q.
$$

D.h. die Fourier-Transformierte des elektrostatischen Potentials ist gegeben
durch (siehe Gl. (5.17))

$$
  \tilde{\Phi}(\mathbf{q}) 
  =
  \frac{Q}{\varepsilon q^2},
$$

und damit lautet die Darstellung im Realraum

$$
\begin{split}
  \Phi(\mathbf{r})
  =&
  \int_{-\infty}^\infty \frac{\text{d}^3 q}{(2\pi)^3}\, \frac{Q}{\varepsilon q^2}
  \exp\left( i \mathbf{q}\cdot \mathbf{r} \right) \\
  =&
  \frac{Q}{(2\pi)^3 \varepsilon} \int_0^\infty \text{d} q \int_0^{2\pi} \text{d} \phi \int_{-1}^1 \text{d}(\cos \theta) \,  \exp\left( i q r \cos \theta \right)
\end{split}
$$

wobei $$\text{d}^3 q = q^2 \text{d} q \text{d}\phi \text{d}(\cos\theta)$$ mit
Azimutwinkel $$\phi$$ und Elevationswinkel $$\theta$$, genutzt wurde (siehe auch
Abb.~\ref{fig:volume-spherical}). Wir verlangen hier (ohne Beschränkung der
Allgemeinheit), dass $$\mathbf{r}$$ in Richtung Zenit zeigt.

Man erhält

$$
\begin{split}
  \Phi(\mathbf{r})
  =&
  \frac{Q}{(2\pi)^2 \varepsilon} \int_0^\infty \text{d} q 
  \int_{-1}^1 \text{d} (\cos\theta) \,  \exp\left( i q r \cos\theta \right)
  \\
  =&
  \frac{Q}{(2\pi)^2 \varepsilon}  \int_0^\infty \text{d} q\, \frac{\exp( i q r ) - \exp (-iqr)}{iqr}
  \\
  =&
  \frac{Q}{(2\pi)^2 \varepsilon}  \int_{-\infty}^\infty \text{d} q\, \frac{\sin q r}{qr}
  \\
  =&
  \frac{Q}{4\pi \varepsilon r},
\end{split}
$$

wobei $$\int \text{d} x\,\sin x/x=\pi$$ genutzt wurde. Dies ist die bekannte
Lösung für das elektrostatische Potential einer Punktladung. Man nennt sie auch
die Fundamentallösung oder *Greensche Funktion* der (dreidimensionalen)
Poisson-Gleichung.

\begin{figure}
\ifpdf
    \includegraphics[width=0.5\textwidth]{Figures/illustr_angles_1}
\else
    \includegraphics[width=1.0\textwidth,natwidth=141,natheight=141]{Figures/illustr_angles_1}
\fi
    \caption{Volumenelement für die Integration in Kugelkoordination}
    \label{fig:volume-spherical}
\end{figure}

