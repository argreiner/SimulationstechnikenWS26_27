---
layout: default
title: "Übung 1: Random Walk"
nav_order: 21
parent: Übungen
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Random walk
Wir nehmen an $$p\ne q$$. In Fall haben wir $$P(x,t+\tau)=pP(x+h,t)+qP(x-h,t)$$
und somit folgt

$$ \frac{P(x,t+\tau)-P(x,t)}{\tau}=\frac{h^2}{\tau}\frac{pP(x+h,t)-P(x,t)+qP(x-h,t)}{h^2}$$

Wir schreiben

$$ p=\frac{1}{2}+\varepsilon\quad\mbox{ und }\quad q=\frac{1}{2}-\varepsilon
	\mbox{ ; mit }0\le|\varepsilon|\le\frac{1}{2}$$

In den Grenzfällen $$\tau\rightarrow 0$$ und $$h\rightarrow 0$$ fordern wir 

$$
\lim_{h\rightarrow 0\atop \tau\rightarrow 0}\frac{h^2}{2\tau}=D \mbox{ and
}\lim_{h\rightarrow 0\atop \tau\rightarrow 0}\frac{h(p-q)}{\tau}=v
$$ 

Welche partielle Differentialgleichung erhalten wir nach dem Grenzübergang?
