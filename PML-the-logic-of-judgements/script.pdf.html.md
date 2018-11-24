_typeset from [original PDF](http://archive-pml.github.io/martin-lof/pdfs/The-logic-of-judgements-1987.pdf)_

<style>
hr {
  page-break-before: always;
}
</style>

22.2.1987

# The Logic of Judgements

Workshop on General Logic, Laboratory for Foundations of Computer Science, University of Edinburgh, 23-27 February 1987

<br>

<style>
.bmg, .tbmg {
  border-bottom: 1px solid black;
}
.tbmg {
  border-top: 1px solid black;
}
.pmlgrid {
  display: grid;
  grid-template: auto auto auto auto / auto auto auto;
  white-space: nowrap;
  width: auto;
  grid-column-gap: 20px;
  align-items: center;
}
.pmlgrid p {
  margin-block-end: 0;
  margin-block-start: 0;
}
</style>

<div style="display: flex; justify-content: center;">
  
<div class="pmlgrid">

<div class="tbmg">type</br>object</div>

<div style="white-space: nowrap; text-align: center; line-height: 0.8; font-size: 80%; margin-top: -100%">judge-<br>ments<br>as<br>types<br><span style="font-size: 300%">←</span></div>

<div class="tbmg">judgement<br>proof</div>

<div style="padding-bottom: 0px">set<br>theory</div>

<div></div>

<div style="padding-bottom: 0px">logical<br>theory</div>

<div class="bmg">set<br>element</div>

<div style="white-space: nowrap; text-align: center; line-height: 0.8; font-size: 80%; margin-top: -50%"><span style="font-size: 300%">←</span><br>propo-<br>sitions<br>as<br>sets<br></div>

<div class="bmg">proposition<br>truth</div>

</div>

</div>

<br>

P.M.-L, On the meanings of the logical constants and the justification of the logical laws

<hr>

Peter Schroeder-Heister, Judgements of higher levels and standardized rules for logical constants in Martin-Löf's theory of logic, June 1985

The logical theory cannot be entirely logical since it needs at least one set for the quantifiers to ranger over.

Type formation

$$set:type$$

$$\frac{A:set}{elem(A):type}$$

$$\frac{
\begin{array}{ccc}
&&(x:\alpha)\\
\alpha:type&&\beta:type
\end{array}
}{(fun\;x:\alpha)\beta:type}$$

$\begin{array}{ccc}
&&\scriptsize\text{AUTOMATH}&&\\
&&\scriptsize\text{CONSTRUCTIONS}&&\scriptsize\text{LF}\\
&&\downarrow&&\downarrow\\
(x:\alpha)\beta&=&\lceil x:\alpha \rceil\beta&=&\Pi x:\alpha.\beta
\end{array}$

<hr>

$(\alpha)\beta=(x:\alpha)\beta\quad{\wedge} J\;\;\beta$ does not depend on $x$

Object formation

$$\frac{\alpha:type}{x:\alpha}\quad\text{(assumption)}$$

$$\frac{\begin{matrix}
(x:\alpha)\\
b:\beta
\end{matrix}}{\begin{array}{l}
(x)b:(x:\alpha)\beta\\
\lambda x:\alpha.b\quad{\scriptsize\longleftarrow\text{LF}}
\end{array}
}\quad\text{(abstraction)}$$

$$\frac{c:(x:\alpha)\beta\quad a:\alpha}{c(a):\beta(a/x)}\quad\text{(application)}$$

Equality

$$\frac{
\begin{array}{ccc}
&&(x:\alpha)\\
a:\alpha&&b:\beta
\end{array}
}{((x)b)(a)\;=\;b(a/x):\beta(a/x)}\quad(\beta)$$

$$\frac{c:(x:\alpha)\beta}{c\;=\;(x)c(x):(x:\alpha)\beta}\quad(\eta)$$

refl., symm., trans.

equals for equals, spec.

$$\frac{a:\alpha\quad\alpha=\beta:type}{a:\beta}$$

$$\frac{a:elem(A)\quad A=B:set}{a:elem(B)}$$

<hr>

$\begin{matrix}
\alpha:type&&\alpha=\beta:type\\
a:\alpha&&a=b:\alpha
\end{matrix}$

Since LF has no equality judgements, $\alpha=\beta:type$ has to be expressed by

$$\alpha,\beta:type,\quad\alpha=_{\beta\eta}\beta,$$

and $a=b:\alpha$ by

$$a,b:\alpha,\quad a=_{\beta\eta}b.$$

The equality judgements are badly needed for formalizing intuitionistic set theory in the logical framework.

A theory, like first order predicate logic or intuitionistic set theory, is specified by typing the constants which make up its signature and writing down the finitely many definitional equations that relate certain combinations of those constants.

In a sensible theory, it is decidable whether or not an expression is wellformed (meaningful) as well as whether or not two wellformed (meaningful) expressions are definitionally equal (have the same meaning).

type checking = checking the wellformedness (meaningfulness) of an expression

<hr>

$$prop:type$$

$$\frac{A:prop}{\begin{array}{c}
proof(A):type\\
A
\end{array}}$$

In the propositions as sets interpretation, we put

$$prop=set:type$$
$$proof(A)=elem(A):type$$

but it is not necessary for what follows that we have made that identification.

<hr>

Judgement formation

$$\frac{A:prop}{\begin{array}{l}
A\;true:judg\\
true(A)\\
\phantom{true(}A
\end{array}}$$

$$\frac{I:judg\quad J:judg}{\begin{array}{l}
I|J:judg\\
\;\rightarrow\quad{\scriptsize\text{(Gentzen)}}\\
\;\Rightarrow\quad{\scriptsize\text{(Schroeder-Heister)}}\\
\;\vdash\;\quad{\scriptsize\text{(LF)}}\\
\end{array}}$$



$$\frac{\begin{array}{l}
&&(x:\alpha)\\
\alpha:type&&J:Judg
\end{array}
}{\begin{array}{l}
|_{x:\alpha} J:judg\\
\rightarrow_{x:\alpha}\\
\Rightarrow_{x:\alpha}\\
\vdash_{x:\alpha}\\
\end{array}}$$

<hr>

Proof rules

$$\frac{J:judg}{J}\quad\text{(assumption)}$$


$$\frac{\begin{array}{c}
(I)\\
J
\end{array}}{
I|J
}
\quad\quad
\frac{I|J\quad I}{J}$$

$$\frac{\begin{array}{c}
(x:\alpha)\\
J
\end{array}}{
|_{x:\alpha}J
}
\quad\quad
\frac{|_{x:\alpha}J\quad a:\alpha}{J(a/x)}$$

A context (sequence of assumptions) in this system has the form

$$x_1:\alpha_1,...,x_m:\alpha_m,\underbrace{J_1,...,J_n}_{\text{permutable}}$$

<hr>

Judgements as types

$$judg=type$$
$$true(A)=proof(A)$$
$$I|J=(I)J$$
$$|_{x:\alpha}J=(x:\alpha)J$$

With a proof of $J$ by means of the proof rules above, we can associate an object

$${\scriptsize\text{proof object}\longrightarrow}\underbrace{c\;:\;\underbrace{J}_{\small\text{synthetic judgement}}}_{\small\text{analytic judgement}}$$

<hr>

Generalized logical operations

$$\frac{\begin{matrix}
&&(A\;true)\\
A\;prop&&B\;prop
\end{matrix}}{\begin{array}{l}
A\supset B\;prop\\
\phantom{A}\,\&
\end{array}}$$

The ordinary implication and conjunction are easy enough to type

$$\begin{array}{ccc}
\supset&:&(prop)(prop)prop\\
\&&:&-\;\,"\;-
\end{array}$$

but how do we type the generalized implication and conjunction?

Type formation

$$\frac{\begin{matrix}
&&(I)\\
I:judg&&\beta:type
\end{matrix}}{I|\beta:type}$$

<hr>

$$\begin{array}{ccl}
\supset&:&(X:prop)(X|prop)prop\\
\&&:&\phantom{(X:prop)(}X\;true\\
&&\phantom{(X:prop)(}true(X)
\end{array}$$

Object formation

$$\frac{\begin{matrix}
(I)\\
b:\beta
\end{matrix}}{b:I|\beta}
\quad\quad
\frac{b:I|\beta\quad I}{b:\beta}$$

$$\frac{
\begin{matrix}\\A:prop\end{matrix}
\quad
\frac{\displaystyle\begin{matrix}
(A\;true)\\
B:prop
\end{matrix}}{\displaystyle B:A\;true|prop}
}{\begin{array}{l}
A\supset B:prop\\
\phantom{A}\;\&
\end{array}}$$