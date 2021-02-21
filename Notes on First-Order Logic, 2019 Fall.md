# First-Order Logic, 2019 Fall

<!-- @import "[TOC]" {cmd="toc" depthFrom=2 depthTo=3 orderedList=false} -->

<!-- code_chunk_output -->

- [First-Order Logic, 2019 Fall](#first-order-logic-2019-fall)
  - [Week 1-2](#week-1-2)
  - [Week 3](#week-3)
  - [Week 5](#week-5)
  - [Week 6](#week-6)
  - [Week 7](#week-7)
  - [Week 8](#week-8)
  - [Week 9](#week-9)

<!-- /code_chunk_output -->



## Week 1-2

* Formal Language
* Meta & Obeject Language
* Truth Value
* Semantics of Propositional Logic

---

> Lewis实质蕴涵，与自然语言中“如果...那么”的区别

**Semantics:**

* 赋值：$V(p)=1$
* 赋值满足：$V\vDash \phi$
* 语义后承：$\Sigma \Vdash \phi$ 

------

**Theorem 1**  对任意公式$\phi$: $\varnothing\Vdash\phi$ iff $\phi$是有效的。

**Theorem 2** $\{\sigma_1,\cdots,\sigma_{n}\}\Vdash \phi$ iff $(\sigma_1\rightarrow(\sigma_2\rightarrow \cdots \rightarrow (\sigma_{n}\rightarrow \phi)\cdots))$是有效的。 

------

> Formal Proof
Math Proof &emsp; &emsp; &emsp; &emsp; &emsp; &emsp; Math Objects 

-----

## Week 3

* Truth Assignment Function Theory - Semantics
* Calculus - Syntax

-----

- *semantically equivalent*: 若$\phi\vDash\alpha$且$\alpha\vDash\phi$，记为$\phi\dashv\vdash\alpha$.
- 二元逻辑n元真值函数个数：$2^{2^{n}}$，以此类推，m元逻辑n元真值函数个数：$m^{m^{n}}$.

-----

**Literal(字节):**
- prop & neg prop;
- $\bot,\neg \bot$

**CNF** (Conjunctive Normal Form) & **DNF** (Disjunctive Normal Form)

**Notation**|
-|
$\bigvee\Sigma,~\bigwedge\Phi$ |   
$\bigvee\{\alpha\}:=\alpha$ |  
$\bigwedge \varnothing:=\neg\bot$ |  
$\bigvee\varnothing:=\bot$ | 

------

**$\alpha$ realizes $g$:** 
- $g$: n-ary truth function with arguments $x_1,\cdots, x_{n}$;
- $A=\{P_1,\cdots,P_{n}\}$;
- wff $\alpha$ with $\Phi(\alpha)=A$.

If for every $(z_1,\cdots,z_{n})\in\{0,1\}^{n}$, we have $g(z_1,\cdots,z_{n})=1$ iff $\{P_{i}\in A~|~z_{i}=1\}\models \alpha$.

<u>**Note**:</u> 也可用$\lambda$表达式来写真值函数


>Some conclusions about *realization*:
>1. If $\alpha,\beta$ are realized by the same $g$, then $\alpha\dashv\vdash\beta$;
>2. Every truth function $g$ can be realized by a wff in DNF.

*Proof of 1*:
Suppose a truth valuation $U$, note: 
$$
y_{i}^{u}=
\begin{cases}
1,\quad &P_{i}\in U\\
0,\quad &P_{i}\notin U
\end{cases}
$$

$V\models\alpha$ iff $V\cap A\models\alpha$ iff $\{P_{i}\in A~| ~y_{i}^{v}=1\}\models\alpha$ iff $g(y^{v}_1,\cdots,y^{v}_{n})=1$.

*Proof of 2*:
1. $g=0$, let $\alpha$ be $\bot\wedge P_1\wedge \cdots \wedge P_{n}$;
2. $g\neq 0$, then there exists a non-empty set $S\subseteq\{0,1\}^{n}$ s.t. for every $y_1,\cdots, y_{n}\in\{0,1\}, (y_1,\cdots, y_{n})\in S$ iff $g(y_1,\cdots, y_{n})=1$. Obviously $S$ is finite.
Enumerate $S$ as $\{(x_{11},\cdots,x_{1n}),\cdots,(x_{k1},\cdots x_{kn})\}$, let $\alpha := \gamma_1\vee\cdots\vee\gamma_{k}$, $\gamma_{k}:=\beta_{i1}\wedge\cdots\wedge\beta_{in}$.
$$
\beta_{ij}=
\begin{cases}
P_{j},\quad &x_{ij}=1\\
\neg P_{j},\quad &x_{ij}=0
\end{cases}
$$
Then it is sufficient to check $\alpha$ realizes $g$.
Note $A=\{P_1,\cdots P_{n}\}, s=(y_1,\cdots, y_{n})\in\{0,1\}^{n}$, let $V_{s}=\{P_{h}\in A~|~y_{h}=1\}$.

    $(\Rightarrow)$: Suppose $g(s)=1$, then $s\in S$, $s=(y_1,\cdots, y_{n})=(x_{i1},\cdots,x_{in})$.
    For any $j\in\{1,\cdots,n\}$: 
        Case 1. $x_{ij}=1$, then $y_{j}=1$, so $P_{j}\in V_{s}$, then $V_{s}\models \beta_{ij}$;
        Case 2. $x_{ij}=0$, then also $V_{s}\models \beta_{ij}$.
    In both cases, we have $V_{s}\models \beta_{ij}$. For $j$ is coincident, then $V_{s}\models\gamma_{j}$, which makes $V_{s} \models \alpha$.
    $(\Leftarrow)$: Suppose $g(s)=0$, then $s \notin S$.
    For any $i\in\{1,\cdots,k\}$, there is a $j\in\{1,\cdots,n\}$ s.t. $x_{ij}\neq y_{j}$.
        Case 1. $x_{ij}=0, y_{j}=1$, then $P_{j}\in V_{s}$, so $V_{s}\nvDash \beta_{ij}$;
        Case 2. $x_{ij}=1,y_{j}=0$,then $P_{j}\notin V_{s}$, so $V_{s}\nvDash \beta_{ij}$.
    In both cases, we have $V_{s}\nvDash \beta_{ij}$, then $V_{s}\nvDash \gamma_{i}$. For $i$ is coincident, then $V_{s} \nvDash \alpha$.

-------

**Calculus:**
- 归结演算
- Hilbert 演算

Define a type. **(Backus-Naur Form)**
$\phi:=\bot~|~p~|~\phi\rightarrow\phi$.

**Classical Propositional Calculus**(3 Axioms Schemes and MP Rule):
1. $\alpha\rightarrow(\beta\rightarrow\alpha)$;
2. $(\alpha\rightarrow(\beta\rightarrow\gamma))\rightarrow((\alpha\rightarrow\beta)\rightarrow(\alpha\rightarrow\gamma))$;
3. $((\beta\rightarrow\bot)\rightarrow(\alpha\rightarrow\bot))\rightarrow(\alpha\rightarrow\beta)$;
4. If $\alpha\rightarrow\beta, \alpha$, then $\beta$.

<u>**Notation.**</u> $~~\vdash \alpha$ means $\alpha$ is *provable* or *have a proof*. 
Call $\alpha$ an *inner theorem*.

<u>_Example._</u>
Abbrev. write $\phi\rightarrow\phi$ as $(\phi\phi)$
Prove: $\vdash \phi\rightarrow \phi$
1. $\vdash (\phi(\phi\phi)\phi)((\phi(\phi\phi))(\phi\phi))$
2. $\vdash (\phi(\phi\phi)\phi)$
3. $\vdash (\phi(\phi\phi))(\phi\phi)$
4. $\vdash \phi(\phi\phi)$
5. $\vdash \phi\phi$

## Week 5

- Derivation
- Deduction Theorem
- Lindenbaum Lemma

-------

<u>**Derivation:**</u>  a finite tree of formulas from $\Gamma$ to $\phi$, each leaf is either an axiom or a wff in $\Gamma$; each node is from the earlier nodes by the application of MP.

- $\Sigma\vdash\phi$, $\vdash \phi$;
- If $\Gamma\vdash\phi$, then $\phi$ is called a *syntactical consequence* of $\Gamma$

------

>**Deduction Theorem**
Suppose $\alpha,\beta,\Sigma$, then $\Sigma\vdash\alpha\rightarrow\beta$ iff $\Sigma\cup\{\alpha\}\vdash\beta$.

*Proof:* Omitted.

------

**Consistent Set:**
$\Sigma$ is said to be consistent, if $\Sigma\nvdash\bot$.

Two Consequences:
- for any $\alpha$, $\{\alpha,\neg\alpha\}$ is not consistent;
- $\Sigma$ is consistent iff $\Sigma\nvdash\alpha$ for some $\alpha$.

*Proof:* 
($\Rightarrow$): By definition;
($\Leftarrow$): Suppose $\Sigma\vdash\bot$. 
For any arbitary $\alpha$, $\vdash((\alpha\rightarrow\bot)\rightarrow(\bot\rightarrow\bot))\rightarrow(\bot\rightarrow\alpha)$, since $\vdash(\bot\rightarrow\bot)$ and $\vdash(\bot\rightarrow\bot)\rightarrow((\alpha\rightarrow\bot)\rightarrow(\bot\rightarrow\bot))$.
Then by an application of MP, we have $\vdash\bot\rightarrow\alpha$.
Since $\Sigma\vdash\bot\rightarrow\alpha$ and $\Sigma\vdash\bot$, by MP, we have $\Sigma\vdash\alpha$.

**Maximal Consistent Set (MCS):**
If $\Sigma\nvdash\bot$, and for every $\Delta\supsetneq\Sigma$, we have $\Delta\vdash\bot$, then $\Sigma$ is said to be a MCS.

<u>**Lindenbaum Lemma**</u>(in a countable language):
If $\Sigma\nvdash\bot$, then there is a MCS $\Delta\supseteq\Sigma$.

Claims about $\Delta$:
1. $\Sigma\subseteq\Delta$;
2. For every $i\in\mathcal{N}$, $\Gamma_{i}\subseteq\Gamma_{i+1}$;
3. For every $i\in\mathcal{N}$, $\Gamma_{i}\nvdash\bot$;
4. $\Delta\nvdash\bot$;
5. For every $\phi$, either $\phi\in\Delta$ or $\phi\rightarrow\bot\in\Delta$;
6. For every $\phi$, $\phi\in\Delta$ iff $\Delta\vdash\phi$;
7. $\Delta$ is a MCS.

## Week 6

- Completeness: for a definite propositional calculus
- Modal Logic
- Intuitionistic Logic

-----

![modal cube](https://www.researchgate.net/profile/Christoph_Benzmueller/publication/280630807/figure/fig1/AS:284592901771264@1444863643131/The-modal-logic-cube-reasoning-in-modal-logics-is-commonly-done-with-respect-to-a.png "Modal Logic Cube by Christoph Benzmüller")

## Week 7

- Complements on IPC
- Natural Deduction
- FOL Language

-----

**Symbols:**
- quantifiers: $\forall,\exists$;
- equality symbol: $=$;
- predicate symbol: $P,R,\cdots$;
- individual variables: $v,x,y,\cdots$;
- constants: $a,b,c,\cdots$;
- function symbol: $f,g,\cdots$;
- prop connectives;
- (,)

**Term:**
$$t::=c|x|f^{(n)}\underbrace{t\cdots t}_{n}$$

**Wff:**
$$\phi::=~\equiv tt|P^{(n)}\underbrace{t\cdots t}_{n}|\bot|\phi\rightarrow\phi|\forall x\phi$$

*Polish Notation:*(An Example)
$\forall u\rightarrow \exists y\in u\exists x\wedge\in xu\forall z\rightarrow\in zx\neg\in zu$

**<u>Some Concepts:</u>**
- ground term;
- binding force;
- range;
- free/bound occurrences of variables:
  - a variable is bounded/free in $\alpha$ if x has a bounded/free occurrence in $\alpha$.
  - $\mathcal{BV}(\alpha),\mathcal{FV}(\alpha)$;
  - $\mathcal{FV}(\alpha)=\emptyset$, $\alpha$ is called a **sentence** or a **closed formula**.

-----

**Substitution:**
1. Term: $S^{x}_{t}$

$$
\begin{cases}
  c^{x}_{t}:=c;\\
  x^{x}_{t}:=t;\\
  y^{x}_{t}:=y;\\
  f^{(n)}t_1\cdots t_{n}=f^{(n)}(t_1)^{x}_{t}\cdots(t_n)^{x}_{t}.
\end{cases}
$$

2. Formula: $\phi^x_t$

$$
\begin{cases}
  (\equiv s_1s_2)^{x}_{t}:=\equiv(s_1)^x_t(s_2)^x_t;\\
  P^{(n)}s_1\cdots s_n:=P^{(n)}(s_1)^x_t\cdots (s_n)^{x}_{t}\\
  (\bot)^{x}_{t}:=\bot;\\
  (\rightarrow\alpha\beta)^{x}_{t}:=\rightarrow(\alpha)_t^x(\beta)^x_t;\\
  (\forall x\alpha)^{x}_{t}:=\forall x\alpha;\\
  (\forall y\alpha)^x_t:=\forall y(\alpha)^x_t.  
\end{cases}
$$


## Week 8

- Model(Structure) in FOL
- Vlidity
  
------

Define **a FOL model** $\mathfrak{A}=(|\mathfrak{A}|,(\cdot)^{\mathfrak{A}})$, in which:
+ $|\mathfrak{A}|\neq\emptyset$;
+ $(\cdot)^{\mathfrak{A}}$

**Interpretation:**
- For every $c\in {\rm CON}$: $c^{\mathfrak{A}}\in|\mathfrak{A}|$;
- For every $f\in {\rm Fct}^{(n)}$: $f^{\mathfrak{A}}:|\mathfrak{A}|^{n}\rightarrow |\mathfrak{A}|$, which must be a total function;
- For every $P\in {\rm Pre}^{(n)}: P^{\mathfrak{A}}\subseteq |\mathfrak{A}|^{\textit{n}}$.

**Assignment(on a model):**
Define an assignment $s: \rm Var\rightarrow |\mathfrak{A}|$, by which we have: $(\cdot)^{\mathfrak{A}}_{s}: {\rm Tm}\rightarrow |\mathfrak{A}|$. Specifically:
+ $c^{\mathfrak{A}}_{s}:= c^{\mathfrak{A}}$;
+ $x^{\mathfrak{A}}_{s}:= s(x)$;
+ $f(t_1\cdots t_{n})^{\mathfrak{A}}_{s}:=f^{\mathfrak{A}}((t_1)_{s}^{\mathfrak{A}},\cdots,(t_1)_{s}^{\mathfrak{A}})$.

**Revision on an assignment:**
For any assignment $s$ on $\mathfrak{A}$, $x\in {\rm Var}$, $d\in |\mathfrak{A}|$, define a revision on an assignment $s(x|d): {\rm Var}\rightarrow |\mathfrak{A}|$:
$$
s(x|d)(y)=
\begin{cases}
    d & x=y;\\
    s(y) & x\neq y.
\end{cases}
$$

*Some concepts:*

- Valid;
- Satisfiable;
- Semantical Consequence: e.g. $\Theta\Vdash\phi$.

Say $\mathfrak{A}$ and $s$ satisfies a formula $\phi$, write $\vDash_{\mathfrak{A}}\phi[s]$, if at least one of the following holds:
1. $\phi$ is of the form $t_1=t_2$, and $(t_1)^{\mathfrak{A}}_{s}=(t_2)^{\mathfrak{A}}_{s}$;
2. $\phi$ is of the form $Pt_1\cdots t_{n}$, and $\langle(t_1)^{\mathfrak{A}}_{s},\cdots,(t_{n})^{\mathfrak{A}}_{s}\rangle\in P^{\mathfrak{A}}$;
3. $\phi$ is of the form $\alpha\rightarrow\beta$, and ``$\nvDash_{\mathfrak{A}}\alpha[s]$ or $\vDash_{\mathfrak{A}}\beta[s]$" holds;
4. $\phi$ is of the form $\forall x\alpha$, and for every $d\in|\mathfrak{A}|$, $\vDash_{\mathfrak{A}}\alpha[s(x|d)]$.

Note that $\exist$ is defined as $\neg\forall\neg$ since:
$$\forall x\alpha\rightarrow\neg\exists x\neg\alpha$$ is valid.

-----

**<u>Remark:</u>** Suppose $\sigma$ a **closed-formula**, if $\vDash_{\mathfrak{A}}\sigma[s]$, then $\vDash_{\mathfrak{A}}\sigma$, which means the satisfiction has nothing to do with the choice of assignment on the model. We just say $\mathfrak{A}$ is a **model** of $\sigma$.

**<u>Notation:</u>** Define the set of free variables in a formula as $\mathcal{FV}$, say $\mathcal{FV}(\phi)=\{x_1,\cdots,x_{n}\}$, then that $\phi$ is satisfied under some assignment $s$ on $\mathfrak{A}$ just means <center>$\vDash_{\mathfrak{A}}\phi\llbracket s(x_1),\cdots,s(x_{n})\rrbracket$ </center> holds. 

-----

**Some Facts:**

<u>**Fact 1:**</u> 

For every $t\in {\rm Tm}$, every model $\mathfrak{M}$ and every assignment $s, s'$ on $\mathfrak{M}$: <center>If $s(x)=s'(x)$ holds for every $x\in \mathcal{Var}(t)$, then $t^{\mathfrak{A}}_{s}=t^{\mathfrak{A}}_{s}$.</center>

<u>**Fact 2:**</u> 

If $s(x)=s'(x)$ holds for every $x\in\mathcal{PV}(\phi)$, then $\vDash_{\mathfrak{A}}\phi[s]$ iff $\vDash_{\mathfrak{A}}\phi[s']$.

<u>**Fact 3:**</u>
$$(t_{t'}^{x})^{\mathfrak{A}}_{s}=(t)^{\mathfrak{A}}_{s(x|(t')^{\mathfrak{A}}_{s})}$$

## Week 9

**Definition:** Term $t$ is free(substituable) for variable $x$, if one of the following holds:
- $\phi$ is atomic;
- $x\notin\mathcal{FV}(\phi)$;
- $\phi$ is of $\alpha\rightarrow\beta$, $t$ is free for $x$ in both $\alpha$ and $\beta$;
- $\phi$ is $\forall y\alpha$, $y\notin\mathcal{Var}(t)$, and $t$ is free for $x$ in $\alpha$.

<u>**Fact 4 (Substitution Lemma):**</u>
If $t$ is free for $x$ in $\alpha$, then:
$$\vDash_{\mathfrak{A}}\alpha[s(x|t^{\mathfrak{A}}_s)]~~~~\text{iff}~~~~\vDash_{\mathfrak{A}}\alpha^{x}_{t}[s]$$.

*Proof:*
> 1. $\vDash_{\mathfrak{A}}t_1\equiv t_2[s(x|t^{\mathfrak{A}}_s)]$
> 2. $\vDash_{\mathfrak{A}}Q\overline{r}[s(x|t^{\mathfrak{A}}_s)]$
> 3. $\bot$, trivial;
> 4. $\vDash_{\mathfrak{A}}\beta\rightarrow\theta[s(x|t^{\mathfrak{A}}_s)]$;
> 5. $\vDash_{\mathfrak{A}}\forall x\beta[s(x|t^{\mathfrak{A}}_s)]$;
> 6. $y\notin\{x\}$, and $\vDash_{\mathfrak{A}}\forall y\beta[s(x|t^{\mathfrak{A}}_s)]$.

<u>**Fact 5:**</u>
If $t$ is free for $x$ in a wff $\alpha$, then $\forall x\alpha\rightarrow\alpha^x_t$ is valid.

------

**Definable Set:**
$\{<e_1,\cdots,e_n>\in|\mathfrak{A}|^n~|~\vDash_{\mathfrak{A}} \phi\llbracket e_1,\cdots,e_n\rrbracket\}$

*Examples:* $\mathfrak{A}=(\mathbb{N},<)$
- $[x<x]^{\mathfrak{A}}=\emptyset$
- $[\exists y(y<x)]^{\mathfrak{A}}=\{(a)|a\in\mathbb{N}\}$

Note that there are uncountable relations on $\mathbb{N}$, but only countable of them are definable.

**Homomorphism:**(P94)

<u>Remark:</u>
1. Replace $\Rightarrow$ in homo definition of relations with $\Leftrightarrow$, then $h$ is said to be a **Strong Homo**;
2. Let a strong homo $h$ be injective, then $h$ is said to be an **Embedding**;
3. Let an embedding $h$ be surjective, then $h$ is said to be an **Isomorphism**;
4. Let the range of an isomorphism $h$ be $|\mathfrak{A}|$, then $h$ is said to be an **Automorphism**;
5. **Self-embedding**.
