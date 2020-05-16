# Chapter 1: Sample Space and Probability
***
## <u>1.1 Sets</u>
- Set operations:
    - Distributive law:
        - $$S \cap (T \cup U) = (S \cap T) \cup (S \cap U)$$
        - $$S \cup (T \cap U) = (S \cup T) \cap (S \cup U)$$
    - De Morgan's laws:
        - $$(\bigcup_n S_n)^c = \bigcap_n S_n^c$$
        - $$(\bigcap_n S_n)^c = \bigcup_n S_n^c$$
***
## <u>1.2 Probabilistic Models</u>
### 1.2.1 Sample Space and Event
- Sample space ($S \ or \ \Omega$): the set of all possible outcomes of an experiment, 试验的所有可能结果
- Event ($A$): a subset of the sample space, 某些试验结果的集合
### 1.2.2 Choose Appropriate Sample Space
- 确定样本空间时，不同试验结果必须是**互斥**的（e.g. 试验为掷一枚骰子，不能同时把“1或3”以及“1或4”定义为一个结果）
### 1.2.3 Sequential Model
### 1.2.4 Axioms of Probability（非负性、可加性、归一性）
- **Probability Space** consists of $S$ and $P$, where $S$ is a sample space and $P$ is a function which takes an event $A \subseteq S$ as input, returns $P(A) \in [0,1]$ as output, such that: 
    - $$P(\varnothing) = 0,\ P(S) = 1$$
    - $$P(\bigcup_{n=1}^\infty A_n) = \sum_{n=1}^\infty P(An)$$ if $A_1, A_2, \dots, A_n$ are disjoint (non-overlapping)
- Intuition: 把样本空间中的试验结果看作质点，每个质点有一个质量。$P(A)$是质点集合的总质量，全空间的总质量为1。可加性公理：不相交的事件序列的总质量等于各个事件的质量之和。
### 1.2.5 Discrete Model
### 1.2.6 Continuous Model
- 单个点所组成的事件的概率为0
### 1.2.7 Properties of Probability
- $$P(A^c) = 1 - P(A)$$
- $$If \ A \subseteq B, \ then \ P(A) \leq P(B)$$
    <details>
    <summary>Proof</summary>

    $B = A \cup (A^c \cap B), \ P(B) = P(A) + P(A^c \cap B) \geq P(A)$
    </details>

- $$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$
    <details>
    <summary>Proof</summary>

    Proof: "Disjointification" $$\begin{array}{cc} P(A \cup B) = P(A \cup (A^c \cap B)) = P(A) + P(A^c \cap B) \\ \because P(A^c \cap B) + P(A \cap B) = P(B) \\ \therefore P(A \cup B) = P(A) + P(B) - P(A \cap B) \end{array}$$
    </details>

- $$P(A \cup B \cup C) = P(A) + P(B) + P(C) - P(A \cap B) - P(A \cap C) - P(B \cap C) + P(A \cap B \cap C)$$
- Inclusion - Exclusion: $$P(A_1 \cup A_2 \cup \dots \cup A_n) = \sum_{j=1}^n P(A_j) - \sum_{i<j}^n P(A_i \cap A_j) + \sum_{i<j<k}^n P(A_i \cap A_j \cap A_k) - \dots + (-1)^{n+1}P(A_1 \cap A_2 \cap \dots \cap A_n)$$
    <details>
    <summary>Example: DeMontmort's Problem (1713), matching problem</summary>

    n cards labeled $1,2,\dots,n$, let $A_j$ be the event "$j$th card matches"
    $$\begin{array}{cc} P(A_j) = \dfrac{(n-1)!}{n!} = \dfrac{1}{n}\\P(A_1 \cap A_2) = \dfrac{(n-2)!}{n!} = \dfrac{1}{n(n-1)}\\ \vdots \\P(A_1 \cap A_2 \cap \dots \cap A_k) = \dfrac{(n-k)!}{n!} \end{array}$$
    $$\begin{aligned} 
    P(\bigcup_{j=1}^n A_j) &= P(A_1 \cup A_2 \cup \dots \cup A_n) = n \cdot \dfrac{1}{n} - {n \choose 2} \cdot \dfrac{(n-2)!}{n!} + {n\choose 3} \cdot \dfrac{(n-3)!}{n!} - \dots + (-1)^{n+1} \cdot \dfrac{1}{n!} \\ 
    &= 1 - \dfrac{1}{2!} + \dfrac{1}{3!} - \dots + (-1)^{n+1} \cdot \dfrac{1}{n!} \stackrel{e^x=\sum_{n=0}^\infty \frac{1}{n!}x^n}{\approx} 1 - \dfrac{1}{e}
    \end{aligned}$$
    $$P(no\ match)=P(\bigcap_{j=1}^n A_j^c)=1-1+\dfrac{1}{2!}-\dfrac{1}{3!}+\dots+(-1)^n\dfrac{1}{n!} \approx \dfrac{1}{e}$$
    </details>

### 1.2.8 Model and Reality
- 贝特朗悖论：同一事件由于样本空间不同，有不同概率；解决实际问题时，必须明确样本空间，建立无歧义的概率模型
***
## <u>1.3 Conditional Probability</u>
"How should you update probability/beliefs/uncertainty based on new evidence?"
"Conditioning is the soul of statistics" - Blitzstein
- Definition: $$P(A|B)=\dfrac{P(A \cap B)}{P(B)},\ if P(B)>0$$
    - Intuition 1: pebble world
    e.g. 9 pebbles, total mass is 1
    $P(A|B)$: get rid of pebbles in $B^c$, renormalize to make total mass 1 again
    - Intuition 2: frequentist world
    repeat experiment many times, circle repititions where B occured, among those, what fraction of time did A also occur?
### 1.3.1 Conditional Probability Law
- 归一性：$P(S|B)=\dfrac{P(S \cap B)}{P(B)}=\dfrac{P(B)}{P(B)}=1$
- 可加性：if $A_1, A_2$ are disjoint
$$\begin{aligned}
P(A_1 \cup A_2|B) &= \dfrac{P((A_1 \cup A_2) \cap B))}{P(B)} 
\\ &= \dfrac{P((A_1 \cap B) \cup (A_2 \cap B))}{P(B)}
\\ &= \dfrac{P(A_1 \cap B)}{P(B)}+\dfrac{P(A_2 \cap B)}{P(B)}
\\ &= P(A_1|B)+P(A_2|B)
\end{aligned}$$
### 1.3.2 Conditional to Unconditional in Sequential Model
- $$P(A \cap B) = P(A|B)P(B)$$
- Multiplication Rule: $$P(\bigcap_{i=1}^n A_i) = P(A_1)P(A_2|A_1)P(A_3|A_1 \cap A_2) \cdots P(A_n|\bigcap_{i=1}^{n-1}A_i)$$
    <details>
    <summary>Monty Hall Problem</summary>

    1 door has car, 2 doors have goats, Monty knows which, he always opens a goat door if he has a choice, he picks with equal probability. Should you switch?
    P(success if switch|Monty opens door 2)$=\dfrac{\frac{1}{3}}{\frac{1}{3} \times \frac{1}{2} + \frac{1}{3}}=\dfrac{2}{3}$
    ```Mermaid    
    graph LR
        A(initial pick door 1) --1/3--> B(car door is 1)
        A(initial pick door 1) --1/3--> C(car door is 2)
        A(initial pick door 1) --1/3--> D(car door is 3)
        B(car door is 1) --1/2--> E(Monty opens door 2)
        B(car door is 1) --1/2--> F(Monty opens door 3)
        C(car door is 2) --1--> G(Monty opens door 3)
        D(car door is 3) --1--> H(Monty opens door 2)
        linkStyle 0 stroke:#ff0000,stroke-width:3px
        linkStyle 3 stroke:#ff0000,stroke-width:3px
        linkStyle 2 stroke:#ff0000,stroke-width:3px
        linkStyle 6 stroke:#ff0000,stroke-width:3px
    ```
    </details>

***
## <u>1.4 Total Probability Theorem & Bayes' Rule</u>
- **Total Probability Theorem:** 设$A_1, A_2, \dots A_n$是一组互不相容的事件，形成样本空间的一个分割（每一个试验结果必定使得其中一个事件发生）
$$\begin{aligned}
P(B) &= P(A_1 \cap B)+ \cdots + P(A_n \cap B)
\\ &= P(A_1)P(B|A_1) + \cdots + P(A_n)P(B|A_n)
\end{aligned}$$
任意事件$B$的概率等于事件$B$在$A_i$发生的情况下的条件概率的加权平均，权数等于事件$A_i$的无条件概率
- **Bayes' Rule:** 设$A_1, A_2, \dots A_n$是一组互不相容的事件，形成样本空间的一个分割
$$\begin{aligned}
P(A_i|B) &= \dfrac{P(A_i)P(B|A_i)}{P(B)}
\\ &= \dfrac{P(A_i)P(B|A_i)}{\sum_{i=1}^nP(A_i)P(B|A_i)}
\end{aligned}$$
    - Example: patient get tested for disease that afflicts 1% of population, suppose test is advertised as "95% accurate", find the probability that patient has disease given tests positive.
    Let D: patient has disease, T: patient tests positive
    $$P(D|T)=\dfrac{P(T|D)P(D)}{P(T)}=\dfrac{P(T|D)P(D)}{P(T|D)P(D)+P(T|D^c)P(D^c)}=\dfrac{0.95 \times 0.01}{0.95 \times 0.01 + 0.05 \times 0.99} \approx 0.16$$
    - "Biohazards"
        - Confusing P(A|B) with P(B|A), "prosecutor's fallacy", Sally Clark case
        - confusing P(A) "prior" with P(A|B) "posterior"
        - confusing independence with conditional independence
***
## <u>1.5 Independence</u>
- Events $A,B$ are **independent** if $$\begin{array}{cc} P(A\cap B)=P(A)P(B) \\ P(A|B)=P(A) \end{array}$$
若$A,B$相互独立，$A,B^c$也相互独立
### 1.5.1 Conditional Independence
- Events $A,B$ are **conditionally independent** given C if $$P(A \cap B|C)=P(A|C)P(B|C)$$
Also, 
$$\begin{array}{cc}
\begin{aligned}
P(A \cap B|C) &= \dfrac{P(A\cap B \cap C)}{P(C)}
\\ &=\dfrac{P(C)P(B|C)P(A|B\cap C)}{P(C)}
\\ &=P(B|C)P(A|B\cap C)
\end{aligned}
\\ \Longrightarrow P(A|B \cap C)=P(A|C),\ given\ P(B|C) \neq 0
\end{array}$$
**给定$C$发生的条件下，进一步假定$B$也发生，并不影响事件$A$的条件概率**
- **$A$和$B$两个事件相互独立并不蕴含条件独立，反之亦然：**
    - e.g. $A,B$相互独立，$C$满足条件$P(C)>0,P(A|C)>0,P(B/C)>0$，且$A\cap B\cap C=\varnothing$，由于$P(A\cap B|C)=0, P(A|C)P(B|C)>0$，$A,B$不可能条件独立
    $$\begin{array}{cc} H_1 = \{硬币第一次扔得正面\} \\ H_2 = \{硬币第二次扔得正面\} \\ D = \{两次扔得的结果不同\} \end{array}$$
### 1.5.2 Independence of a series of events
- $A_1,A_2, \dots, A_n$ is mutually independent if
$$P(\bigcap_{i \in S}A_i)=\prod_{i \in S}P(A_i) \ for\ any\ subset\ S\ of \{1,2,\dots ,n\}$$
    - e.g. Events $A_1,A_2,A_3$ are independent if
        - $P(A_1 \cap A_2) = P(A_1)P(A_2)$
        - $P(A_1 \cap A_3) = P(A_1)P(A_3)$
        - $P(A_2 \cap A_2) = P(A_2)P(A_3)$
        - $P(A_1 \cap A_2 \cap A_3) = P(A_1)P(A_2)P(A_3)$
        - 三个事件两两独立不包含三个事件独立
- Gambler's Ruin: 一个赌徒进行一系列相互独立的押注活动，每次押注以概率$p$赢一元，$q=1-p$输一元。开始押注时有$k$元，当自己输光或累计钱数为$n$元（对方输光）时，停止押注，问他累计钱数为$n$元（对方输光）的概率有多大？
Strategy: condiiton on the first step (first step analysis)
Let $A$ = {累计钱数为$n$元（对方输光）}，$w_k$ = P($A$ | 以$k$元开始押注)
$$\begin{array}{cc}
w_k \stackrel{LOTP}{=} pw_{k+1} + qw_{k-1}, \ 0<k<n, \ and\ 
\begin{cases}
w_0=0\\
w_n=1
\end{cases}
\\ Let\ r=q/p,\ w_{k+1}-w_k=r(w_k-w_{k-1})=r^k(w_1-w_0)=r^kw_1 \\ w_{k+1}=w_k+r^kw_1= w_{k-1}+r^{k-1}w_1+r^kw_1=w_1+rw_1+\cdots+r^kw_1 \\
w_k = 
\begin{cases}
\dfrac{1-r^k}{1-r}w_1 &, \ if\ p \neq q\\
kw_1 &, \ if\ p=q
\end{cases} \\
\because w_n=1,
w_1 = 
\begin{cases}
\dfrac{1-r}{1-r^n} &, \ if\ p \neq q\\
\dfrac{1}{n} &, \ if\ p=q
\end{cases} \\
\therefore
w_k = 
\begin{cases}
\dfrac{1-r^k}{1-r^n} &, \ if\ p \neq q\\
\dfrac{k}{n} &, \ if\ p=q
\end{cases}
\end{array}$$

### 1.5.4 Independent Experiment & Binomial Probability
- $$p(k) = {n \choose k}p^k(1-p)^{n-k}$$
- $$\sum_{k=0}^n{n \choose k}p^k(1-p)^{n-k}=1$$
    - when p = 1/2, 等同于$n$元素集合子集个数问题 $$\sum_{k=0}^n {n \choose k}=2^n$$
***
## <u>1.6 Counting</u>
### 1.6.1 Multiplication Rule
- If have experiment with $n_1$ possible outcomes, and for each outcome of 1st experiment, there are $n_2$ outcomes for 2nd experiment, $\dots$, for each there are $n_r$ outcomes for rth experiment, then:
$$n_1n_2 \cdots n_r = overall\ possible\ outcomes$$
    - e.g. $n$元素集合$\{s_1, s_2, \dots, s_n\}$的子集的个数$=2^n$
### 1.6.2 Permutation
### 1.6.3 Combination
- Sampling table: choose $k$ objects out of $n$

&nbsp; | order matters | order doesn't matter
- | - | - |
**replace** | $$n^k$$ | $${n+k-1 \choose k}$$ |
**don't replace** | $$\dfrac{n!}{(n-k)!}$$ | $${n \choose k}$$ |
 - Properties:
    - $${n \choose k} = {n \choose n-k}$$
    - $$n{n-1 \choose k-1} = k{n \choose k}$$
    pick $k$ people out of $n$, with 1 designated as "President":
    pick "President" and then pick the rest = pick k people and choose one to be "President"
    - Vandermonde's Identity: $${m+n \choose k}=\sum_{j=0}^k {m \choose j}{n \choose k-j}$$
### 1.6.4 Segmentation
- Multinomial Coefficient: 
$$\begin{aligned}
{n \choose n_1,n_2,\dots, n_r} &= {n \choose n_1}{n-n_1 \choose n_2} \cdots {n-n_1-\cdots n_{r-1} \choose n_r}
\\ &= \dfrac{n!}{n_1!n_2! \cdots n_r!}
\end{aligned}$$



# Chapter 2 Discrete Random Variables
***
## <u>2.1 Basic Concepts</u>
- A function from sample space $S$ to real line $\mathbb{R}$
***
## <u>2.2 Distributions</u>
Random Variable<br>$X$ | Definition | Probability Mass Function<br>$p_X(k),\ P(X=k)$ | Expectation<br>$E[X]=\sum_xxp_X(x)$ | Variance<br>$var(X)=E[X^2]-(E[X])^2$ | Moment Generating Function<br>$M_X(s)=E[e^{sX}]$ | Graph of PMF | Graph of CDF
- | - | - | - | - | - | - | -
**Discrete Uniform**<br>$X \sim Unif\{a,b\}$ | a finite number of values are equally likely to be observed<br>(e.g. dice) | $$p_X(k)= \begin{cases} \dfrac{1}{b-a+1} &, \ if\ k=a,a+1,\dots,b \\ 0 &, \ otherwise \end{cases}$$ | $$\dfrac{a+b}{2}$$ | $$\dfrac{(b-a)(b-a+2)}{12}$$ | $$M_X(s)=\dfrac{e^{as}}{b-a+1} \cdot \dfrac{e^{(b-a+1)s}-1}{e^s-1}$$ | <img src="https://s1.ax1x.com/2020/04/19/JKnbi8.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/04/19/JKnqJS.png" width = "300" />
**Bernoulli**<br>$X\sim Bern(p)$ | $X$ has only 2 possible value, 0 and 1 | $$p_X(k)= \begin{cases} p &, \ if\ k=1 \\ 1-p &, \ if\ k=0 \end{cases}$$ | $$p$$ | $$p(1-p)$$ | $$M_X(s)=1-p+pe^{s}$$ | <img src="https://s1.ax1x.com/2020/04/19/JKmxUK.png" width = "300" />
**Binomial**<br>$X\sim Bin(n,p)$ | $X$ is #successes in $n$ independent Bern(p) trials | $$p_X(k)= {n \choose k}p^k(1-p)^{n-k} ,\ k=0,1,\dots,n$$ | $$np$$ | $$np(1-p)$$ | $$M_X(s)=(1-p+pe^{s})^n$$ | <img src="https://s1.ax1x.com/2020/04/19/JKeb0P.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/04/19/JKmY1H.png" width = "300" />
**Multinomial**<br>$\vec{X} \sim Mult(n,\vec{p})$<br>$\vec{X} = (X_1,\dots,X_k)$<br>$\vec{p} = (p_1,\dots,p_k)$ | $n$ objects, independently putting into $k$ categories, $p_j$=P(category $j$), $X_j$ is #objects in category $j$ | Joint PMF: <br>$$P(X_1=n_1,\dots,X_k=n_k)=\dfrac{n!}{n_1! \cdots n_k!}p_1^{n_1} \cdots p_k^{n_k}$$ $$,\ for\ n_1+\cdots+n_k=n$$ | $$E[X_i]=np_i$$ | $$var(X_i)=np_i(1-p_i)$$ | $$M_X(\vec{s}) = \bigg( \sum_{i=1}^k p_i e^{s_i} \bigg)^n$$
**Hypergeometric**<br>$X \sim Hypergeo(w,b,n)$ | $X$ is #white balls in $n$ draws without replacement from a population of size $N=w+b$ that contains $w$ white balls and $b$ black balls | $$p_X(k) = \dfrac{{w \choose k}{b \choose n-k}}{w+b \choose n},\ 0 \leq k \leq w$$ | $$n\dfrac{w}{w+b}$$ | $$\dfrac{N-n}{N-1} n\dfrac{w}{N}\dfrac{b}{N}$$ |  | <img src="https://s1.ax1x.com/2020/04/19/JK1ydA.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/04/19/JK16II.png" width = "300" />
**Geometric**<br>$X\sim Geo(p)$ | indepedent Bern(p) trials, keep failing until suceed at the $k$th trial | $$p_X(k)= (1-p)^{k-1}p,\ k=1,2,\dots$$ | $$\dfrac{1}{p}$$ | $$\dfrac{1-p}{p^2}$$ | $$M_X(s)=\dfrac{pe^s}{1-(1-p)e^s}$$ | <img src="https://s1.ax1x.com/2020/04/19/JKKMBn.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/04/19/JKKQ7q.png" width = "300" />
**Poisson**<br>$X\sim Pois(\lambda)$ | Bin(n,p) converges to Pois($\lambda$) as $n\rightarrow \infty, p \rightarrow 0$ | $$p_X(k)= e^{-\lambda}\dfrac{\lambda^k}{k!},\ k=0,1,2,\dots$$ | $$\lambda$$ | $$\lambda$$ | $$M_X(s)=e^{\lambda(e^s-1)}$$ | <img src="https://s1.ax1x.com/2020/04/19/JKM98U.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/04/19/JKMC2F.png" width = "300" />
**Negative Binomial**<br>$X\sim NB(r,p)$ | $X$ is #failures before $r$th success | $$p_X(k)= {k+r-1 \choose k}p^k(1-p)^r ,\ k=0,1,\dots$$ | $$\dfrac{pr}{1-p}$$ | $$\dfrac{pr}{(1-p)^2}$$ | $$M_X(s) = \bigg( \dfrac{1-p}{1-pe^s} \bigg)^r$$ | <img src="https://s1.ax1x.com/2020/04/19/JKYe3t.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/04/19/JKYmgP.png" width = "300" />

<details>
<summary>Properties of Multinomial Distribution</summary>

(a) Its marginal distribution is Binomial: $$\vec{X} \sim Mult(n, \vec{p}),\ X_j \sim Mult(n, p_j)$$
(b) Lumping property: for example $$\vec{X}=(X_1, X_2, \dots, X_{10}) \sim Mult(n, (p_1, \dots, p_{10}))$$ $$Let\ \vec{Y}=(X_1, X_2, (X_3+\cdots+X_{10}))$$ $$Then,\ \vec{Y} \sim Mult(n, (p_1,p_2,(p_3+\cdots+p_{10})))$$
(c) Conditional joint distribution: for example $$\vec{X} \sim Mult(n, \vec{p}),\ and\ given\ X_1=n_1$$ $$(X_2,\dots,X_k) \sim Mult(n-n_1, (p_2',\dots,p_k'))$$ $$where\ p_j' = \dfrac{p_j}{p_2+\cdots+p_k}$$
</details>

<details>
<summary>Variance of Hypergeometric Distribution</summary>

$$X \sim Hypergeo(w,b,n),\ p=\dfrac{w}{w+b},\ N=w+b$$ $$\begin{aligned}
var(X) = var(\sum_{j=1}^n X_j) &= \sum_{j=1}^n var(X_j) + 2 \sum_{i < j} cov(X_i,X_j) \\
&= n var(X_1) + 2 {n \choose 2} cov(X_1,X_2) \\
&= n var(X_1) + 2 {n \choose 2} (E[X_1X_2]-E[X_1]E[X_2]) \\
&= np(1-p) + 2 \dfrac{n(n-1)}{2!} \bigg( \dfrac{w}{w+b}\dfrac{w-1}{w+b-1} - p^2 \bigg) \\
&= \underbrace{\dfrac{N-n}{N-1}}_{finite\ population\ correction} \underbrace{n \dfrac{w}{N} \dfrac{b}{N}}_{np(1-p)}
\end{aligned}$$
Extreme cases:
$(1)\ n=1,\ Hypergeo(w,b,1) \to Bern(p), var(X)=p(1-p)$
$(2)\ N\ much\ larger\ than\ n,\ \dfrac{N-n}{N-1} \to 1, Hypergeo(w,b,n) \to Bin(n,p),\ var(X) \approx np(1-p)$
</details>

<details>
<summary>Poisson Paradigm</summary>

Proof that Bin(n,p) converged to Pois($\lambda$) as $n\rightarrow \infty, p \rightarrow 0, constant\ \lambda = np\ (p=\dfrac{\lambda}{n})$:
$$\begin{aligned}
p_X(k) &= \dfrac{n!}{(n-k)!k!}p^k(1-p)^{n-k}
\\ &= \dfrac{n(n-1) \cdots (n-k+1)}{n^k} \cdot \dfrac{\lambda^k}{k!} \cdot (1-\dfrac{\lambda}{n})^{n-k}
\end{aligned}$$ $$Let\ k\ fixed,\ j=1,2,\dots,k,\ \because n \rightarrow \infty,\ \therefore \dfrac{n-k+j}{n} \rightarrow 1,\ (1-\dfrac{\lambda}{n})^{-k} \rightarrow 1,\ (1-\dfrac{\lambda}{n})^{n} \rightarrow e^{-\lambda}$$ $$p_X(k) \rightarrow e^{-\lambda} \dfrac{\lambda^k}{k!}$$
</details>

***
## <u>2.3 Functions of Random Variables</u>
- $$if\ Y=g(X),\ p_Y(y)=\sum_{\{x|g(x)=y\}} p_X(x)$$
***
## <u>2.4 Expectation, Mean, and Variance</u>
### 2.4.1 Variance, Moment and Law of the Unconscious Statistician(LOTUS)
- **LOTUS:** $$E[g(X)]=\sum_x g(x)p_X(x)$$
    <details>
    <summary>Proof</summary>

    $$\begin{array}{cc}
    Let\ Y=g(X), \\
    \begin{aligned}
    E[g(X)] = E[Y] &= \sum_{y} yp_Y(y) 
    \\ &= \sum_{y} (y \sum_{\{x|g(x)=y\}}p_X(x))
    \\ &= \sum_{y} \sum_{\{x|g(x)=y\}} yp_X(x)
    \\ &= \sum_{y} \sum_{\{x|g(x)=y\}} g(x)p_X(x)
    \\ &= \sum_x g(x)p_X(x)
    \end{aligned}
    \end{array}$$
    </details>

- Moment: $$n^{th} \ moment = E[X^n] = \sum_{x}x^np_X(x)$$
- Variance: $$var(X)=E[(X-E[X])^2] = \sum_{x}(x-E[X])^2p_X(x)$$
### 2.4.2 Properties of Mean and Variance
- $$\begin{array}{cc} Let\ Y=aX+b, \\ E(Y)=aE(X)+b \\ var(Y)= a^2var(X) \end{array}$$
    <details>
    <summary>Proof</summary>

    $$E[Y]=\sum_{x}(ax+b)p_X(x)=a\sum_{x}xp_X(x)+b\sum_{x}p_X(x)=aE[X]+b$$
    $$\begin{aligned}
    var(Y) &= \sum_x (ax+b-E[ax+b])^2p_X(x)
    \\ &= \sum_x (ax+b-aE[X]-b)^2p_X(x)
    \\ &= \sum_x a^2(x-E[X])^2p_X(x)
    \\ &= a^2var(X)
    \end{aligned}$$
    </details>

- $$var(X)=E[X^2]-(E[X])^2$$
    <details>
    <summary>Proof</summary>

    $$\begin{aligned}
    var(X) &= \sum_x (x-E[X])^2p_X(x)
    \\ &= \sum_x (x^2 - 2xE[X] + (E[X])^2)p_X(x)
    \\ &= \sum_x x^2p_X(x) - 2E(X) \sum_x xp_X(x) + (E[X])^2 \sum_x p_X(x)
    \\ &= E[X^2] - 2(E[X])^2 + (E[X])^2
    \\ &= E[X^2] - (E[X])^2
    \end{aligned}$$
    </details>

- $$E[g(X)] \neq g(E[X]), unless\ g(X)\ is\ linear$$

***
## <u>2.5 Joint PMFs of Multiple Random Variables</u>
- Multiple random variables: 指在同一个试验结果下产生的多个随机变量，它们所涉及的样本空间和概率律是相同的
- Joint PMF: $$p_{X,Y}(x,y)=P(X=x,Y=y)$$
联合分布可确定任何由随机变量$X$和$Y$所刻画的事件的概率，例如$A$是某些$(x,y)$所形成的集合：
$$P((X,Y) \in A)=\sum_{(x,y)\in A}p_{X,Y}(x,y)$$
可利用联合分布计算$X$或$Y$的分布， $p_X(x),\ p_Y(y)$称为边缘分布 (marginal distribution)
$$p_X(x)=\sum_{y} p_{X,Y}(x,y),\ p_Y(y)=\sum_{x} p_{X,Y}(x,y)$$
### 2.5.1 Functions of Multiple Random Variables
- $$if\ Z=g(X,Y),\ p_Z(z) = \sum_{\{(x,y)|g(x,y)=z\}} p_{X,Y}(x,y)$$
- $$E[g(X,Y)]=\sum_{x} \sum_{y} g(x,y)p_{X,Y}(xy)$$
    - $$if\ g(X,Y)=aX+bY+c,\ E[aX+bY+c]=aE[X]+bE[Y]+c$$
### 2.5.2 More than Two Random Variables
- Joint PMF: $$p_{X,Y,Z}(x,y,z) = P(X=x, Y=y, Z=z)$$
- Marginal PMF: $$p_{X,Y}(x,y) = \sum_{z}p_{X,Y,Z}(x,y,z)$$ $$p_{X}(x) = \sum_{y} \sum_{z} p_{X,Y,Z}(x,y,z)$$
- Expectation of function of random variables: $$E[g(X,Y,Z)] = \sum_{x} \sum_{y} \sum_{z} g(x,y,z)p_{X,Y,Z}(x,y,z)$$
    - $$if\ g(X,Y,Z)=aX+bY+cZ+d,\ E[aX+bY+cZ+d]=aE[X]+bE[Y]+cE[Z]+d$$
***
## <u>2.6 Conditioning</u>
### 2.6.1 Given Some Event Occurred
- Conditional PMF of random variable $X$ given some event $A$ occurred: $$p_{X|A}(x)=P(X=x|A)=\dfrac{P(\{X=x\} \cap A)}{P(A)}$$
    - For different $x$, $\{X=x\} \cap A$ are disjoint events, their union is $A$: $$P(A)=\sum_{x}P(\{X=x\} \cap A)$$
    - $$\sum_{x} p_{X|A}(x) = 1$$
### 2.6.2 Given Value of Another Random Variable
- Conditional PMF of random variable $X$ given random variable $Y=y$: $$p_{X|Y}(x|y)=P(X=x|Y=y)=\dfrac{P(X=x,Y=y)}{P(Y=y)}=\dfrac{p_{X,Y}(x,y)}{p_Y(y)}$$
    - $$\sum_{x} p_{X|Y}(x|y) = 1$$
- Conditional PMF to Joint PMF: $$p_{X,Y} (x,y) = p_Y (y) p_{X|Y}(x|y)$$ $$p_{X,Y} (x,y) = p_X (x) p_{Y|X}(y|x)$$
- Conditional PMF to Marginal PMF: (Total Probability Theorem) $$p_X(x) = \sum_y p_{X,Y}(x,y) = \sum_y p_Y(y)p_{X|Y}(x|y)$$
- More than two random variables:
    - 设$A_1,\dots, A_n$是一组互不相容的事件，并且形成样本空间的一个分割：$$p_X(x)=\sum_{i=1}^nP(A_i)p_{X|A_i}(x)$$
    - 进一步假定事件$B$满足对一切$i$，$P(A_i \cap B)>0$：$$p_{X|B}(x)=\sum_{i=1}^nP(A_i|B)p_{X|A_i \cap B}(x)$$
### 2.6.3 Conditional Expectation
- Conditional expectation of random variable $X$ given some event $A$ occurred: $$E[X|A]=\sum_x xp_{X|A}(x)$$
    - $$for\ function\ g(X),\ E[g(X)|A]=\sum_x g(x)p_{X|A}(x)$$
    - 设$A_1,\dots, A_n$是一组互不相容的事件，并且形成样本空间的一个分割：$$E[X]=\sum_{i=1}^n P(A_i)E[X|A_i] \tag{1}$$
        <details>
        <summary>Proof</summary>
        
        $$\begin{aligned}
        E[X] &= \sum_xxp_X(x)
        \\ &= \sum_x x \sum_{i=1}^n P(A_i)p_{X|A_i}(x)
        \\ &= \sum_{i=1}^nP(A_i) \sum_x xp_{X|A_i}(x)
        \\ &= \sum_{i=1}^n P(A_i)E[X|A_i]
        \end{aligned}$$
        </details>

    - 进一步假定事件$B$满足对一切$i$，$P(A_i \cap B)>0$：$$E[X|B]=\sum_{i=1}^nP(A_i|B)E[X|A_i \cap B] \tag{2}$$
- Conditional expectation of random variable $X$ given random variable $Y=y$: $$E[X|Y=y]=\sum_x xp_{X|Y}(x|y)$$
    - $$E[X]=\sum_y p_Y(y)E[X|Y=y] \tag{3}$$
- Total Expectation Theorem: $(1),(2),(3)$ Unconditional expectation is the expectation of conditional expectations
    - Proof of expectation and variance of $X \sim Geo(p)$: 
    $$\begin{array}{cc}
    Let\ A_1 = \{X=1\} = \{succeed\ at\ 1st\ trail\},\ A_2 = \{X>1\} = \{fail\ at\ 1st\ trail\}, 
    \\ E[X|A_1]=1,\ E[X|A_2]=E[1+X]=1+E[X]
    \\ E[X]=P(A_1)E[X|A_1]+P(A_2)E[X|A_2]=p+(1-p)(1+E[X])
    \\ E[X]=\dfrac{1}{p}
    \end{array}$$ $$\begin{array}{cc} 
    E[X^2|A_1]=1,\ E[X^2|A_2]=E[(1+X)^2]=1+2E[X]+E[X^2]
    \\ E[X^2]=p+(1-p)(1+2E[X]+E[X^2])
    \\ E[X^2]=\dfrac{1+2(1-p)E[X]}{p}=\dfrac{2-p}{p^2}
    \\ var(X) = E[X^2]-(E[X])^2=\dfrac{2-p}{p^2}-\dfrac{1}{p^2}=\dfrac{1-p}{p^2}
    \end{array}$$

***
## <u>2.7 Independence</u>
### 2.7.1 Independence between Random Variable and Event
- Random variable $X$ is independent with event $A$: $$P(\{X=x\} \cap A)=P(X=x)P(A)=p_X(x)P(A) ,\ for\ all\ x$$ $$p_X(x)=p_{X|A}(x) ,\ for\ all\ x$$
### 2.7.2 Independence between Two Random Variables
- Random variable $X$ is independent with random variable $Y$: $$p_{X,Y}(x,y)=p_X(x)p_Y(y) ,\ for\ all\ x\ and\ y$$ $$p_X(x)=p_{X|Y}(x|y) ,\ for\ all\ x$$
- Random variable $X$ is conditionally independent with random variable $Y$ given event $A$ occurred: $$p_{X,Y|A}(x,y)=p_{X|A}(x)p_{Y|A}(y),\ for\ all\ x\ and\ y$$ $$p_{X|Y,A}(x|y)=p_{X|A}(x),\ for\ all\ x$$
- Expectation of product of independent random variables $XY$: $$E[XY]=E[X]E[Y]$$ $$E[g(X)h(Y)]=E[g(X)]E[h(Y)]$$
    <details>
    <summary>Proof</summary>

    $$\begin{aligned}
    E[XY] &= \sum_x \sum_y xyp_{X,Y}(x,y)
    \\ &= \sum_x \sum_y xyp_{X}(x)p_{Y}(y)
    \\ &= \sum_xxp_X(x)\sum_yyp_Y(y)
    \\ &= E[X]E[Y]
    \end{aligned}$$
    </details>

- Variance of sum of independent random variables $X+Y$: $$var(X+Y)=var(X)+var(Y)$$
    <details>
    <summary>Proof</summary>

    $\because var(X+c)=var(X)$
    Shift the random variables and let their expectations be 0 $\tilde{X}=X-E[X],\tilde{Y}=Y-E[Y]$
    $$\begin{aligned}
    var(X+Y) &= var(\tilde{X}+\tilde{Y})
    \\ &= E[(\tilde{X}+\tilde{Y})^2] - \underbrace{(E[\tilde{X}+\tilde{Y}])^2}_0
    \\ &= E[\tilde{X}^2+2\tilde{X}\tilde{Y}+\tilde{Y}^2]
    \\ &= E[\tilde{X}^2] + \underbrace{2E[\tilde{X}]E[\tilde{Y}]}_0 + E[\tilde{Y}^2]
    \\ &= var(\tilde{X}) + var(\tilde{Y})
    \\ &= var(X) + var(Y)
    \end{aligned}$$
    </details>

### 2.7.3 Independence among Multiple Random Variables
- Random variables $X,Y,Z$ are independent: $$p_{X,Y,Z}(x,y,z)=p_X(x)p_Y(y)p_Z(z) ,\ for\ all\ x,y,z$$
$f(X),g(Y),h(Z)$ are independent;
$g(X,Y),h(Z)$ are independent;
$g(X,Y),h(Y,Z)$ are usually not independent
### 2.7.4 Variance of Sum of Multiple Independent Variables
- $X_1, \dots ,X_n$ are independent random variables: $$var(X_1+\cdots +X_n) = var(X_1)+ \cdots + var(X_n)$$

# Chapter 3 General Random Variables
***
## <u>3.1 Continuous Random Variables</u>
Random Variable<br>$X$ | Definition | Probability Density Function<br>$f_X(x)$ | Cumulative Distribution Function<br>$F_X(x)$ | Expectation<br>$E[X]=\int_{-\infty}^{\infty} xf_X(x)dx$ | Variance<br>$var(X)=E[X^2]-(E[X])^2$ |  Moment Generating Function<br>$M_X(s)=E[e^{sX}]$ | Graph of PDF | Graph of CDF
- | - | - | - | - | - | - | - | - 
**Continuous Uniform**<br>$X\sim Unif(a,b)$ | An experiment where there is an arbitrary outcome that lies between certain bounds | $$f_X(x)= \begin{cases} \dfrac{1}{b-a} &, \ if\ a \leq x \leq b \\ 0 &, \ otherwise \end{cases}$$ | $$F_X(x)=\dfrac{x-a}{b-a}$$ | $$\dfrac{a+b}{2}$$ | $$\dfrac{(b-a)^2}{12}$$ | $$M_X(s)=\dfrac{1}{b-a} \cdot \dfrac{e^{sb}-e^{sa}}{s}$$ | <img src="https://s1.ax1x.com/2020/04/19/JKtVZF.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/04/19/JKtZa4.png" width = "300" />
**Beta**<br>$X\sim Beta(\alpha,\beta),\alpha>0,\beta>0$ | The conjugate prior probability distribution for $Bern$, $Bin$, $NB$, $Geo$ in Bayesian inference; a suitable model for the random behavior of percentages and proportions | $$f_X(x) = \dfrac{1}{B(\alpha,\beta)}x^{\alpha-1}(1-x)^{\beta-1},\ if\ 0 \leq x \leq 1$$ $$where\ B(\alpha,\beta) = \dfrac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}$$ |  | $$\dfrac{\alpha}{\alpha+\beta}$$ | $$\dfrac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}$$ |  | <img src="https://s1.ax1x.com/2020/05/03/JzagPK.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/05/03/Jza28O.md.png" width = "300" />
**Exponential**<br>$X\sim Exp(\lambda)$ | The time between events in a Poisson process (in which events occur continuously and independently at a constant average rate) | $$f_X(x)= \lambda e^{-\lambda x} , \ if\ x \geq 0$$ | $$F_X(x)=1-e^{-\lambda x}$$ | $$\dfrac{1}{\lambda}$$ | $$\dfrac{1}{\lambda^2}$$ | $$M_X(s)=\dfrac{\lambda}{\lambda-s},\ s<\lambda$$ | <img src="https://s1.ax1x.com/2020/04/19/JKNU7F.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/04/19/JKNdk4.png" width = "300" />
**Laplace**<br>$Z \sim Laplace(0, \lambda^{-1})$ | $Z=X-Y$, where $X,Y \stackrel{i.i.d.}{\sim} Exp(\lambda)$ | $$f_Z(z) = \dfrac{\lambda}{2} e^{-\lambda \lvert z \rvert}$$ | $$F_Z(z) = \begin{cases} 1- \dfrac{1}{2}e^{-\lambda z} &,\ z \geq 0 \\ \dfrac{1}{2}e^{\lambda z} &,\ z<0 \end{cases}$$ | $$0$$ | $$\dfrac{2}{\lambda^2}$$ |  | <img src="https://s1.ax1x.com/2020/05/07/YZDqxO.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/05/07/YZDOMD.png" width = "300" />
**Gamma**<br>$X \sim Gamma(k, \lambda)$ | $k$th arrival time in Poisson process, sum of i.i.d. $Exp(\lambda)$ | $$f_X(x) = \dfrac{1}{\Gamma(k)} (\lambda x)^k e^{-\lambda x} \dfrac{1}{x}$$ $$where\ \Gamma(k)=\int_0^{\infty} x^k e^{-x} \dfrac{dx}{x}$$ |  | $$\dfrac{k}{\lambda}$$ | $$\dfrac{k}{\lambda^2}$$ | $$M_X(s) = \dfrac{1}{\bigg( 1-\dfrac{s}{\lambda} \bigg)^k},\ s<\lambda$$ | <img src="https://s1.ax1x.com/2020/05/03/JzRWkD.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/05/03/JzRfte.md.png" width = "300" />
**Normal**<br>$X\sim N(\mu,\sigma)$ | The sum of a large number of independent and identically distributed r.v.'s has an approximately normal CDF | $$f_X(x)=\dfrac{1}{\sigma \sqrt{2\pi}}e^{\frac{-(x-\mu)^2}{2\sigma^2}}$$ | $$F_X(x)=\dfrac{1}{\sigma \sqrt{2\pi}} \int_{-\infty}^x e^{\frac{-(t-\mu)^2}{2\sigma^2}} dt$$ | $$\mu$$ | $$\sigma^2$$ | $$M_X(s)=e^{(\sigma^2s^2/2)+\mu s}$$ | <img src="https://s1.ax1x.com/2020/04/19/JKNbB8.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/04/19/JKNqHS.png" width = "300" />
**Standard Normal**<br>$Z\sim N(0,1)$ | $$Z=\dfrac{X-\mu}{\sigma}$$ | $$f_Z(z)=\dfrac{1}{\sqrt{2\pi}}e^{-z^2/2}$$ | $$\Phi(x)=\dfrac{1}{\sqrt{2\pi}} \int_{-\infty}^x e^{-t^2/2} dt$$ | $$0$$ | $$1$$ | $$M_X(s)=e^{s^2/2}$$
**Cauchy**<br>$T \sim Cauchy(0,1)$ | $T=\dfrac{Z_1}{Z_2}$, where $Z_1,Z_2 \stackrel{i.i.d.}{\sim} N(0,1)$ | $$f_T(t) = \dfrac{1}{\pi(1+t^2)}$$ | $$F_T(t) = \dfrac{1}{\pi} \arctan(t) + \dfrac{1}{2}$$ | undefined | undefined | does not exist | <img src="https://s1.ax1x.com/2020/05/07/YZ03sH.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/05/07/YZ08Ld.png" width = "300" />
**Chi-Squared**<br>$V \sim \chi^2(k)$ | $V=\sum\limits_{i=1}^k Z_i^2$, where $Z_i \stackrel{i.i.d.}{\sim} N(0,1)$, $\chi^2(k)$ is $Gamma(\dfrac{k}{2},\dfrac{1}{2})$ | $$f_V(v) = \dfrac{1}{2^{k/2}\Gamma(k/2)} v^{k/2} e^{-v/2} \dfrac{1}{v}$$ |  | $$k$$ | $$2k$$ |  | <img src="https://s1.ax1x.com/2020/05/07/YZcV10.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/05/07/YZcZcV.png" width = "300" />
**Student's $t$**<br> | $T_n=\dfrac{Z}{\sqrt{V/n}}$, where $Z \sim N(0,1),V \sim \chi^2(n)$ | $$f_{T_n}(t) = \dfrac{\Gamma(\frac{n+1}{2})}{\sqrt{n\pi}\Gamma(\frac{n}{2})}(1+\dfrac{t^2}{n})^{-\frac{n+1}{2}}$$ | | $$\begin{cases} 0 &,\ n>1 \\ undefined &,\ otherwise \end{cases}$$ | $$\begin{cases} \dfrac{n}{n-2} &,\ n>2 \\ \infty &,\ 1 < n \leq 2 \\ undefined &,\ otherwise \end{cases}$$ | undefined | <img src="https://s1.ax1x.com/2020/05/14/YBMlAP.png" width = "300" /> | <img src="https://s1.ax1x.com/2020/05/14/YBM1tf.png" width = "300" />

- CDFs of geometric and exponential r.v.'s:
$$X \sim Geo(p):\ F_{geo}(n)=\sum_{k=1}^n(1-p)^{k-1}p=p \cdot \dfrac{1-(1-p)^n}{1-(1-p)}=1-(1-p)^n,\ n=1,2,\dots$$  $$X \sim Exp(\lambda):\ F_{exp}(x)=\int_0^x \lambda e^{-\lambda t}dt=-e^{-\lambda t} \big|_0^x = 1-e^{-\lambda x},\ x>0$$
$$Let\ \delta=-\dfrac{\ln(1-p)}{\lambda},\ so\ that\ \pmb{e^{-\lambda \delta}=1-p}$$ $$\Longrightarrow F_{exp}(n\delta)=F_{geo}(n),\ when\ n=1,2,\dots$$
<div align="center">
<img src="https://s1.ax1x.com/2020/04/13/GjAWkt.md.png" width = "500" />
</div>


***
## <u>3.2 Cumulative Distribution Functions (CDF)</u>
- $$F_X(x) = P(X \leq x) = \begin{cases} \sum_{k \leq x}p_X(k) &,\ if\ X\ is\ discrete \\ \int_{-\infty}^x f_X(t)dt &,\ if\ X\ is\ continuous \end{cases}$$
- If $X$ is discrete and integer:
    - $$F_X(k) = \sum_{i=-\infty}^kp_X(i)$$
    - $$p_X(k) = P(X \leq k) - P(X \leq k-1) = F_X(k) - F_X(k-1)$$
- If $X$ is continuous:
    - $$f_X(x)=\dfrac{dF_X}{dx}(x)$$
***
## <u>3.3 Normal Random Variables</u>
***
## <u>3.4 Joint PDFs of Multiple Random Variables</u>
- Joint PDF: nonnegative function $f_{X,Y}(x,y)$ satisfies
$$P((X,Y)\in B)=\iint\limits_{(x,y)\in B} f_{X,Y}(x,y) dxdy$$
    - $If\ B=\{(x,y)|a \leq x \leq b, c \leq y \leq d\},$ $$P(a \leq x \leq b, c \leq y \leq d)=\int_c^d \int_a^b f_{X,Y}(x,y)dxdy$$
    - Let $\delta$ be a small positive number and consider the probability of a small rectangle: $$P(a \leq X \leq a+\delta, c \leq Y \leq c+\delta)=\int_c^{c+\delta}\int_a^{a+\delta} f_{X,Y}(x,y)dxdy \approx f_{X,Y}(a,c)\delta^2$$ view $f_{X,Y}(a,c)$ as the "probability per unit area" in the  vicinity of $(a,c)$
- Marginal PDF:
$$f_X(x)=\int_{-\infty}^{\infty}f_{X,Y}(x,y)dy$$ $$f_Y(y)=\int_{-\infty}^{\infty}f_{X,Y}(x,y)dx$$
- Two-dimensional uniform PDF: uniform joint PDF on subset $S$ of the two-dimensional plane $$f_{X,Y}(x,y) = \begin{cases} \dfrac{1}{area\ of\ S} &,\ if\ (x,y)\in S \\ 0 &,\ otherwise \end{cases}$$ For any set $A \subset S$, the probability that $(X,Y)$ lies in $A$ is $$P((X,Y)\in A)=\iint\limits_{(x,y)\in A} f_{X,Y}(x,y)dxdy=\dfrac{1}{area\ of\ S}\int_{(X,Y)\in A} \int dxdy=\dfrac{area\ of\ A}{area\ of\ S}$$
### 3.4.1 Joint CDFs
- $$F_{X,Y}(x,y)=P(X\leq x,Y\leq y)=\int_{-\infty}^x \int_{-\infty}^y f(s,t)dtds$$
- $$f_{X,Y}(x,y)=\dfrac{\partial^2 F_{X,Y}}{\partial x \partial y}(x,y)$$
### 3.4.2 Expectation
- $If\ Z=g(X,Y),$ $$E[g(X,Y)]=\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} g(x,y)f_{X,Y}(x,y)dxdy$$
- $If\ Z=aX+bY+c,$ $$E[aX+bY+c]=aE[X]+bE[Y]+c$$
### 3.4.3 More than Two Random Variables
- Joint PDF: nonnegative function $f_{X,Y,Z}(x,y,z)$ satisfies
$$P((X,Y,Z)\in B)=\iiint\limits_{(x,y,z)\in B} f_{X,Y,Z}(x,y,z)dxdydz$$
- Marginal PDF: $$f_{X,Y}(x,y)=\int_{-\infty}^{\infty} f_{X,Y,Z}(x,y,z)dz$$ $$f_{X}(x)=\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f_{X,Y,Z}(x,y,z)dydz$$
***
## <u>3.5 Conditioning</u>
### 3.5.1 Conditioning a Random Variable on an Event
- $$f_{X|A}(x) = \begin{cases} \dfrac{f_X(x)}{P(X \in A)} &,\ if\ x \in A \\ 0 &,\ otherwise \end{cases}$$
- $$f_{X,Y|C}(x,y) = \begin{cases} \dfrac{f_{X,Y}(x,y)}{P(C)} &,\ if\ x,y \in A \\ 0 &,\ otherwise \end{cases}$$
    - $$f_{X|C}(x) = \int_{-\infty}^{\infty} f_{X,Y|C}(x,y)dy$$
- Total probability Theorem: $$f_X(x)=\sum_{i=1}^n P(A_i)f_{X|A_i}(x)$$
### 3.5.2 Conditioning one Random Variable on Another
- $$f_{X|Y}(x|y) = \dfrac{f_{X,Y}(x,y)}{f_Y(y)} \ if\ f_Y(y)>0$$
    - Think of value of $Y$ as fixed at some $y$
    shape of $f_{X|Y}(\cdot|y)$: slice of joint PDF $f_{X,Y}(x,y)$
    <img src="https://s1.ax1x.com/2020/04/13/GjAftP.md.png" width = "500" />
    - $$\int_{-\infty}^{\infty} f_{X|Y}(x|y)=\dfrac{\int_{-\infty}^{\infty} f_{X,Y}(x,y)}{f_Y(y)}=1,\ f_Y(y):scaling\ factor$$
- Intuitive way to understand conditional PDF:
    - Let $\delta,\epsilon$ be small positive numbers $$P(x \leq X \leq x+\delta|A) \approx f_{X|A}(x) \cdot \delta$$ $$P(x \leq X \leq x+\delta|y \leq Y \leq y+\epsilon) \approx \dfrac{f_{X,Y}(x,y)\cdot \delta \cdot \epsilon}{f_Y(y) \cdot \epsilon}=f_{X|Y}(x|y) \cdot \delta$$ $$when\ \epsilon \rightarrow 0,\ P(x \leq X \leq x+\delta|Y=y) \approx f_{X|Y}(x|y) \cdot \delta$$ $$more\ generally,\ P(X \in A|Y=y) = \int_A f_{X|Y}(x|y)dx$$
### 3.5.3 Conditional Expectation
- $$E[X|A]=\int_{-\infty}^{\infty} xf_{X|A}(x)dx$$ $$E[X|Y=y]=\int_{-\infty}^{\infty} xf_{X|Y}(x|y)dx$$
- Total Expectation Theorem: $$E[X]=\int_{-\infty}^{\infty} f_Y(y)E[X|Y=y]dy$$
### 3.5.4 Independence
- $X$ and $Y$ are independent if: 
    - $$f_{X,Y}(x,y) = f_X(x)f_Y(y),\ for\ all\ x,y$$
    - $$f_{X|Y}(x|y) = f_X(x),\ for\ all\ x\ and\ all\ y\ with\ f_Y(y)>0$$
    - $$F_{X,Y}(x,y) = F_X(x)F_Y(y),\ for\ all\ x,y$$
    - $$E[XY] = E[X]E[Y]$$
    - $$var(X+Y) = var(X)+var(Y)$$
***
## <u>3.6 The Continuous Bayes' Rule</u>
- $$f_{X|Y}(x|y) = \dfrac{f_X(x)f_{Y|X}(y|x)}{f_Y(y)}$$ $$f_{X|Y}(x|y) = \dfrac{f_X(x)f_{Y|X}(y|x)}{\int_{-\infty}^{\infty} f_X(t)f_{Y|X}(y|t)dt}$$
- $N$: discrete, $Y$: continuous $$P(N=n|Y=y) = p_{N|Y}(n|y) = \dfrac{p_N(n)f_{Y|N}(y|n)}{f_Y(y)} = \dfrac{p_N(n)f_{Y|N}(y|n)}{\sum\limits_{i} p_N(i)f_{Y|N}(y|i)}$$ $$P(Y=y|N=n) = f_{Y|N}(y|n) = \dfrac{f_Y(y)p_{N|Y}(n|y)}{p_N(n)} = \dfrac{f_Y(y)p_{N|Y}(n|y)}{\int f_Y(t)p_{N|Y}(n|t)dt}$$

# Chapter 4 Further Topics on Random Variables
***
## <u>4.1 Derived Distributions</u>
- Calculation of the PDF of $Y=g(X)$
    - Calculate the CDF $F_Y$ of $Y$: $$F_Y=P(Y \leq y)=P(g(X) \leq y)=\int_{\{x|g(x) \leq y\}} f_X(x)dx$$
    - Differentiate to obtain the PDF of $Y$: $$f_Y(y)=\dfrac{dF_Y}{dy}(y)$$
### 4.1.1 The Linear Case
- $$Let\ Y=aX+b,\ f_Y(y)=\dfrac{1}{|a|}f_X(\dfrac{y-b}{a})$$
### 4.1.2 The Monotonic Case
- Suppose that $g$ is **strictly monotonic** and for all $x$ in the range of $X$ we have $$y=g(x)\ if\ and\ only\ if\ x=g^{-1}(y)$$ Assume that $h$ is differentiable, then $$f_Y(y)=f_X(x)\bigg|\dfrac{dx}{dy}\bigg|$$

    <details>
    <summary>Example: derive Log Normal from Normal</summary>

    Let $Y=e^Z$, $Z \sim N(0,1)$, $Y=g(Z)$ is increasing and infinitely differentiable
    $$f_Y(y) = f_Z(z) \dfrac{dz}{dy} = \dfrac{1}{\sqrt{2\pi} y} e^{-(\ln{y})^2/2}$$
    </details>

- Derived distribution in $\mathbb{R}^n$: $\vec{Y} = g(\vec{X}),\ where\ \vec{X}=(X_1,\dots,X_n)$, the joint PDF of $\vec{Y}$ is $$f_{\vec{Y}}(\vec{y})=f_{\vec{X}}(\vec{x}) \bigg| \dfrac{d\vec{x}}{d\vec{y}} \bigg|$$ $$,\ where\ \bigg| \dfrac{d\vec{x}}{d\vec{y}} \bigg|\ is\ absolute\ value\ of\ determinant\ of\ Jacobian\ \dfrac{d\vec{x}}{d\vec{y}} = 
\left[
\begin{matrix}
\dfrac{\partial x_1}{\partial y_1} & \cdots & \dfrac{\partial x_1}{\partial y_n} \\
\vdots & \vdots & \vdots \\
\dfrac{\partial x_n}{\partial y_1} & \cdots & \dfrac{\partial x_n}{\partial y_n}
\end{matrix}
\right]$$
### 4.1.3 Multiple Random Variables
- Laplace (two-sided exponential) PDF:
Romeo and Juliet have a date at a given time, and each, independently, will be late by an amount of time that is exponentially distributed with parameter $\lambda$. What is the PDF of the difference between their times of arrival?
Let $X,Y$ be the amounts by which Romeo and Juliet are late. We want to find the PDF of $Z=X-Y$. We will first calculate the CDF $F_Z(z)$ by considering seperately the cases $z \geq 0$ and $z<0$.
[![GjA2TI.png](https://s1.ax1x.com/2020/04/13/GjA2TI.png)](https://imgchr.com/i/GjA2TI)
$$f_{X,Y}(x,y)=f_X(x)f_Y(y)=\lambda e^{-\lambda x} \lambda e^{-\lambda y},\ x,y \geq 0$$
    - For $z \geq 0$:
    $$\begin{aligned}
    F_Z(z) &= P(Z \leq z) = P(X-Y \leq z) = 1 - P(X-Y > z)
    \\ &= 1 - \int_0^{\infty} \int_{z+y}^{\infty} \lambda e^{-\lambda x} \lambda e^{-\lambda y} dxdy
    \\ &= 1 - \int_0^{\infty} \lambda e^{-\lambda y} \bigg[ -e^{-\lambda x}\bigg]_{z+y}^{\infty} dy
    \\ &= 1 - \int_0^{\infty} \lambda e^{-\lambda y} e^{-\lambda (z+y)} dy
    \\ &= 1 - e^{-\lambda z}\bigg[ -\dfrac{1}{2} e^{-2\lambda y} \bigg]_0^{\infty}
    \\ &= 1 - \dfrac{1}{2}e^{-\lambda z}
    \end{aligned}$$
    - For $z < 0$: by symmetry, $Z=X-Y$ and $-Z=Y-X$ have the same distribution
    $$\begin{aligned} F_Z(z) &= P(Z \leq z)=P(-Z \geq -z)=P(Z \geq -z)=1-F_Z(-z) \\ &= 1 - \bigg( 1-\dfrac{1}{2}e^{\lambda z} \bigg) = \dfrac{1}{2}e^{\lambda z} \end{aligned}$$
    - $$F_Z(z) = \begin{cases} 1- \dfrac{1}{2}e^{-\lambda z} &,\ z \geq 0 \\ \dfrac{1}{2}e^{\lambda z} &,\ z<0 \end{cases}$$
    - $$\Longrightarrow f_Z(z) = \begin{cases} \dfrac{\lambda}{2}e^{-\lambda z} &,\ z \geq 0 \\ \dfrac{\lambda}{2}e^{\lambda z} &,\ z<0 \end{cases}$$ $$\pmb{f_Z(z) = \dfrac{\lambda}{2}e^{-\lambda |z|}}$$
    **Can be solved by convolution(4.1.5) as well**

### 4.1.4 Simulation
- Universality of continuous uniform r.v.'s: 通过均匀分布构造服从分布$F$的随机变量
$$Let\ U \sim Unif(0,1),\ F\ is\ a\ CDF (strictly\ increasing\ and\ continuous)$$ $$Let\ X \triangleq F^{-1}(U),\ then\ X \sim F$$
### 4.1.5 Sum of Independent Random Variables - Convolution
$X,Y$ are independent r.v.'s, $Z=X+Y$
- Discrete convolution: $$p_Z(z) = \sum_x p_X(x)p_Y(z-x)$$
- Continuous convolution: $$f_Z(z) = \int_{-\infty}^{\infty} f_{X,Z}(x,z) dx = \int_{-\infty}^{\infty} f_X(x)f_Y(z-x) dx$$
    - Graphical Calculation of Convolution 
    [![Gj1cn0.png](https://s1.ax1x.com/2020/04/13/Gj1cn0.png)](https://imgchr.com/i/Gj1cn0)
- Sum of independent normal r.v.'s: $X \sim N(\mu_x,\sigma_x^2), Y \sim N(\mu_y,\sigma_y^2)$ $$\begin{aligned} f_Z(z) &= \int_{-\infty}^{\infty} \dfrac{1}{\sigma_x \sqrt{2\pi}} exp \bigg( -\dfrac{(x-\mu_x)^2}{2\sigma_x^2} \bigg) \dfrac{1}{\sigma_y \sqrt{2\pi}} exp \bigg( -\dfrac{(z-x-\mu_y)^2}{2\sigma_y^2} \bigg) dx \\ &= \dfrac{1}{\sqrt{2\pi(\sigma_x^2+\sigma_y^2)}} exp \bigg( -\dfrac{(z-\mu_x-\mu_y)^2}{2(\sigma_x^2+\sigma_y^2)} \bigg) \end{aligned}$$ $\Longrightarrow Z \sim N(\mu_x+\mu_y, \sigma_x^2+\sigma_y^2)$
**The sum of finitely many independent normal is normal**
***
## <u>4.2 Covariance and Correlation</u>
- Covariance: $$\begin{aligned} cov(X,Y) &= E[(X-E[X])(Y-E[Y])] \\ &= E[XY] - E[X]E[Y] \end{aligned}$$
    - Properties:
    $$cov(X,X)=var(X)$$ $$cov(X,aY+b)=a \cdot cov(X,Y)$$ $$cov(X,Y+Z)=cov(X,Y)+cov(X,Z)$$ $$cov(X,Y)=0 \Longrightarrow uncorrelated$$ $$if\ X,Y\ are\ independent,\ they\ are\ uncorrelated;\ The\ converse\ is\ not\ always\ true$$
- Correlation Coefficient: $$\begin{aligned} \rho(X,Y) &= E \bigg[ \dfrac{(X-E[X])}{\sigma_X} \cdot \dfrac{(Y-E[Y])}{\sigma_Y} \bigg] \\ &= \dfrac{cov(X,Y)}{\sigma_X \sigma_Y} \end{aligned}$$
    - $$-1 \leq \rho(X,Y) \leq 1$$
        <details>
        <summary>Proof</summary>

        Assume zero means and unit variances, so that $\rho(X,Y)=E[XY]$ $$\begin{aligned} E[(X - \rho Y)^2] &= E[X^2] - 2 \rho E[XY] + \rho^2 E[Y^2] \\ &= 1 - 2 \rho^2 + \rho^2 = 1 - \rho^2 \geq 0 \end{aligned}$$
        </details>
    - $$|\rho| = 1,\ if\ and\ only\ if\ Y-E[Y]=c(X-E[X])$$
    - $$\rho(aX+b,Y)=\dfrac{a \cdot cov(X,Y)}{|a| \cdot \sigma_X\sigma_Y}=sign(a) \cdot \rho(X,Y)$$
    - Correlation often reflects underlying, common, hidden factor
        <details>
        <summary>Example</summary>

        Example of $\rho=0.5$: assume $Z,V,W$ are independent, $X=Z+V,Y=Z+W$, assume $Z,V,W$ have zero means and unit variance
        $$var(X)=var(Z)+var(V)=2 \Longrightarrow \sigma_X=\sqrt{2}$$ $$similarly,\ \sigma_Y=\sqrt{2}$$ $$cov(X,Y)=E[(Z+V)(Z+W)]=E[Z^2]+E[ZW]+E[VZ]+E[VW]=1$$ $$\rho(X,Y)=\dfrac{1}{\sqrt{2}\sqrt{2}}=\dfrac{1}{2}$$
        </details>
- Variance of the sum of random variables: $$var(X_1+X_2) = var(X_1) + var(X_2) + cov(X_1,X_2)$$ $$var(\sum_{i=1}^n X_i) = \sum_{i=1}^n var(X_i) + \underbrace{\sum_{\{(i,j)|i \neq j\}} cov(X_i,X_j)}_{n(n-1)\ terms}$$
    <details>
    <summary>Proof</summary>

    $Let\ \tilde{X_i} = X_i - E[X_i], $ $$\begin{aligned} var(\sum_{i=1}^n X_i) &= E \bigg[ \bigg( \sum_{i=1}^n \tilde{X_i} \bigg)^2 \bigg] \\ &= E \bigg[ \sum_{i=1}^n \sum_{j=1}^n \tilde{X_i}\tilde{X_j} \bigg] \\ &= \sum_{i=1}^n \sum_{j=1}^n E[\tilde{X_i}\tilde{X_j}] \\ &= \sum_{i=1}^n E[\tilde{X_i}^2] + \sum_{\{(i,j)|i \neq j\}} E[\tilde{X_i}\tilde{X_j}] \\ &= \sum_{i=1}^n var(X_i) + \sum_{\{(i,j)|i \neq j\}} cov(X_i,X_j) \end{aligned}$$
    </details>

***
## <u>4.3 Conditional Expectation and Variance Reavisited</u>
- Conditional Expectation: $E[X|Y]=g(Y)$, $g(y)=E[X|Y=y]$
    - a function of $Y$
    - a random variable
    - has a distribution, mean, variance, etc.
- **Law of Iterated Expectations:** $$E[E[X|Y]]=E[X]$$
    <details>
    <summary>Proof</summary>

    $$E[E[X|Y]]=E[g(Y)]=\sum_y g(y)p_Y(y)=\sum_y E[X|Y=y]p_Y(y) \stackrel{Total\ Expectation\ Theorem}{=} E[X]$$
    </details>

### 4.3.1 Conditional Expectation as an Estimator
- If $Y$ is an observation that provides information about $X$, we view the conditional expectation as an estimator of $X$ given $Y$: $$\hat{X}=E[X|Y]$$
The estimation error: $$\tilde{X}=\hat{X} - X$$
is a random variable satisfying: $$E[\tilde{X}|Y]=E[\hat{X} - X|Y]=E[\hat{X}|Y]-E[X|Y]=\hat{X}-\hat{X}=0$$
By using the law of iterated expectation, it indicates that the estimation error does not have a systematic upward or downward bias: $$E[\tilde{X}]=E[E[\tilde{X}|Y]]=0$$
- The estimator $\hat{X}$ is uncorrelated with the estimated error $\tilde{X}$: $$E[\hat{X}\tilde{X}]=E[E[\hat{X}\tilde{X}|Y]]=E[\hat{X}E[\tilde{X}|Y]]=0$$ $$cov(\hat{X},\tilde{X})=E[\hat{X}\tilde{X}]-E[\hat{X}]E[\tilde{X}]=0$$
- $$var(X) = var(\hat{X}) + var(\tilde{X})$$
### 4.3.2 Conditional Variance
- $$var(X|Y)=E[(X-E[X|Y])^2|Y]=E[\tilde{X}^2|Y]$$
- $$var(\tilde{X})=E[\tilde{X}^2]-\underbrace{(E[\tilde{X}])^2}_0=E[E[\tilde{X}^2|Y]]=E[var(X|Y)]$$
- **Law of Total Variance:** $$\begin{aligned} var(X) &= var(\hat{X}) + var(\tilde{X}) \\ &= \pmb{var(E[X|Y]) + E[var(X|Y)]} \end{aligned}$$
***
## <u>4.4 Transforms (Moment-Generating Function)</u>
- The transform associated with a r.v. $X$ is a function $M_X(s)$ (associated MGF) of a scalar parameter $s$: $$M_X(s)=E[e^{sX}]= \begin{cases} \sum\limits_x e^{sx}p_X(x) &,\ if\ X\ is\ discrete \\ \int_{-\infty}^{\infty} e^{sx}f_X(x) dx &,\ if\ X\ is\ continuous \end{cases}$$
- $X \sim Pois(\lambda):$ $$M(s)=e^{\lambda(e^s-1)}$$
- $X \sim Exp(\lambda):$ $$M(s)=\dfrac{\lambda}{\lambda-s},\ only\ if\ s<\lambda$$
- $Y=aX+b$: $$M_Y(s)=E[e^{s(aX+b)}]=e^{sb}E[e^{saX}]=e^{sb}M_X(sa)$$
- $Y \sim Z(0,1):$ $$M_Y(s)=e^{s^2/2}$$
$X \sim N(\mu, \sigma^2),\ X=\sigma Y + \mu$ $$M_X(s)=e^{s\mu}M_Y(s\sigma)=e^{s^2\sigma^2/2 + \mu s}$$
### 4.4.1 From Transforms(MGFs) to Moments
- $$\dfrac{d}{ds}M(s)=\dfrac{d}{ds}\int_{-\infty}^{\infty} e^{sx}f_X(x) dx=\int_{-\infty}^{\infty} xe^{sx}f_X(x) dx$$
- $$\dfrac{d}{ds}M(s) \bigg|_{s=0} = \int_{-\infty}^{\infty} xf_X(x) dx=E[X]$$
- $$\dfrac{d^n}{ds^n}M(s) \bigg|_{s=0} = \int_{-\infty}^{\infty} x^nf_X(x) dx=E[X^n]$$
- **Why does MGF work?** $$Recall\ e^x=1+x+\dfrac{x^2}{2!}+\dfrac{x^3}{3!}+\cdots$$ $$and\ e^{sx}=1+sx+\dfrac{s^2}{2!}t^2+\dfrac{s^3}{3!}t^3+\cdots$$ $$\Longrightarrow E[e^{sX}]=1+sE[X]+\dfrac{s^2}{2!}E[X^2]+\dfrac{s^3}{3!}E[X^3]+\cdots$$ $$\begin{aligned} \Longrightarrow \dfrac{d}{ds}E[e^{sX}]\bigg|_{s=0} &= 0+E[X]+sE[X^2]+\dfrac{3s^2}{3!}E[X^3]+\cdots \\ &=0+E[X]+0+0+\cdots \\ &= E[X] \end{aligned}$$ $$\begin{aligned} and\ \dfrac{d^2}{ds^2}E[e^{sX}]\bigg|_{s=0} &= 0+0+E[X^2]+\dfrac{3!s}{3!}E[X^3]+\cdots \\ &=0+0+E[X^2]+0+\cdots \\ &= E[X^2] \end{aligned}$$
- Properties of MGF:
    - $M_X(0)=E[e^{0X}]=1$
    - $If\ X\ only\ takes\ nonnegative\ integer\ values,\ \lim\limits_{s \to -\infty}M_X(s)=P(X=0)$
- Convergence of MGFs $\Longrightarrow$ Convergence of CDFs: 
That is, let $X_1,X_2,\dots$ be a sequence of r.v.'s, each with MGF $M_{X_i}(s)$ and CDF $F_{X_i}(x)$
Suppose $\lim\limits_{i \to \infty} M_{X_i}(s)=M_X(s)$, $\forall s$ in a neighborhood of $0$, and $M_X(s)$ is an MGF
Then there exists a r.v. $X$ with CDF $F_X(x)$ where
$\lim\limits_{i \to \infty} F_{X_i}(x) = F_X(x)$
and this r.v. $X$ has moments determined by MGF $M_X(s)$
    <details>
    <summary>Example: Convergence of Binomial and Poisson MGFs$</summary>

    $Bin(n,p)$ can be approx by $Pois(\lambda)$ using $\lambda=np$,
    Let $X \sim Bin(n,p)$, $Y \sim Pois(np)$,
    $M_X(s)=(1-p+pe^s)^n$
    $M_Y(s)=e^{np(e^s-1)}$
    $$\begin{aligned} M_X(s) &= (1-p+pe^s)^n \\ &= (1+p(e^s-1))^n \\ &= (1+\dfrac{np(e^s-1)}{n})^n \\ &= e^{np(e^s-1)},\ when\ n \to \infty \\ &= M_Y(s) \end{aligned}$$
    </details>
### 4.4.2 Inversion of Transforms
- The transform $M_X(s)$ associated with a r.v. $X$ uniquely determines the CDF of $X$, assuming that $M_X(s)$ is finite for all $s$ in some interval $[-a, a]$, where $a$ is a positive number
- The transform associated with a mixture of distributions: 
Let $X_1,\dots,X_n$ be continuous r.v.'s with PDFs $f_{X_1},\dots,f_{X_n}$. The value $y$ of a r.v. $Y$ is generated as follows: an index $i$ is chosen with a corresponding probability $p_i$, and $y$ is taken to be equal to the value of $X_i$. Then, $$f_Y(y)=p_1f_{X_1}(y) + \cdots + p_nf_{X_n}(y)$$ and $$M_Y(s)=p_1M_{X_1}(s)+\cdots+p_nM_{X_n}(s)$$
### 4.4.3 Sum of Independent Random Variables - MGF (Another way: 4.1.5 Convolution)
- Let $X,Y$ be independent r.v.'s, and let $Z=X+Y$: $$M_Z(s)=E[e^{s(X+Y)}]=E[e^{sX}e^{sY}]=E[e^{sX}]E[e^{sY}]=M_X(s)M_Y(s)$$
- If $X_1,\dots,X_n$ is a collection of independent r.v.'s, and $Z=X_1+\cdots+X_n$, then $$M_Z(s)=M_{X_1}(s) \cdots M_{X_n}(s)$$
### 4.4.4 Transfroms Associated with Joint Distributions
- Consider $n$ r.v.'s $X_1,\dots,X_n$ related to the same experiment. Let $s_1,\dots,s_n$ be scalar free parameters. The associated multivariate transform is a function of these $n$ parameters: $$M_{X_1,\dots,X_n}(s_1,\dots,s_n)=E[e^{s_1X_1+\cdots+s_nX_n}]$$
***
## <u>4.5 Sum of a Random Number of Independent Random Variables</u>
- Let $X_1,X_2,\dots$ be identically distributed r.v.'s with mean $E[X]$ and variance $var(X)$. Let $N$ be a r.v. that takes nonnegative integer values. Assume all of these r.v.'s are independent and the sum $Y=X_1+\cdots+X_N$, then:
    - $E[Y]=E[N]E[X]$
        <details>
        <summary>Proof</summary>

        $$\begin{aligned} E[Y|N=n] &= E[X_1+\cdots+X_N|N=n] \\ &=  E[X_1+\cdots+X_n] \\ &= nE[X] \end{aligned}$$ $$\Longrightarrow E[Y|N]=NE[X]$$ $$\stackrel{Law\ of\ Iterated\ Expectations}{\Longrightarrow} E[Y]=E[E[Y|N]]=E[NE[X]]=E[N]E[X]$$
        </details>
    - $var(Y)=E[N]var(X)+(E[X])^2var(N)$
        <details>
        <summary>Proof</summary>

        $$\begin{aligned} var(Y|N=n) &= var(X_1+\cdots+X_N|N=n) \\ &=  var(X_1+\cdots+X_n) \\ &= nvar(X) \end{aligned}$$ $$\Longrightarrow var(Y|N])=Nvar(X)$$ $$\begin{aligned} \stackrel{Law\ of\ Total\ Variance}{\Longrightarrow} var(Y) &= E[var(Y|N)]+var(E[Y|N]) \\ &= E[Nvar(X)]+var(NE[X]) \\ &= E[N]var(X)+(E[X])^2var(N) \end{aligned}$$
        </details>
    - $M_Y(s)=M_N \big( \log{M_X(s)} \big)$
        <details>
        <summary>Proof</summary>

        $$\begin{aligned} E[e^{sY}|N=n] &= E[e^{s(X_1+\cdots+X_N)}|N=n] \\ &=  E[e^{sX_1} \cdots e^{sX_n}] \\ &= E[e^{sX_1}] \cdots E[e^{sX_n}] \\ &= \big( M_X(s) \big)^n \end{aligned}$$ $$\Longrightarrow E[e^{sY}|N]=\big( M_X(s) \big)^N$$ $$\stackrel{Law\ of\ Iterated\ Expectations}{\Longrightarrow} M_Y(s) = E[e^{sY}] = E[E[e^{sY}|N]] = E[\big( M_X(s) \big)^N] = \sum_{n=1}^{\infty} \big( M_X(s) \big)^n P_N(n)$$ $$while,\ M_N(s) = E[e^{sN}] = \sum_{n=1}^{\infty} (e^s)^n P_N(n)$$ $$when\ M_X(s)=e^s,\ s=\log{M_X(s)}$$ $$M_N \big( \log{M_X(s)} \big)=M_Y(s)$$
        </details>
***
## <u>4.6 Beta and Gamma</u>
- Sterling Formula: $$n! \approx \sqrt{2 \pi n} \bigg( \dfrac{n}{e} \bigg)^n$$
- Gamma Function: $$\Gamma(a)=\int_0^{\infty} x^a e^{-x} \dfrac{dx}{x},\ for\ real\ a>0$$ $$\Gamma(n)=(n-1)!,\ for\ positive\ integer\ n$$ $$\Gamma(x+1)=x \Gamma(x)$$ $$\Gamma(\dfrac{1}{2}) = \sqrt{\pi},\ \Gamma(\dfrac{3}{2}) = \dfrac{\sqrt{\pi}}{2}$$
- Gamma Distribution:
    - $X \sim Gamma(a,1)$ $$f_X(x) = \dfrac{1}{\Gamma(a)} x^a e^{-x} \dfrac{1}{x}$$
    - $Y \sim Gamma(a,\lambda)$, that is, $Y=\dfrac{X}{\lambda},\ where\ X \sim Gamma(a,1)$ $$\begin{aligned} f_Y(y) &= f_X(x) \dfrac{dx}{dy} = \lambda f_X(\lambda y) \\ &= \dfrac{1}{\Gamma(a)} (\lambda y)^a e^{- \lambda y} \dfrac{1}{y} \end{aligned}$$
    - Moments of $X \sim Gamma(a,1)$ $$E[X^k] = \int_0^{\infty} x^k \dfrac{1}{\Gamma(a)} x^a e^{-x} \dfrac{1}{x} = \dfrac{1}{\Gamma(a)} \int_0^{\infty} x^{a+k} e^{-x} \dfrac{1}{x} = \dfrac{\Gamma(a+k)}{\Gamma(a)},\ if\ a+k > 0$$ $$E[X] = \dfrac{\Gamma(a+1)}{\Gamma(a)}=a$$ $$E[X^2] = \dfrac{\Gamma(a+2)}{\Gamma(a)} = (a+1)a$$ $$var(X) = E[X^2] - (E[X])^2 = a$$
    - Moments of $Y \sim Gamma(a, \lambda),\ Y=\dfrac{X}{\lambda}$ $$E[Y]=\dfrac{a}{\lambda}$$ $$var(Y) = \dfrac{a}{\lambda^2}$$
- Gamma-Exponential Connection: in Poisson process, interarrival times are i.i.d. $Exp(\lambda)$, $k$th arrival time is $Gamma(k, \lambda)$, which is sum of exponentials
Proof: $T_n \sim Gamma(n,1),\ where\ T_n = \sum\limits_{j=1}^n X_j,\ X_j \stackrel{i.i.d.}{\sim} Exp(1)$
$$M_{T_n}(s) = E[e^{s T_n}] = E \bigg[ e^{s \sum\limits_{j=1}^n X_j} \bigg] = (E[e^{s X_1}])^n = \bigg( \dfrac{1}{1-s} \bigg)^n,\ s<1$$
$$Let\ Y \sim Gamma(n,1),\ M_Y(s) = E[e^{sY}] = \int_0^{\infty} e^{sy} \dfrac{1}{\Gamma(n)} y^n e^{-y} \dfrac{dy}{y} = \dfrac{1}{\Gamma(n)} \int_0^{\infty} y^n e^{-(1-s)y} \dfrac{dy}{y}$$ $$Let\ x=(1-s)y,\ then\ M_Y(s) = \dfrac{1}{\Gamma(n)} \int_0^{\infty} \bigg( \dfrac{x}{1-s} \bigg)^n e^{-x} \dfrac{dx}{x} = \dfrac{1}{(1-s)^n \Gamma(n)} \underbrace{\int_0^{\infty} x^n e^{-x} \dfrac{dx}{x}}_{\Gamma(n)} = \bigg( \dfrac{1}{1-s} \bigg)^n$$ $$\therefore M_Y(s)=M_{T_n}(s),\ T_n \sim Gamma(n,1)$$
- Gamma-Beta Connection: bank - post office example
Waiting time at the bank $X \sim Gamma(a,\lambda)$, waiting time at the post office $Y \sim Gamma(b,\lambda)$, $X,Y$ are independent. Find the joint distribution of total waiting time $T=X+Y$ and the portion of time waiting at the bank $W=\dfrac{X}{X+Y}$. Let $lambda=1$ to simplify notations.
$$f_{T,W}(t,w) = f_{X,Y}(x,y) \bigg| \dfrac{\partial(x,y)}{\partial(t,w)} \bigg| = \dfrac{1}{\Gamma(a)\Gamma(b)} x^a e^{-x} y^b e^{-y} \dfrac{1}{xy} \bigg| \dfrac{\partial(x,y)}{\partial(t,w)} \bigg|$$ $$x+y=t,\dfrac{x}{x+y}=w \Rightarrow x=tw,y=t(1-w)$$ $$\bigg| \dfrac{\partial(x,y)}{\partial(t,w)} \bigg| = \left|
    \begin{matrix}
    \dfrac{\partial{x}}{\partial{t}} & \dfrac{\partial{x}}{\partial{w}} \\
    \dfrac{\partial{y}}{\partial{t}} & \dfrac{\partial{y}}{\partial{w}}
    \end{matrix}
    \right|
    = \left|
    \begin{matrix}
    w & t \\
    1-w & -t
    \end{matrix}
    \right| = |-tw-t(1-w)| = t$$ $$\begin{aligned} f_{T,W}(t,w) &= \dfrac{1}{\Gamma(a)\Gamma(b)} (tw)^a e^{-tw} (t(1-w))^b e^{-t(1-w)} \dfrac{t}{t^2w(1-w)} \\ &= \dfrac{1}{\Gamma(a)\Gamma(b)} w^{a-1} (1-w)^{b-1} \cdot t^{a+b} e^{-t} \dfrac{1}{t} \\ &= \dfrac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)} w^{a-1} (1-w)^{b-1} \cdot \dfrac{1}{\Gamma(a+b)} t^{a+b} e^{-t} \dfrac{1}{t}  \end{aligned}$$ $$\therefore f_T(t) = \dfrac{1}{\Gamma(a+b)} t^{a+b} e^{-t} \dfrac{1}{t},\ f_W(w) = \dfrac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)} w^{a-1} (1-w)^{b-1}$$ $$T \sim Gamma(a+b,1),\ W \sim Beta(a,b),\ and\ T,W\ are\ independent$$
- Expectation of Beta distribution:
$$\because T,W\ are\ independent$$ $$\begin{aligned} \therefore E[TW] &= E[T]E[W] \\ E[X] &= E[T]E[W] \\ E[W] &= \dfrac{E[X]}{E[T]} = \dfrac{a}{a+b} \end{aligned}$$
- Order Statistics:
Let $X_1,\dots,X_n$ be i.i.d with PDF $f$ and CDF $F$. The order statistics are $X_{(1)} \leq X_{(2)} \leq \cdots \leq X_{(n)}$, where $X_{(1)}=\min(X_1,\dots,X_n)$, $X_{(2)}$ is the second smallest, $\dots$, $X_{(n)}=\max(X_1,\dots,X_n)$, apparently $X_{(j)}$ are dependent. Find the CDF and PDF of $X_{(j)}$
$$F_{X_{(j)}}(x) = P(X_{(j)} \leq x) = P(at\ least\ j\ of\ X_i's\ \leq x) = \sum_{k=j}^n {n \choose k} F(x)^k (1-F(x))^{n-k}$$ $\because$ for PDF of $X_{(j)}$, consider one of $X_i's$ is in the tiny little interval around $x$, $j-1$ of them are to the left, and $n-j$ of them are to the right $$\therefore f_{X_{(j)}}(x)dx = nf(x)dx \cdot {n-1 \choose j-1} F(x)^{j-1} (1-F(x))^{n-j}$$ $$f_{X_{(j)}}(x) = n {n-1 \choose j-1} F(x)^{j-1} (1-F(x))^{n-j} f(x)$$ for example, if $U_1,\dots,U_n$ are i.i.d. $Unif(0,1)$, then $$f_{U_{(j)}}(x) = n {n-1 \choose j-1} x^{j-1} (1-x)^{n-j},\ U_{(j)} \sim Beta(j, n-j+1)$$
# Chapter 5 Limit Theorems
***
## <u>5.1 Markov and Chebyshev Inequalities</u>
- Markov Inequality (based on the mean): use a bit of information about a distribution to learn something about probabilities of "extreme events" 
"If $X \geq 0$ and $E[X]$ is small, then $X$ is unlikely to be very large" 
$$If\ X \geq 0\ and\ a > 0,\ then\ P(X \geq a) \leq \dfrac{E[X]}{a}$$
    <details>
    <summary>Proof</summary>

    (1) $$E[X]=\int_0^{\infty} xf_X(x)dx \geq \int_a^{\infty} xf_X(x)dx \geq \int_a^{\infty} af_X(x)dx = a P(X \geq a)$$

    (2) $$Let\ Y= \begin{cases} 0 &, X<a \\ a &, X \geq a \end{cases},\ then\ Y \leq X,\ E[Y] \leq E[X]$$ $$\therefore E[Y]=aP(X \geq a) \leq E[X]$$
    </details>
- Chebyshev Inquality (based on the mean and variance): "If the variance is small, then $X$ is unlikely to be too far from the mean" $$P(|x-\mu| \geq c) \leq \dfrac{\sigma^2}{c^2}$$
    <details>
    <summary>Proof</summary>

    Use Markov Inequality: $$P((X-\mu)^2 \geq c^2) \leq \dfrac{E[(X-\mu)^2]}{c^2} = \dfrac{\sigma^2}{c^2}$$
    </details>

    - $$P(|x-\mu| \geq k\sigma) \leq \dfrac{\sigma^2}{k^2 \sigma^2}=\dfrac{1}{k^2}$$
    - Upper bounds in the Chebyshev Inequality:
    When $X$ is known to take values in a range $[a,b]$, we claim that $\sigma^2 \leq (b-a)^2/4$. Thus, if $\sigma$ is unknown, we may use the bound $(b-a)^2/4$ in place of $\sigma^2$ in the Chebyshev Inequality, and obtain $$P(|x-\mu| \geq c) \leq \dfrac{(b-a)^2}{4c^2}$$
        <details>
        <summary>Proof</summary>

        To verify, note that for any constant $\gamma$, we have $$E[(X-\gamma)^2]=E[X^2]+2E[X]\gamma+\gamma^2=(\gamma-E[X])^2+E[X^2]-(E[X])^2 \geq E[X^2]-(E[X])^2 = \sigma^2$$ Let $\gamma=(a+b)/2$, we obtain $$\sigma^2 \leq E[(X-\dfrac{a+b}{2})^2] = E[(X-a)(X-b)]+\dfrac{(b-a)^2}{4} \stackrel{(x-a)(x-b) \leq 0}{\leq} \dfrac{(b-a)^2}{4}$$ The bound $\sigma^2 \leq (b-a)^2/4$ may be quite conservative, but in the absence of further information about $X$, it cannot be improved. It is satisfied with equality when $X$ is the r.v. that takes the two extreme values $a$ and $b$ with equal probability $1/2$.
        </details>
- Related Topics:
    - Better bounds/approximations on tail probabilities:
        - Chernoff bound $$P(X \geq a) \leq e^{-\phi(a)} ,\ where\ \phi(a)=\max\limits_{s \geq 0}(sa-\ln{M(s)})$$
            <details>
            <summary>Proof and Application</summary>

            (a) For some real number $a$ and $s \geq 0$: 
            $$P(X \geq a) = P(e^{sX} \geq e^{sa}) \stackrel{Markov}{\leq} \dfrac{E[e^{sX}]}{e^{sa}} = e^{-sa}M_X(s) = e^{-(sa-\ln{M_X(s)})}$$ $$\Longrightarrow P(X \geq a) \leq \min\limits_{s \geq 0} e^{-(sa-\ln{M_X(s)})} = e^{- \max\limits_{s \geq 0} ( sa-\ln{M_X(s)} )} = e^{-\phi(a)}$$
            (b) Proof: $if\ a>E[X],\ then\ \phi(a)>0$
            $M_X(s)=E[e^{sX}]=1+sE[X]+\dfrac{s^2}{2!}E[X^2]+ \cdots ,\ near\ s=0$
            $When\ s=0,\ sa-\ln{M_X(s)}=0-\ln{1}=0$
            $and,\ \dfrac{d}{ds} \Big( sa-\ln{M_X(s)} \Big) \bigg|_{s=0} = a - \dfrac{1}{M_X(s)} \dfrac{dM_X(s)}{ds} \bigg|_{s=0} = a - E[X] >0$
            Since $sa-\ln{M_X(s)}$ is zero and has a positive derivative at $s=0$, it must be positive when $s$ is positive and small.
            
            (c) Example: obtain a bound for $P(X \geq a)$ for the case where $X$ is a standard normal r.v. and $a>0$
            $$X \sim Z(0,1),\ M_X(s) = e^{s^2/2}$$ $$\phi(a)=\max\limits_{s \geq 0}(sa-\ln{M(s)}) = \max\limits_{s \geq 0} (sa-\dfrac{s^2}{2}) = \max\limits_{s \geq 0} \Big( -\dfrac{1}{2}(s-a)^2+\dfrac{a^2}{2} \Big) = \dfrac{a^2}{2}$$ $$\therefore P(X \geq a) \leq e^{-a^2/2}$$
            (d) Let $X_1,X_2,\dots$ be independent r.v.'s with the same distribution as $X$. For any $a>E[X]$, $$P \bigg( \dfrac{1}{n} \sum_{i=1}^n X_i \geq a \bigg) \leq e^{-n\phi(a)}$$ so that the probability that the sample mean exceeds the mean by a certain amount decreases exponentially with $n$
            </details>

        - Hoeffding's Inequality: If i.i.d. $X_i$ is equally likely to be $-1$ or $1$, and $a>0$,then $$P(X_1+\cdots+X_n \geq na) \leq e^{-na^2/2}$$
            <details>
            <summary>Proof</summary>

            
            $$P(e^{s(X_1+\cdots+X_n)} \geq e^{sna}) \leq \dfrac{E[e^{s(X_1+\cdots+X_n)}]}{e^{sna}} = \dfrac{\prod\limits_{i=1}^n E[e^{sX_i}]}{e^{sna}} = \bigg( \dfrac{E[e^{sX_i}]}{e^{sa}} \bigg)^n = \bigg( \dfrac{\dfrac{1}{2}(e^s+e^{-s})}{e^{sa}} \bigg)^n$$ $$\because e^s=1+s+\dfrac{s^2}{2!}+\dfrac{s^3}{3!}+\cdots=\sum_{i=0}^{\infty} \dfrac{s^i}{i!}$$ $$\therefore \dfrac{1}{2}(e^s+e^{-s}) = \dfrac{1}{2}(1+s+\dfrac{s^2}{2!}+\dfrac{s^3}{3!}+\cdots) + \dfrac{1}{2}(1-s+\dfrac{s^2}{2!}-\dfrac{s^3}{3!}+\cdots) = \sum_{i=0}^{\infty} \dfrac{s^{2i}}{(2i)!}$$ $$\because (2i)!=\underbrace{1 \cdot 2 \cdot \cdots \cdot i}_{i\ terms} \underbrace{\cdot (i+1) \cdot \cdots \cdot (2i)}_{i\ terms} \geq i! \cdot 2^i$$ $$\therefore \sum_{i=0}^{\infty} \dfrac{s^{2i}}{(2i)!} \leq \sum_{i=0}^{\infty} \dfrac{s^{2i}}{i! \cdot 2^i} = \sum_{i=0}^{\infty} \dfrac{(\dfrac{s^2}{2})^i}{i!} = e^{s^2/2}$$ $$\bigg( \dfrac{\dfrac{1}{2}(e^s+e^{-s})}{e^{sa}} \bigg)^n \leq \bigg( \dfrac{e^{s^2/2}}{e^{sa}} \bigg)^n = \bigg( e^{s^2/2-sa} \bigg)^n \stackrel{Let\ s=a}{=} e^{-na^2/2}$$
            </details>

        - Central limit theorem (5.4)
    - Jensen's Inequality: comparing $E\big[ g(X) \big]$ to $g \big( E[X] \big)$
    $$Let\ g\ be\ convex,\ then\ E\big[ g(X) \big] \geq g \big( E[X] \big)$$ "convex" means that $$for\ any\ c,x:\ g(x) \geq g(c)+g'(c)(x-c)$$ For example:
        - $g(x)=x^2$
        - $g(x)=-\log x$

***
## <u>5.2 The Weak Law of Large Numbers (WLLN)</u>
- WLLN asserts that the sample mean of a large number of i.i.d. r.v.'s is very close to the true mean with high probability
    - Consider a sequence $X_1,X_2,\dots$ of i.i.d. r.v.'s with mean $\mu$ and variance $\sigma^2$
        - Define sample mean by $$M_n=\dfrac{X_1+\cdots+X_n}{n}$$
        - $$E[M_n]=\dfrac{E[X_1]+\cdots+E[X_n]}{n}=\dfrac{n\mu}{n}=\mu$$
        - $$var(M_n)=\dfrac{var(X_1)+\cdots+var(X_n)}{n^2}=\dfrac{n\sigma^2}{n^2}=\dfrac{\sigma^2}{n}$$
        - Apply the Chebyshev Inequality and obtain $$P(|M_n-\mu| \geq \epsilon) \leq \dfrac{\sigma^2}{n\epsilon^2} \stackrel{n \to \infty}{\longrightarrow} 0$$
    - **WLLN:** $$For\ \epsilon >0,\ P(|M_n-\mu| \geq \epsilon)=P \Big( \Big| \dfrac{X_1+\cdots+X_n}{n}-\mu \Big| \geq \epsilon \Big) \longrightarrow 0,\ as\ n \to \infty$$
- Probabilities and Frequencies: consider an event $A$ defined the conext of some probabilistic experiment. Let $p=P(A)$ be the probability of this event. We consider $n$ independent repetitions of the experiment, and let $M_n$ be the fraction of time that event $A$ occurs; in this context, $M_n$ is often called the **empirical frequency** of $A$. $$M_n=\dfrac{X_1+\cdots+X_n}{n}$$ $$X_i= \begin{cases} 1 &,\ if A\ occurs \\ 0 &,\ otherwise \end{cases}$$ $E[X_i]=p$, the WLLN applies and shows that when $n$ is large, the empirical frequency is most likely to be within $\epsilon$ of $p$. This allows us to conclude that empirical frequencies are faithful estimates of $p$.
***
## <u>5.3 Convergence in Probability</u>
- Convergence of a Deterministic Sequence:
Let $a_1,a_2,\dots$ be a sequence of real numbers, and let $a$ be another real number. We say that the sequence $a_n$ converges to $a$, or $\lim\limits_{n \to \infty} a_n = a$, if for every $\epsilon>0$ there exists some $n_0$ such that $$|a_n-a|\leq \epsilon,\ for\ all\ n \geq n_0$$ <img src="https://s1.ax1x.com/2020/04/14/JSMSk8.md.png" width = "500" />
- Convergence in Probability:
Let $Y_1,Y_2,\dots$ be a sequence of r.v.'s (not necessarily independent), and let $a$ be a real number. We say that the sequence $Y_n$ converges to $a$ in probability, if for every $\epsilon > 0$, we have $$\lim_{n \to \infty} P(|Y_n-a| \geq \epsilon)=0$$ <img src="https://s1.ax1x.com/2020/04/14/JS8okt.md.png" width = "500" />
"Almost all of the PMF/PDF of $Y_n$ eventually gets concentrated arbitrarily close to $a$"
- Convergence in probability **does not** imply convergence of expectations: convergence in probability only cares about that the tail of the distribution has small probability; the expectation is highly sensitive to the tail of the distribution
    <details>
    <summary>Example</summary>

    [![JSUpSP.png](https://s1.ax1x.com/2020/04/14/JSUpSP.png)](https://imgchr.com/i/JSUpSP)
    </details>
- Convergence in probability of the sum of two r.v.'s: $$If\ X_n \to a\ and\ Y_n \to b,\ then\ X_n+Y_n \to a+b$$
- Related Topics:
    - Different types of convergene
        - Convergence "with probability 1": when an outcome of the experiment is obtained, the resulting sequence of the values of the r.v.'s $Y_n$ will converge to the value of the r.v. $Y$ $$P( \{ \omega: Y_n(\omega) \stackrel{n \to \infty}{\longrightarrow} Y(\omega) \} ) = 1$$
        - Strong law of large numbers (5.5)
        - Convergence of a sequence of distributions (CDFs) to a limiting CDF
***
## <u>5.4 Central Limit Theorem</u>
- Different scaling of the sum of i.i.d. r.v.'s:
    - $S_n=X_1+\cdots+X_n$ $$E[S_n]=n\mu,\ var(S_n)=n\sigma^2$$
    - $M_n=\dfrac{S_n}{n}=\dfrac{X_1+\cdots+X_n}{n}$ $$E[M_n]=\mu,\ var(M_n)=\dfrac{\sigma^2}{n}$$
    - $Z_n=\dfrac{S_n-n\mu}{\sqrt{n}\sigma}$ $$E[Z_n]=0,\ var(Z_n)=1$$
- **Central Limit Theorem:** $$\lim_{n \to \infty} P(Z_n \leq z)=\Phi(z)=\dfrac{1}{\sqrt{2\pi}} \int_{-\infty}^{z} e^{-t^2/2} dt,\ for\ all\ z$$
    <details>
    <summary>Proof using convergence of MGF</summary>

    Let $X_1,\dots,X_n$ be a sequence of i.i.d. r.v.'s with mean $0$, variance $\sigma^2$ and associated transform (MGF) $M_X(s)$. Assume that $M_X(s)$ is finite when $-d<s<d$, where $d$ is some positive number. Let $$Z_n=\dfrac{X_1+\cdots+X_n}{\sigma \sqrt{n}}$$
    (a) The transform associated with $Z_n$ satisfies $$M_{Z_n}(s)=\bigg( M_X \big( \dfrac{s}{\sigma \sqrt{n}} \big)  \bigg)^n$$ Derivation: 
    $$\begin{aligned} M_{Z_n}(s) = E[e^{sZ_n}] &= E \bigg[ exp \bigg\{ \dfrac{S}{\sigma \sqrt{n}} \sum_{i=1}^n X_i \bigg\} \bigg] \\ &= \prod_{i=1}^n \bigg[ exp \bigg\{ \dfrac{S}{\sigma \sqrt{n}} X_i \bigg\} \bigg] \\ &= \bigg( M_X \big( \dfrac{s}{\sigma \sqrt{n}} \big)  \bigg)^n \end{aligned}$$
    (b) Suppose that the transform $M_X(s)$ has a second order Tyler series expansion around $s=0$, of the form $$M_X(s) = a + bs + cs^2 + o(s^2)$$ where $o(s^2)$ is a function that satisfies $\lim\limits_{s \to 0} o(s^2)/s^2=0$. Find $a,b,c$.
    Derivation: $$a=M_X(0)=1$$ $$b = \dfrac{d}{ds} M_X(s) \bigg|_{s=0} = E[X] = 0$$ $$c = \dfrac{1}{2!} \dfrac{d^2}{ds^2} M_X(s) \bigg|_{s=0} = \dfrac{1}{2} E[X^2] = \dfrac{\sigma^2}{2}$$
    (c) Combine the results of (a) and (b) to show that the transform $M_{Z_n}(s)$ converges to the transform associated with a standard normal random variable, that is, $$\lim_{n \to \infty} M_{Z_n}(s) = e^{s^2/2} ,\ for\ all\ s$$ Derivation: $$\begin{aligned} M_{Z_n}(s)=\bigg( M_X \big( \dfrac{s}{\sigma \sqrt{n}} \big)  \bigg)^n &= \bigg( a + \dfrac{bs}{\sigma \sqrt{n}} + \dfrac{cs^2}{\sigma^2 n} + o\big( \dfrac{s^2}{\sigma^2 n} \big) \bigg)^n \\ &= \bigg( 1 + \dfrac{s^2}{2 n} + o\big( \dfrac{s^2}{\sigma^2 n} \big) \bigg)^n \end{aligned}$$ $$\lim_{n \to \infty} M_{Z_n}(s)=\lim_{n \to \infty} \bigg( 1 + \dfrac{\frac{s^2}{2}}{n} \bigg)^n=e^{s^2/2}$$
    </details>

## 5.4.1 Approximations Based on the CLT
- Let $S_n=X_1+\cdots+X_n$, where the $X_i$ are i.i.d. r.v.'s with mean $\mu$ and variance $\sigma^2$. If $n$ is large, the probability $P(S_n \leq c)$ can be approximated by treating $S_n$ as if it were normal, according to the following procedure.
    - 1. Calculate the mean $n\mu$ and the variance $n\sigma^2$ of $S_n$
    - 2. Calculate the normalized value $z=\dfrac{c-n\mu}{\sqrt{n} \sigma}$
    - 3. Use the approximation $$P(S_n \leq c) \approx \Phi(z)$$ where $\Phi(z)$ is available from standard normal CDF tables
- The normal approximation is increasingly accurate as $n \to \infty$
- How large $n$ should be depends on whether the distribution of $X_i$ is close to normal and whether it is symmetric
- The normal approximation to $P(S_n \leq c)$ tends to be more faithful when $c$ is in the vicinity of the mean of $S_n$
### 5.4.2 De Moivre-Laplace Approximation to the Binomial
- If $S_n$ is a binomial r.v. with parameters $n$ and $p$, $n$ is large, and $k,l$ are nonnegative integers, then $$P(k \leq S_n \leq l) \approx \Phi \bigg( \dfrac{l+\frac{1}{2}-np}{\sqrt{np(1-p)}} \bigg)-\Phi \bigg( \dfrac{k-\frac{1}{2}-np}{\sqrt{np(1-p)}} \bigg)$$
<div align=center>
<img src="https://s1.ax1x.com/2020/04/18/JeazSP.png" />
</div>


***
## <u>5.5 The Strong Law of Large Numbers</u>
- Let $X_1,X_2,\dots$ be a sequence of i.i.d. r.v.'s with mean $\mu$. Then, the sequence of sample means $M_n=(X_1+\cdots+X_n)/n$ converges to $\mu$, with probability 1 $$P\bigg( \lim_{n \to \infty} \dfrac{X_1+\cdots+X_n}{n}=\mu \bigg)=1$$
- Convergence with Probability 1:
Let $Y_1,Y_2,\dots$ be a sequence of r.v.'s (not necessarily independent). Let $c$ be a real number. $Y_n$ converges to $c$ with probability 1 (or almost surely) if $$P(\lim_{n \to \infty} Y_n = c) = 1$$
- Convergence with probability 1 implies convergence in probability, but the converse is not necessarily true

# Chapter 6 The Bernoulli and Poisson Processes
***
## <u>6.1 The Bernoulli Process</u>
- A sequene of independent Bernoulli trials $X_i$, at each trial $i$: 
$P(X_i=1)=P(success\ at\ the\ i_{th}\ trial)=p$
$P(X_i=0)=P(failure\ at\ the\ i_{th}\ trial)=1-p$
- Stochastic processes:
    - First view: infinite sequence of r.v.'s $X_1,X_2,\dots$
    Interested in: 
    $E[X_i]=p,\ var(X_i)=p(1-p),\ p_{X_i}(x) = \begin{cases} p &,\ x=1 \\ 1-p &,\ x=0 \end{cases}$
    $p_{X_1,\dots,X_n}(x_1,\dots,x_n) \stackrel{indep.}{=} p_{X_1}(x_1) \cdots p_{X_n}(x_n) ,\ for\ all\ n$
    - Second view: sample space $\Omega$ = set of infinite sequences of $0$'s and $1$'s (a phenomenon that evolves over time)
- Number of successes/arrivals $S$ in $n$ time slots:
    - $S = X_1 + \cdots + X_n$
    - $p_S(k) = {n \choose k} p^k (1-p)^{n-k},\ k=0,\dots,n$
    - $E[S] = np$
    - $var(S) = np(1-p)$
- Time until the first success/arrival:
    - $T = \min \{ i: X_i=1 \}$
    - $p_T(k) = (1-p)^{k-1}p$
    - $E[T] = \dfrac{1}{p}$
    - $var(T) = \dfrac{1-p}{p^2}$
### 6.1.1 Independence, Memorylessness and Fresh-Start Properties
- For any given time $n$, the sequence of r.v.'s $X_{n+1},X_{n+2},\dots$ (the future of the process) is also a Bernoulli process, and is independent from $X_1,\dots,X_n$ (the past of the process)
- Let $n$ be a given time and let $\bar{T}$ be the time of the first success after time $n$. Then, $\bar{T}-n$ has a geometric distribution with parameter $p$ and is independent of the r.v.'s $X_1,\dots,X_n$ $$P(\bar{T}-n=t|\bar{T}>n)=(1-p)^{t-1}p=P(\bar{T}=t)$$
### 6.1.2 Interarrival Times
- $Y_k$: the time of the $k$th success/arrival
$T_k$: the $k$th interarrival time ($T_i \sim i.i.d.\ Geo(p)$)
$$T_1=Y_1$$ $$T_k = Y_k - Y_{k-1} \ for\ k=2,3,\dots$$
### 6.1.3 Time of $k$th Success/Arrival
- $Y_k=T_1+\cdots+T_k$
- $E[Y_k]=E[T_1]+\cdots+E[T_k]=\dfrac{k}{p}$
- $var(Y_k)=var(T_1)+\cdots+var(T_k)=\dfrac{k(1-p)}{p^2}$
- $p_{Y_k}(t)={t-1 \choose k-1} p^k (1-p)^{t-k},\ t=k,k+1,\dots$
### 6.1.4 Splitting and Merging of Bernoulli Processes
- Splitting: $splitted\ processes \sim Bern(pq)\ and\ Bern(p(1-q))$
<img src="https://s1.ax1x.com/2020/04/20/JQtuzn.md.png" width="500" />
- Merging: $merged\ process \sim Bern(p+q-pq)$
<img src="https://s1.ax1x.com/2020/04/20/JQtMMq.md.png" width="500" />
***
## <u>6.2 The Poisson Process</u>
- Definition: $$P(k,\tau)=P(there\ are\ exactly\ k\ arrivals\ during\ an\ interval\ of\ length\ \tau)$$ An arrival process is called a Poisson process with arrival rate/intensity $\lambda$ (probability per unit time) if it has the following properties:
    - **Time-homogeneity:** the probability $P(k,\tau)$ of $k$ arrivals is the same for all intervals of the same length $\tau$
    - **Independence:** the number of arrivals during a particular interval is independent of the history of arrivals outside this interval
    - **Small interval probabilities:** for every small interval $\delta$, the probabilities $P(k,\delta)$ satisfy $$P(k,\delta)= \begin{cases} 1-\lambda\delta+O(\delta^2) &,\ k=0 \\ \lambda\delta+O(\delta^2) &,\ k=1 \\ 0+O(\delta^2) &,\ k=2,3,\dots \end{cases}$$ Here, $$\lim_{\delta \to 0} \dfrac{O(\delta^2)}{\delta}=0$$
### 6.2.1 Number of Arrivals in an Interval
- Numbers of arrivals in an interval: $N_{\tau}$
$P(k,\tau)$ is approximately the same as the binomial probability of $k$ successes in $n=\tau/\delta$ independent Bernoulii trials with success probability $p=\lambda\delta$ at each interval. While keeping the length $\tau$ of the interval fixed, let the period length $\delta \to 0$. Then the number of periods $n \to \infty$ and success probability $p \to 0$, while $np=\lambda\tau$ reamins constant.
$$p_{N_{\tau}}(k)=P(k, \tau)= e^{-\lambda\tau} \dfrac{(\lambda\tau)^k}{k!},\ k=0,1,\dots$$ $$E[N_{\tau}]=\lambda\tau,\ var(N_{\tau})=\lambda\tau$$
- Time until the first arrival: $T$
Assuming that the process starts at time $0$. We have $T>t$ if and only if there are no arrivals during the interval $[0,t]$ $$F_T(t)=P(T \leq t)=1-P(T > t)=1-P(0,t)=1-e^{-\lambda t}$$ $$f_T(t)=\dfrac{d}{dt}F_T(t)=\lambda e^{-\lambda t}$$ $$E[T]=\dfrac{1}{\lambda},\ var(T)=\dfrac{1}{\lambda^2}$$
- The sum of independent Poisson random variables is Poisson: the probability of $k$ arrivals during a set of times of total length $\tau$ is always given by $P(k,\tau)$, even if that set is not an interval
### 6.2.2 Independence and Memorylessness
- For any given time $t>0$, the process after time $t$ is also a Poisson process, and is independent from history of the process until time $t$
- Let $t$ be a given time and let $\bar{T}$ be the time of the first arrival after time $t$. Then, $\bar{T}-t$ has an exponential distribution with parameter $\lambda$, and is independent of the history of the process until time $t$ $$P(\bar{T}-t>s)=P(0\ arrival\ during\ [t,t+s])=P(0,s)=e^{-\lambda s}$$
### 6.2.3 Interarrival Times
- $Y_k$: the time of the $k$th success/arrival
$T_k$: the $k$th interarrival time ($T_i \sim i.i.d.\ Exp(\lambda)$)
$$T_1=Y_1$$ $$T_k = Y_k - Y_{k-1} \ for\ k=2,3,\dots$$
### 6.2.4 The $k$th Arrival Time
- $Y_k=T_1+\cdots+T_k$
- $E[Y_k]=E[T_1]+\cdots+E[T_k]=\dfrac{k}{\lambda}$
- $var(Y_k)=var(T_1)+\cdots+var(T_k)=\dfrac{k}{\lambda^2}$
- $f_{Y_k}(y)=\dfrac{\lambda^k y^{k-1} e^{-\lambda y}}{(k-1)!},\ y \geq 0$
$Y_k \sim Erlang(k, \lambda)$
### 6.2.5 Splitting and Merging of Poisson Processes
- Splitting: $splitted\ processes \sim Pois(\lambda q)\ and\ Pois(\lambda (1-q))$
Unlike splitted Bernoulli processes, splitted Poisson processes are independent
- Merging: $merged\ process \sim Pois(\lambda_1+\lambda_2)$
Any particular arrival of the merged process has probability $\lambda_1/(\lambda_1+\lambda_2)$ of originating from the first process and probability $\lambda_2/(\lambda_1+\lambda_2)$ of originating from the second process, independent of all other arrivals and their origins

&nbsp; | $$1-\lambda_1\delta$$ $$0$$ | $$\lambda_1\delta$$ $$1$$ | $$O(\delta^2)$$ $$\geq 2$$
- | - | - | - 
$1-\lambda_2\delta$ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $0$ | $$1-(\lambda_1+\lambda_2)\delta+O(\delta^2)$$ | $$\lambda_1\delta+O(\delta^2)$$ | $$0$$
$\lambda_2\delta$ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $1$ | $$\lambda_2\delta+O(\delta^2)$$ | $$O(\delta^2)$$ | $$0$$
$O(\delta^2)$ &nbsp;&nbsp;&nbsp;&nbsp; $\geq 2$ | $$0$$ | $$0$$ | $$0$$

Example: 
$P(originate\ from\ 1st\ process | arrival\ at\ time\ t) = \dfrac{\lambda_1}{\lambda_1+\lambda_2}$
$P(kth\ arrival\ originates\ from\ 1st\ process) = \dfrac{\lambda_1}{\lambda_1+\lambda_2}$
$P(4\ out\ of\ first\ 10\ arrivals\ originate\ from\ 1st\ process) = {10 \choose 4} \bigg( \dfrac{\lambda_1}{\lambda_1+\lambda_2} \bigg)^4 \bigg( \dfrac{\lambda_2}{\lambda_1+\lambda_2} \bigg)^6$

- Competing Exponentials: three light bulbs have independent and exponentially distributed lifetimes $T_a$, $T_b$ and $T_c$, with parameters $\lambda_a$, $\lambda_b$ and $\lambda_c$.
(a) Find the distribution of the time until fisrt burn out, $Z=\min\{T_a,T_b,T_c\}$
$$\begin{aligned} F_Z(z) &= P(\min\{T_a,T_b,T_c\} \leq z) \\ &= 1- P(\min\{T_a,T_b,T_c\} > z) \\ &= 1 - P(T_a > z, T_b > z, T_c > z) \\ &= 1 - P(T_a > z)P(T_b > z)P(T_c > z) \\ &= 1 - e^{-\lambda_a z}e^{-\lambda_b z}e^{-\lambda_c z} \\ &= 1 - e^{-(\lambda_a+\lambda_b+\lambda_c) z} \end{aligned}$$ $$\therefore Z \sim Exp(\lambda_a+\lambda_b+\lambda_c),\ E[Z]=\dfrac{1}{\lambda_a+\lambda_b+\lambda_c}$$
(b) If $\lambda_a=\lambda_b=\lambda_c=\lambda$, find the expected time until all burn out $$T_1 = time\ until\ 1st\ burn\ out$$ $$T_2 = time\ after\ 1st\ burn\ out\ until\ 2nd$$ $$T_3 = time\ after\ 2nd\ burn\ out\ until\ 3rd$$ $$T_1 \sim Exp(3\lambda), T_2 \sim Exp(2\lambda), T_3 \sim Exp(\lambda)$$ $$E[T_1+T_2+T_3] = \dfrac{1}{3\lambda} + \dfrac{1}{2\lambda} + \dfrac{1}{\lambda}$$ $$var(T_1+T_2+T_3) = \dfrac{1}{9\lambda^2} + \dfrac{1}{4\lambda^2} + \dfrac{1}{\lambda^2}$$
### 6.2.6 Bernoulli and Poisson Processes, and Sums of Random Variables
- Let $N,X_1,X_2,\dots$ be independent r.v.'s, where $N$ takes nonnegtive integer values. Let $Y=X_1+\cdots+X_N$ for positive values of $N$, and let $Y=0$ when $N=0$
    - If $X_i \sim Bern(p)$ and $N \sim Bin(m,q)$, then $Y \sim Bin(m,pq)$
    - If $X_i \sim Bern(p)$ and $N \sim Pois(\lambda)$, then $Y \sim Pois(\lambda p)$
    - If $X_i \sim Geo(p)$ and $N \sim Geo(q)$, then $Y \sim Geo(pq)$
    - If $X_i \sim Exp(\lambda)$ and $N \sim Geo(q)$, then $Y \sim Exp(\lambda q)$
- Consider a Poisson process with paramater $\lambda$, and an independent r.v. $T$, which is exponential with parameter $\nu$. The number of Poisson arrivals $N_T$ during the time interval $[0,T]$ is geometric shifted by 1 to the left
<div align=center>
<img src="https://s1.ax1x.com/2020/04/22/JUkFHg.md.png" width="500" />
</div>

$$K = \#arrivals\ in\ merged\ process\ till\ get\ one\ from\ process\ \nu=N_T+1$$ $$P(arrival\ originating\ from\ process\ \nu)=\dfrac{\nu}{\lambda+\nu}$$ $$K \sim Geo \bigg( \dfrac{\nu}{\lambda+\nu} \bigg),\ p_K(k)=\bigg( \dfrac{\lambda}{\lambda+\nu} \bigg)^{k-1} \bigg( \dfrac{\nu}{\lambda+\nu} \bigg)$$ $$p_{N_T}(n)=p_K(n+1)=\bigg( \dfrac{\lambda}{\lambda+\nu} \bigg)^{n} \bigg( \dfrac{\nu}{\lambda+\nu} \bigg)$$
### 6.2.7 The Random Incidence Paradox
<div align=center>
<img src="https://s1.ax1x.com/2020/04/22/JNq5E8.png" width="500" />
</div>

$$L=(t^*-U)+(V-t^*)$$ $$(t^*-U) \sim Exp(\lambda),\ (V-t^*) \sim Exp(\lambda)$$ $$L \sim Erlang(2, \lambda),\ E[L]=2/\lambda$$
An observer who arrive at an arbitrary time is more likely to fall in a large rather than a small interarrival interval. As a consequence the expected length seen by the observer is higher: $2/\lambda$ compared with the $1/\lambda$ mean of the exponential PDF
### 6.2.8 Poisson vs. Normal Approximations of the Binomial
- $Binomial(n, p)$
    - $p$ fixed, $n \to \infty$: Normal
    - $np$ fixed, $n \to \infty$, $p \to 0$: Poisson
- $Pois(n)$
    - sum of i.i.d. $Pois(1)$, $n \to \infty$: Normal
- In practice (rule of thumb):
    - $p=1/100,n=100$: Poisson
    - $p=1/3,n=100$: Normal
    - $p=1/100,n=10000$: Both



# Chapter 7 Markov Chains
***
## <u>7.1 Discrete-Time Markov Chains</u>
- Checkout counter example:
    - discrete time $n=0,1,\dots$
    - customer arrivals: $Bern(p)$
    - customer service times: $Geo(q)$
    - state $X_n$: number of customers in the queue at time $n$
    <img src="https://s1.ax1x.com/2020/04/23/JaaoLV.md.png" width="500" />
    $Let\ X_0=2,\ then\ X_1=2, X_2=2+1=3,X_3=3,X_4=3-1=2,X_5=2,X_6=2+1-1=2,\dots$
    - Assume no more than 10 customers can be in the queue, the **transition probability graph** is as follows: 
    <img src="https://s1.ax1x.com/2020/04/24/J08deS.md.png" width="500" />
- Discrete-time Markov chains:
    - at each time step $n$, the state of the chain: $X_n$
    - state place (a finite set of possible states): $S=\{1,\dots,m\}$
    - transition probabilities: $p_{ij}=P(X_{n+1}=j|X_n=i),\ i,j \in S$
    - transition probability matrix: 
    $$
    \left[
    \begin{matrix}
    p_{11} & p_{12} & \cdots & p_{1m} \\
    p_{21} & p_{22} & \cdots & p_{2m} \\
    \vdots & \vdots & \vdots & \vdots \\
    p_{m1} & p_{m2} & \cdots & p_{mm}
    \end{matrix}
    \right]
    $$
- Markov Property: the Markov chain is a sequence of r.v.'s $X_0,X_1,X_2,\dots$ that take values in $S$ and which satisfy $$P(X_{n+1}=j|X_n=i,X_{n-1}=i_{n-1},\dots,X_0=i_0)=P(X_{n+1}=j|X_n=i)=p_{ij}$$ for all times $n$, all states $i,j \in S$, and all possible sequences $i_0,\dots,i_{n-1}$ of earlier states
### 7.1.1 The Probability of a Path
- $$P(X_0=i_0,X_1=i_1,\dots,X_n=i_n)=P(X_0=i_0)p_{i_0i_1}p_{i_1i_2} \cdots p_{i_{n-1}i_n}$$
### 7.1.2 $n$-Step Transition Probabilities
- $n$-step transition probability: the probability that the state after $n$ time periods will be $j$, given that the current state is $i$ $$r_{ij}(n)=P(X_n=j|X_0=i)=P(X_{n+s}=j|X_s=i)$$
- Chapman-Kolmogorov Equation: the $n$-step transition probabilities can be generated by the recursive formula $$r_{ij}(n)=\sum_{k=1}^m r_{ik}(n-1)p_{kj},\ for\ n>1\ and\ all\ i,j$$ starting with $$r_{ij}(1)=p_{ij}$$
***
## <u>7.2 Classification of States</u>
- Accessible: a state $j$ is accessible from a state $i$ if for some $n$, $r_{ij}(n)$ is positive
- Let $A(i)$ be the set of states that are accessible from $i$
    - state $i$ is **recurrent** if for every $j$ that is accessible from $i$, $i$ is also accessible from $j$; that is, for all $j$ that belong to $A(i)$ we have that $i$ belongs to $A(j)$
    - state $i$ is **transient** if there is a state $j \in A(i)$ such that $i$ is not accessible from $j$
    - if $i$ is a recurrent state, the set of states $A(i)$ form a **recurrent class**, meaning that states in $A(i)$ are all accessible from each other and no states outside $A(i)$ is accessible from them
    <img src="https://s1.ax1x.com/2020/04/24/J0tR39.png" width="500" />
- Markov Chain Decomposition:
    - A Markov chain can be decomposed into one or more recurrent classes, plus possibly some transient states
    - A recurrent state is accessible from all states in its class, but is not accessible from recurrent states in other classes
    - A transient state is not accessible from any recurrent state
    - At least one, possibly more, recurrent states are accessible from a given transient state
- (a) once the state enters (or starts in) a recurrent class, it stays within that class; since all states in the class are accessible from each other, all states in the class will be visited an infinite number of times
(b) if the initial state is transient, then the state trajectory contains an initial portion consisting of transient states and a final portion consisting of recurrent states from the same class
- Periodicity: consider a recurrent class $R$
    - The class is periodic if its states can be grouped in $d>1$ disjoint subsets $S_1,\dots,S_d$, so that all transitions from $S_k$ lead to $S_{k+1}$ (or to $S_1$ if $k=d$)
    <img src="https://s1.ax1x.com/2020/04/24/J0U5FO.png" width="300" />
    - The class is aperiodic if and only if there exists a time $n$ such that $r_{ij}(n)>0,\ for\ all\ i,j \in R$
***
## <u>7.3 Steady-State Behavior</u>
- Situations that $r_{ij}(n)$ will not converge to steady-state values that are independent of the initial state:
    - Multiple recurrent classes: the limit of $r_{ij}(n)$ must depend on the initial state (the posibility of visitng $j$ in the future depends on whether $j$ is in the same class as the initial state $i$)
    - Simple periodic recurrent class: consider a recurrent class with two states, 1 and 2, such that from 1 we can only go to 2, and from 2 we can only go to 1 ($p_{12}=p_{21}=1$) It can be seen that $r_{ij}(n)$ generically oscillate $$r_{ii}(n)= \begin{cases} 1 &,\ n\ even \\ 0 &,\ n\ odd \end{cases}$$
- Steady-state probability: approximately independent of the original state $X_0=i$ $$\pi_j \approx P(X_n=j),\ when\ n\ is\ large$$
- **Steady-State Convergence Theorem:** consider a Markov chain with a single recurrent class which is aperiodic (and some transient states). Then, the states $j$ associated with $\pi_j$ have the following properties
    - (a) For each $j$, we have $$\lim_{n \to \infty} r_{ij}(n)=\pi_j,\ for\ all\ i$$
    - (b) $\pi_j$ are the unique solution to the system of equations: $$\pi_j = \sum_{k=1}^m \pi_kp_{kj},\ j=1,\dots,m \tag{balance\ equations}$$ $$1=\sum_{k=1}^m \pi_k \tag{normalization\ equation}$$
        - Derivation of balance equations: $$r_{ij}(n) = \sum_{k=1}^m r_{ik}(n-1) p_{kj}$$ $$\lim_{n \to \infty} r_{ij}(n) = \lim_{n \to \infty} \sum_{k=1}^m r_{ik}(n-1) p_{kj}$$ $$\pi_j = \sum_{k=1}^m \pi_k p_{kj}$$
    - (c) We have $$\pi_j=0,\ for\ all\ transient\ states\ j$$ $$\pi_j>0,\ for\ all\ recurrent\ states\ j$$
- $\pi_j$ form a **stationary distribution** of the chain: if the initial state is chosen according to this distribution $$P(X_0=j)=\pi_j,\ j=1,\dots,m$$ $$then,\ P(X_1=j)= \sum_{k=1}^m P(X_0=k)p_{kj} = \sum_{k=1}^m \pi_k p_{kj} = \pi_j$$ $$similarly,\ P(X_n=j) = \pi_j,\ for\ all\ n\ and\ j$$
### 7.3.1 Long-Term Frequency Interpretations
- Balance equations interpreted by frequency: $$\pi_j=\sum_{k=1}^m \pi_k p _{kj}$$
    - (Long-run) frequency of being in $j$: $$\pi_j=\lim_{n \to \infty} \dfrac{\nu_{ij}(n)}{n}$$ where $\nu_{ij}(n)$ is the expected value of the number of visits to state $j$ within the first $n$ transitions, starting from state $i$
    - frequency of transitions $k \to j$: $$\pi_k p_{kj} = \lim_{n \to \infty} \dfrac{q_{kj}(n)}{n}$$ where $q_{kj}(n)$ is the expected number of such transitions that takes the state from $k$ to $j$
    - frequency of transitions into $j$: $$\sum\limits_{k} \pi_k p_{kj}$$
### 7.3.2 Birth-Death Processes
<img src="https://s1.ax1x.com/2020/04/24/JDj2uT.png" width="500" />

- Local balance equations：the expected frequency of transitions from $i$ to $i+1$ must be equal to the expected frequency of transitions from $i+1$ to $i$ $$\pi_i b_i = \pi_{i+1} d_{i+1}$$ $$\begin{cases} \pi_i = \pi_0 \dfrac{b_0b_1 \cdots b_{i-1}}{d_1d_2 \cdots d_i} \\ \sum\limits_{i} \pi_i = 1 \end{cases}$$
- Special case: $b_i = p$ and $d_i = q$ for all $i$
$Let\ \rho = p/q,\ \pi_{i+1}=\pi_i \rho$
$\pi_i = \pi_0 \rho^i,\ i=0,1,\dots,m$
$\sum\limits_i \pi_i = \pi_0 (1+\rho+\rho^2+\cdots+\rho^m)=1$
(1) assume $p=q$: symmetric random walk
$\pi_i = \pi_0,\ i=0, \dots, m$
$\pi_i = \pi_0 = \dfrac{1}{m+1}$ equally likely to be at any states
(2) assume $p<q$ and $m \to \infty$:
$\pi_0 = \dfrac{1}{\sum\limits_{i=0}^{\infty} \rho^i} = \dfrac{1}{\dfrac{1}{1-\rho}} = 1-\rho$
$\pi_i = (1-\rho) \rho^i$ shifted geometric distribution, $E[X_n]=\dfrac{\rho}{1-\rho}$
***
## <u>7.4 Absorption Probabilities and Expected Time to Absorption</u>
- Absorbing state: recurrent state $k$ with $p_{kk}=1$
- Absorption probability: $$a_i = P(X_n\ eventually\ becomes\ equal\ to\ the\ absorbing\ state\ s|X_0=i)$$
- Absorption probability equations: $$\begin{cases} a_s=1 \\ a_i=0 &,\ for\ all\ absorbing\ i \neq s \\ a_i=\sum\limits_{j=1}^m p_{ij}a_j &,\ for\ all\ transient\ i \end{cases}$$
### 7.4.1 Expected Time to Absorption
- Expected time to absorption: $$\begin{aligned} \mu_i &= E[number\ of\ transitions\ until\ absorption,\ starting\ from\ i] \\ &= E[min\{n \geq 0\ such\ that\ X_n\ is\ recurrent\}|X_0=i] \end{aligned}$$
- Equations for the expected time to absorption: $$\begin{cases} \mu_i=0 &,\ for\ all\ recurrent\ states\ i \\ \mu_i=1+\sum\limits_{j=1}^m p_{ij}\mu_j &,\ for\ all\ transient\ states\ i \end{cases}$$
### 7.4.2 Mean First Passage and Recurrence Times
- Mean first passage time from $i$ to $s$: $$\begin{aligned} t_i &= E[number\ of\ transitions\ to\ reach\ s\ for\ the\ first\ time,\ starting\ from\ i] \\ &= E[min\{n \geq 0\ such\ that\ X_n=s\}|X_0=i] \end{aligned}$$
- Equations for the mean first passage time: $$\begin{cases} t_s=0 \\ t_i=1+\sum\limits_{j} p_{ij}t_j &,\ for\ all\ i \neq s \end{cases}$$
Example: what happens after reaching to $s$ is not in our consideration; think of $s$ as an absorbing state
[![JyRdgJ.png](https://s1.ax1x.com/2020/04/25/JyRdgJ.png)](https://imgchr.com/i/JyRdgJ)
- Mean recurrence time of $s$: $$\begin{aligned} t_s^* &= E[number\ of\ transitions\ up\ to\ the\ first\ return\ to\ s,\ starting\ from\ s] \\ &= E[min\{n \geq 1\ such\ that\ X_n=s\}|X_0=s] \end{aligned}$$
- Solution to the mean recurrence time: $$t_s^* = 1 + \sum_{j}p_{sj}t_j$$
***
## <u>7.5 Continuous-Time Markov Chains</u>
- Assumptions:
    - If the current state is $i$, the time until the next transition is exponentially distributed with a given parameter $\nu_i$, independent of the past history of the process and of the next state
    - If the current state is $i$, the next state will be $j$ with a given probability $p_{ij}$, independent of the past history of the process and of the time until the next transition
- Transition rate out of state $i$: $\nu_i$ (the average number of transitions out of state $i$, per unit time spent at state $i$)
- Transition rate from $i$ to $j$: $q_{ij}$ (the average number of transitions from $i$ to $j$, per unit time spent at state $i$, since only a fraction $p_{ij}$ of the transitions out of state $i$ will lead to state $j$) $$q_{ij} = \nu_i p_{ij}$$
- Obtain the transition rates and probabilities: $$\nu_i = \sum_{j=1}^m q_{ij}$$ $$p_{ij} = \dfrac{q_{ij}}{\nu_i}$$
- Ignore self-transitions because of the memorylessness of exponential distribution (the remaining time until next transition is the same irrespective of whether a self-transition just occurred or not) $$p_{ii}=q_{ii}=0,\ for\ all\ i$$
### 7.5.1 Approximation by a Discrete-Time Markov Chain
- Let $\delta$ be a small positive time interval and consider the discrete-time Markov chain $Z_n$ that is obtained by observing $X(t)$ every $\delta$ time units: $$Z_n = X(n\delta),\ n=0,1,\dots$$ Given that $Z_n=i$, there is a probability approximately equal to $\nu_i\delta$ that there is a transition between times $n\delta$ and $(n+1)\delta$, and in that case there is a further probability $p_{ij}$ that the next state is $j$: $$\bar{p}_{ij} = P(Z_{n+1}=j|Z_n=i) = \nu_i p_{ij} \delta + o(\delta) = q_{ij}\delta + o(\delta),\ if\ j \neq i$$ $$\bar{p}_{ii} = P(Z_{n+1}=i|Z_n=i) = 1 - \sum_{j \neq i} \bar{p}_{ij} + o(\delta)$$
- Given the current state $i$ of a continuous-time Markov Chain, and for any $j \neq i$, the state $\delta$ time units later is equal to $j$ with probability $$q_{ij}\delta+o(\delta)$$ independent of the past history of the process
### 7.5.2 Steady-State Behavior
- Consider a continuous-time Markov chain with a single recurrent class. Then, the state $j$ are associated with steady-state probabilities $\pi_j$ that have the following properties:
    - (a) For each $j$, we have $$\lim_{t \to \infty} P(X(t)=j|X(0)=i)=\pi_j,\ for\ all\ i$$
    - (b) $\pi_j$ are the unique solution to the system of equations: $$\pi_j \sum_{k \neq j} q_{jk} = \sum_{\pi_k} q_{kj} \tag{balance equations}$$ $$\sum_{k=1}^m \pi_k = 1 \tag{normalization equation}$$
        - Derivation of the balance equations:
        $$\begin{aligned} \pi_j &= \sum_{j=1}^m \pi_k \bar{p}_{kj} \\ &= \pi_j \bar{p}_{jj} + \sum_{k \neq j} \pi_k \bar{p}_{kj} \\ &= \pi_j \bigg( 1 - \delta \sum_{k \neq j} q_{jk} + o(\delta) \bigg) + \sum_{k \neq j} \pi_k (q_{kj}\delta + o(\delta)) \\ \therefore \pi_j \sum_{k \neq j} q_{jk} &= \sum_{\pi_k} q_{kj} \end{aligned}$$
### 7.5.3 Birth-Death Processes
- Local balance euqations: $$\pi_j q_{ji} = \pi_i q_{ij},\ for\ all\ i,j$$



# Chapter 8 Bayesian Statistical Inference
Unknown parameters are viewed as random variables with a single, fully-specified probabilistic model
***
## <u>8.1 Bayesian Inference and the Posterior Distribution</u>
<img src="https://s1.ax1x.com/2020/04/27/JhSGOU.png" width="500" />

- Bayesian Inference:
    - Start with a prior distribution $p_{\Theta}$ or $f_{\Theta}$ for the unknown r.v. $\Theta$
    - Have a model $p_{X|\Theta}$ or $f_{X|\Theta}$ of the observation vector $X$
    - After observing the value $x$ of $X$, we form the posterior distribution of $\Theta$, using the appropriate version of Bayes' rule
- The four versions of Bayes' rule:
    - $\Theta$ discrete, $X$ discrete: $$p_{\Theta|X}(\theta|x) = \dfrac{p_{\Theta}(\theta)p_{X|\Theta}(x|\theta)}{\sum\limits_{\theta'} p_{\Theta}(\theta')p_{X|\Theta}(x|\theta')}$$
    - $\Theta$ discrete, $X$ continuous: $$p_{\Theta|X}(\theta|x) = \dfrac{p_{\Theta}(\theta)f_{X|\Theta}(x|\theta)}{\sum\limits_{\theta'} p_{\Theta}(\theta')f_{X|\Theta}(x|\theta')}$$
    - $\Theta$ continuous, $X$ discrete: $$f_{\Theta|X}(\theta|x) = \dfrac{f_{\Theta}(\theta)p_{X|\Theta}(x|\theta)}{\int f_{\Theta}(\theta')p_{X|\Theta}(x|\theta') d\theta'}$$
    - $\Theta$ continuous, $X$ continuous: $$f_{\Theta|X}(\theta|x) = \dfrac{f_{\Theta}(\theta)f_{X|\Theta}(x|\theta)}{\int f_{\Theta}(\theta')f_{X|\Theta}(x|\theta') d\theta'}$$
***
## <u>8.2 Point Estimation, Hypothesis Testing, and the MAP Rule</u>
- Maximum a Posteriori Probability (MAP) rule: Given the value $x$ of the observation, we select a value of $\theta$, denoted $\hat{\theta}$, that maximizes the posterior distribution $p_{\Theta|X}(\theta|x)$ or $f_{\Theta|X}(\theta|x)$ $$\begin{aligned} \hat{\theta} &= \arg \max_{\theta} p_{\Theta|X}(\theta|x),\ \Theta\ discrete \\ \hat{\theta} &= \arg \max_{\theta} f_{\Theta|X}(\theta|x),\ \Theta\ continuous \end{aligned}$$
    - Since the denominator is the same for all $\theta$ and depends only on the value of $x$ of the observation, to maximize the posterior, we only need to choose a value of $\theta$ that maximizes the **numerator**: $$p_{\Theta}(\theta)p_{X|\Theta}(x|\theta)$$ $$p_{\Theta}(\theta)f_{X|\Theta}(x|\theta)$$ $$f_{\Theta}(\theta)p_{X|\Theta}(x|\theta)$$ $$f_{\Theta}(\theta)f_{X|\Theta}(x|\theta)$$
    - If $\Theta$ takes only a finite number of values, the MAP rule minimizes the probability of selecting an incorrect hypothesis. This is true for both the unconditional probability of error and the conditional one, given any observation value $x$
### 8.2.1 Point Estimation
- An estimator is a r.v. of the form $\hat{\Theta}=g(X)$, for some function $g$; different choices of $g$ correspond to different estimators
- An estimate is the value $\hat{\theta}$ of an estimator, as determined by the realized value $x$ of the observation $X$
- Once the value $x$ of $X$ is observed, the MAP estimator, sets the estimate $\hat{\theta}$ to a value that maximizes the posterior distribution over all possible value of $\theta$
    - If the posterior distribution of $\Theta$ is symmetric around its (conditional) mean and unimodal, the maximum occurs at the mean. Then, the MAP estimator coincides with the LMS estimator (i.e., normal)
    - If $\Theta$ is continuous, the actual evaluation of the MAP estimate $\hat{\theta}$ can sometimes be carried out analytically; for example. if there are no constraints on $\theta$, by setting zero the derivative of $f_{\Theta|X}(\theta|x)$, or of $\log{f_{\Theta|X}(\theta|x)}$, and solving for $\theta$
- Once the value $x$ of $X$ is observed, the Conditional Expectation (LMS) estimator sets the estimate $\hat{\theta}$ to $E[\Theta|X=x]$
### 8.2.2 Hypothesis Testing
- The MAP rule for hypothesis testing:
    - Given the observation value $x$, the MAP rule selects a hypothesis $H_i$ for which the value of the posterior probability $P(\Theta=\theta_i|X=x)$ is largest
    - Equivalently, it selects a hypothesis $H_i$ for which $p_{\Theta}(\theta_i)p_{X|\Theta}(x|\theta_i)$ or $p_{\Theta}(\theta_i)f_{X|\Theta}(x|\theta_i)$ is largest
    - The MAP rule minimizes the probability of selecting an incorrect hypothesis for any observation value $x$, as well as the probability of error over all decision rules
- If $g_{MAP}(x)$ is the hypothesis selected by the MAP rule when $X=x$, the probability of correct decision is $$P(\Theta=g_{MAP}(x)|X=x)$$
- If $S_i$ is the set of all $x$ such that the MAP rule selects hypothesis $H_i$, the overall probability of correct decision is $$P(\Theta=g_{MAP}(X)) = \sum_i P(\Theta=\theta_i, X \in S_i)$$ and the corresponding probability of error is $$\sum_i P(\Theta \neq \theta_i, X \in S_i)$$
***
## <u>8.3 Bayesian Least Mean Squares (LMS) Estimation</u>
- LMS: minimize Mean Squared Error (MSE)
    - In the absence of any observations, $E[(\Theta-\hat{\theta})^2]$ is minimized when $\hat{\theta}=E[\Theta]$ $$E \Big[ \big( \Theta-E[\Theta] \big)^2 \Big] \leq E[(\Theta-\hat{\theta})^2],\ for\ all\ \hat{\theta}$$
    <img src="https://s1.ax1x.com/2020/05/08/YuVJjU.png" width="300" />
    - For any given value $x$ of $X$, $E[(\Theta-\hat{\theta})^2|X=x]$ is minimized when $\hat{\theta}=E[\Theta|X=x]$ $$E \Big[ (\Theta-E[\Theta|X=x])^2 \Big| X=x \Big] \leq E[(\Theta-\hat{\theta})^2|X=x],\ for\ all\ \hat{\theta}$$
    - Out of all estimators $g(X)$ of $\Theta$ based on $X$, the mean squared estimation error $E\Big[ \big( \Theta - g(X) \big)^2 \Big]$ is minimized when $g(X)=E[\Theta|X]$ $$E \Big[ \big( \Theta-E[\Theta|X] \big)^2 \Big] \leq E \Big[ \big( \Theta-g(X) \big)^2 \Big],\ for\ all\ estimators\ g(X)$$
- LMS Performance Evaluation:
    - Expected performance once we have a measurement: $$MSE = E \Big[ (\Theta-E[\Theta|X=x])^2 \Big| X=x \Big] = var(\Theta|X=x)$$
    - Expected performance of the estimator: $$MSE = E \Big[ \big( \Theta-E[\Theta|X] \big)^2 \Big] = E \big[ var(\Theta|X) \big]$$
### 8.3.1 Some Properties of the Estimation Error
$$\hat{\Theta} = E[\Theta|X],\ \tilde{\Theta} = \hat{\Theta} - \Theta$$
- Properties of estimation error:
    - The estimation error $\tilde{\Theta}$ is unbiased, it has zero unconditional and conditional mean $$E[\tilde{\Theta}]=0,\ E[\tilde{\Theta}|X=x]=0,\ for\ all\ x$$
    - The estimation error $\tilde{\Theta}$ is uncorrelated with the estimate $\hat{\Theta}$ $$cov(\tilde{\Theta},\hat{\Theta})=0$$
    - The variance of $\Theta$ can be decomposed as $$var(\Theta) = var(\hat{\Theta}) + var(\tilde{\Theta})$$
### 8.3.2 The Case of Multiple Observations and Multiple Parameters
- Multiple observations: $$E \Big[ \big( \Theta - E[\Theta|X_1,\dots,X_n] \big)^2 \Big] \leq E \Big[ \big( \Theta - g(X_1,\dots,X_n) \big)^2 \Big],\ for\ all\ g(X_1,\dots,X_n)$$
- Multiple parameters: find $\hat{\Theta}_1, \dots, \hat{\Theta}_m$ to minimize $$E \big[ (\Theta_1 - \hat{\Theta}_1)^2 \big] + \cdots + E \big[ (\Theta_m - \hat{\Theta}_m)^2 \big]$$ essentially dealing with $m$ decoupled estimation problems, one for each unknown parameter $\Theta_i$, yielding $\hat{\Theta}_i = E[\Theta_i | X_1,\dots,X_n],\ for\ all\ i$
***
## <u>8.4 Bayesian Linear Least Mean Squares (LLMS) Estimation</u>
### 8.4.1 LLMS Estimation Based on a Single Observation
- The LLMS estimator $\hat{\Theta}$ of $\Theta$ based on $X$ is $$\hat{\Theta} = E[\Theta] + \dfrac{cov(\Theta,X)}{var(X)}(X-E[X]) = E[\Theta] + \rho \dfrac{\sigma_{\Theta}}{\sigma_X}(X-E[X])$$
Derivation: let $\hat{\Theta} = aX+b$ that minimizes the MSE $E[(\Theta-aX-b)^2]$
First, choosing a constant $b$ to estimate the r.v. $\Theta-aX$. The best choice is $$b = E[\Theta - aX] = E[\Theta] - aE[X]$$ with this choice of $b$, it remains to minimize, with respect to $a$ that $$\begin{aligned} E \big[ ( \Theta - aX - E[\Theta - aX] )^2 \big] &= var(\Theta-aX) \\ &= var(\Theta) + a^2 var(X) - 2 cov(\Theta, aX) \\ &= \sigma_{\Theta}^2 + a^2 \sigma_X^2 - 2a \cdot cov(\Theta, X) \end{aligned}$$ to minimize $var(\Theta-aX)$, we set its derivative to zero and solve for $a$ $$\begin{aligned} \dfrac{d}{da}var(\Theta-aX) &= 0 \\ 2\sigma_X^2 a - 2cov(\Theta,X) &= 0 \\ a = \dfrac{cov(\Theta,X)}{\sigma_X^2} &= \rho \dfrac{\sigma_{\Theta}}{\sigma_X} \end{aligned}$$

- The resulting MSE is equal to $$(1-\rho^2)\sigma_{\Theta}^2$$
Derivation: $$\begin{aligned} E[(\Theta-\hat{\Theta})^2] &= var(\Theta - aX) \\ &= \sigma_{\Theta}^2 + a^2 \sigma_X^2 - 2a \cdot cov(\Theta, X) \\ &= \sigma_{\Theta}^2 + \rho^2 \dfrac{\sigma_{\Theta}^2}{\sigma_X^2} \sigma_X^2 - 2 \rho \dfrac{\sigma_{\Theta}}{\sigma_X} \rho \sigma_{\Theta}\sigma_X \\ &= (1-\rho^2)\sigma_{\Theta}^2 \end{aligned}$$
- The estimator starts with the baseline estimate $E[\Theta]$ for $\Theta$, which is then adjusted by taking into account the value of $X-E[X]$. For example, when $X$ is larger than its mean, the positive correlation between $X$ and $\Theta$ suggests that $\Theta$ is expected to be larger than its mean. Accordingly, teh resulting estimate is set to a value larger than $E[\Theta]$.
- When $|\rho|$ is close to $1$, the two r.v.'s are highly correlated, and knowing $X$ allows us to accurately estimate $\Theta$, resulting in a small MSE
- The properties of the estimation error presented in LMS hold when $\hat{\Theta}$ is LLMS estimator
### 8.4.2 The Case of Multiple Observations and Multiple Parameters
- Multiple parameters: $$E \big[ (\Theta_1 - \hat{\Theta}_1)^2 \big] + \cdots + E \big[ (\Theta_m - \hat{\Theta}_m)^2 \big]$$ find a linear estimator $\hat{\Theta}_i$ that minimizes $E[(\Theta_i - \hat{\Theta}_i)^2]$, so that we are essentially dealing with $m$ decoupled linear estimation problems, one for each unknown parameter
- In the case where there are multiple observations with a certain independence property, let $\Theta$ be a r.v. with mean $\mu$ and variance $\sigma_0^2$, and let $X_1, \dots, X_n$ be observations of the form $$X_i = \Theta + W_i$$ where $W_i$ are the r.v.'s with mean $0$ and variance $\sigma_i^2$, which represent observation errors. Under the assumption that $\Theta$ and $W_1,\dots,W_n$ are uncorrelated, the LLMS estimator of $\Theta$, based on the observations $X_1,\dots,X_n$, is $$\hat{\Theta} = \dfrac{\mu / \sigma_0^2 + \sum\limits_{i=1}^n X_i/\sigma_i^2}{\sum\limits_{i=0}^n 1/\sigma_i^2}$$
### 8.4.3 Linear Estimation and Normal Models
- The LLMS estimator is generally different from and inferior to the LMS estiamtor $E[\Theta|X_1,\dots,X_n]$. However, if the LMS estimator happens to be linear in the observations $X_1,\dots,X_n$, then it is also the LLMS estimator
    - Example: the estimation of a normal r.v. $\Theta$ on the basis of observations $X_i = \Theta + W_i$, where $W_i$ are independent zero mean normal noise terms, independent of $\Theta$
    - More generally, if $\Theta,X_1,\dots,X_n$ are all linear functions of a collection of independent normal random variables, then the LMS and the LLMS estimators coincide; they also coincide with the MAP estimator
### 8.4.4 The Choice of Variables in Linear Estimation
- Estimation based on $h(X)$ versus $X$:
    - LMS: $E[\Theta|h(X)] = E[\Theta|X]$
    - LLMS: different, estimator $\hat{\Theta}=ah(X)+b$ versus $\hat{\Theta}=aX+b$
    for example, suppose that $\Theta$ is the unknown variance of some distribution and $X_1,\dots,X_n$ represent independent random variables drawn from that distribution; then it would be unreasonable to expect that a good estimator of $\Theta$ can be obtained with a linear function of $X_1,\dots,X_n$
***
## <u>8.5 Summary</u>
&emsp; | Estimator<br>$\hat{\Theta} = g(X)$ | Characteristics
- | - | - 
**MAP** | $$\hat{\theta} = \arg\max_{\theta} p_{\Theta \vert X}(\theta \vert x),\ \Theta\ discrete$$ $$\hat{\theta} = \arg\max_{\theta} f_{\Theta \vert X}(\theta \vert x),\ \Theta\ continuous$$ | minimize the unconditional probability of error and the conditional one, given any observation value $x$
**LMS** | $$\hat{\Theta} = E[\Theta \vert X]$$ | minimize $MSE = E[(\Theta-E[\Theta \vert X])^2] = var(\Theta \vert X)$
**LLMS** | $$\begin{aligned} \hat{\Theta} &= E[\Theta] + \dfrac{cov(\Theta,X)}{var(X)}(X-E[X]) \\ &= E[\Theta] + \rho \dfrac{\sigma_{\Theta}}{\sigma_X}(X-E[X]) \end{aligned}$$ | simple calculation, minimize MSE based on linear function of observation, where $MSE = (1-\rho^2)\sigma_{\Theta}^2$



# Chapter 9 Classical Statistical Inference
Unknown parameters are viewed as constants to be determined. each possible value of the unknown parameter has a separated probabilistic model 
***
## <u>9.1 Classical Parameter Estimation</u>
### 9.1.1 Properties of Estimators
- Let $\hat{\Theta}_n$ be an estimator of an unknown parameter $\theta$, that is, a function of $n$ observations $X_1,\dots,X_n$ whose distribution depends on $\theta$
    - Estimation error: $$\tilde{\Theta}_n = \hat{\Theta}_n - \theta$$
    - Bias of the estimator: $$b_{\theta}(\hat{\Theta}_n) = E[\tilde{\Theta}_n] = E_{\theta}[\hat{\Theta}_n] - \theta$$
    - The expected value, variance, and bias of $\hat{\Theta}_n$ depend on $\theta$, while the estimation error depends in addition on the observations $X_1,\dots,X_n$
    - We call $\hat{\Theta}_n$ unbiased if $E_{\theta}[\hat{\Theta}_n] = \theta$, for every possible value of $\theta$
    - We call $\hat{\Theta}_n$ asymptotically unbiased if $\lim\limits_{n \to \infty} E_{\theta}[\hat{\Theta}_n] = \theta$, for every possible value of $\theta$
    - We call $\hat{\Theta}_n$ consistent if the sequence $\hat{\Theta}_n$ converges to the true value of parameter $\theta$, in probability, for every possible value of $\theta$ (WLLN)
    - Mean Squared Error: $$E[\tilde{\Theta}_n^2] = b^2_{\theta}(\hat{\Theta}_n) + var_{\theta}(\hat{\Theta}_n)$$
### 9.1.2 Maximum Likelihood Estimation (ML)
- Let the vector of observations $X=(X_1,\dots,X_n)$ be described by a joint PMF $p_X(x;\theta)$ whose form depends on an unknown (scalar or vector) parameter $\theta$. Suppose we observe a particular value $x=(x_1,\dots,x_n)$ of $X$. Then, a ML estimate is a value of the parameter that maximizes the numerical function $p_X(x_1,\dots,x_n;\theta)$ over all $\theta$ $$\hat{\theta}_n = \arg\max_{\theta} p_X(x_1,\dots,x_n;\theta),\ X\ discrete$$ $$\hat{\theta}_n = \arg\max_{\theta} f_X(x_1,\dots,x_n;\theta),\ X\ continuous$$ where $p_X(x;\theta)$ or $f_X(x;\theta)$ is called likelihood function, which means the probability that the observed value $x$ can arise when the parameter is equal to $\theta$
- In many applications, the observations $X_i$ are assumed to be independent, then the likelihood function is of the form: $$p_X(x_1,\dots,x_n; \theta) = \prod_{i=1}^n p_{X_i}(x_i;\theta),\ X\ discrete$$ $$f_X(x_1,\dots,x_n; \theta) = \prod_{i=1}^n f_{X_i}(x_i;\theta),\ X\ continuous$$
it is ofte analytically or computationally convenient to maximize its logarithm, called the log-likelihood function: $$\ln{p_X(x_1,\dots,x_n; \theta)} = \sum_{i=1}^n \ln{p_{X_i}(x_i;\theta)},\ X\ discrete$$ $$\ln{f_X(x_1,\dots,x_n; \theta)} = \sum_{i=1}^n \ln{f_{X_i}(x_i;\theta)},\ X\ continuous$$
- ML versus MAP: in Bayesian MAP estimation, the estimate is chosen to maximize the expression $p_{\Theta}(\theta)p_{X|\Theta}(x|\theta)$ over all $\theta$
    - in the case of discrete $\theta$, if we view $p_X(x;\theta)$ as a conditional PMF, ML estimation can be interpreted as MAP estimation with a flat prior (a prior which is the same for all $\theta$, indicating the absence of any useful prior knowledge)
    - in the case of continuous $\theta$ with a bounded range of possible values, ML estimation can be interpreted as MAP estimation with a uniform prior: $f_{\Theta}(\theta) = c$ for all $\theta$ and some constant $c$
- Maximum Likelihood Estimation:
    - We are given the realization $x=(x_1,\dots,x_n)$ of a random vector $X=(X_1,\dots,X_n)$, distributed according to a PMF $p_X(x;\theta)$ or PDF $f_X(x;\theta)$
    - The ML estimate is a value of $\theta$ that maximizes the likelihood function, $p_X(x;\theta)$ or $f_X(x;\theta)$, over all \$theta$
    - The invariance principle: the ML estimate of a one-to-one function $h(\theta)$ of $\theta$ is $h(\hat{\theta}_n)$, where $h(\hat{\theta}_n)$ is the ML estimate of $\theta$
    - When the r.v.'s $X_i$ are i.i.d., and under some mild additional assumptions, each component of the ML estimator is consistent and asymptotically normal
### 9.1.3 Estimation of the Mean and Variance of a Random Variable
- Let the observations $X_1,\dots,X_n$ be i.i.d., with mean $\theta$ and variance $v$ that are unknown
    - the sample mean $$M_n = \dfrac{X_1+\cdots+X_n}{n}$$ is an unbiased estimator of $\theta$, and its $MSE = \dfrac{v}{n}$
    - two variance estimators are $$\bar{S}_n^2 = \dfrac{1}{n} \sum_{i=1}^n (X_i - M_n)^2,\ \hat{S}_n^2 = \dfrac{1}{n-1} \sum_{i=1}^n (X_i - M_n)^2$$
    - the estimator $\bar{S}_n^2$ coincides with the ML estimator if the $X_i$ are normal; it is biased but asymptotically unbiased; the estimator $\hat{S}_n^2$ is unbiased; for large $n$, the two variance estimators essentially coincide
- Example:
    - **Bayesian MAP estimator of the common mean of a normal random variable:**
     Suppose that the observations $X_1,\dots,X_n$ are normal, i.i.d., with an unknown common mean $\theta$ and known variance $v$. If we use a Bayesian approach and assume a normal prior distribution on the parameter $\theta$. For the case where the prior mean of $\theta$ is zero, we arrive at the following estimator $$\hat{\Theta}_n = \dfrac{X_1+\dots+X_n}{n+1}$$ this estimator is biased because $b_{\theta}(\hat{\Theta}_n) = E_{\theta}[\hat{\Theta}_n] - \theta = \dfrac{n \theta}{n+1} - \theta = -\dfrac{\theta}{n+1}$, but is asymptotically unbiased because $\lim\limits_{n \to \infty} b_{\theta}(\hat{\Theta}_n) = 0$
    its variance is $$var(\hat{\Theta}_n) = \dfrac{nv}{(n+1)^2}$$ it is slightly smaller than the variance $\dfrac{v}{n}$ of the sample mean; $var(\hat{\Theta}_n)$ is independent of $\theta$ given known variance $v$; the MSE is equal to $$E_{\theta}[\tilde{\Theta}_n^2] = b^2_{\theta}(\hat{\Theta}_n) + var(\hat{\Theta}_n) = -\dfrac{\theta^2}{(n+1)^2} + \dfrac{nv}{(n+1)^2}$$
    - **Classical ML estimator of the mean and variance of a normal random variable:**
    Estimate the mean $\mu$ and variance $v$ of a normal distribution using $n$ independent observations $X_1,\dots,X_n$. The parameter vector is $\theta = (\mu, v)$. The corresponding likelihood function is $$\begin{aligned} f_X(x;\mu,v) &= \prod_{i=1}^n f_{X_i}(x_i;\mu,v) = \prod_{i=1}^n \dfrac{1}{\sqrt{2\pi v}} e^{-(x_i - \mu)^2 / 2v} \\ &= \dfrac{1}{(2 \pi v)^{n/2}} \cdot exp \bigg\{ -\dfrac{ns_n^2}{2v} \bigg\} \cdot exp \bigg\{ -\dfrac{n(m_n - \mu)^2}{2v} \bigg\} \end{aligned}$$ where $m_n,\ s_n^2$ are the realized value of the random variable $$M_n = \dfrac{1}{n} \sum_{i=1}^n X_i,\ \bar{S}_n^2 = \dfrac{1}{n} \sum_{i=1}^n (X_i-M_n)^2$$ The log-likelihood function is $$\ln{f_X(x;\mu,v)} = -\dfrac{n}{2} \ln{2\pi} - \dfrac{n}{2} \ln{v} - \dfrac{ns_n^2}{2v} - \dfrac{n(m_n - \mu)^2}{2v}$$ $$\begin{cases} \dfrac{\partial}{\partial \mu}\ln{f_X(x;\mu,v)} = -\dfrac{n}{2v}(2\mu - 2m_n) = 0 \\ \dfrac{\partial}{\partial v}\ln{f_X(x;\mu,v)} = -\dfrac{n}{2v^2} \big( v - s_n^2 - (m_n-\mu)^2 \big) = 0 \end{cases} \Longrightarrow \begin{cases} \mu = m_n \\ v = s_n^2 \end{cases}$$ $$\therefore \hat{\theta} = (m_n, s_n^2),\ \hat{\Theta} = (M_n, \bar{S}_n^2)$$
    $$E_{(\mu, v)}[M_n] = \mu,\ E_{(\mu, v)}[X_i^2] = v + \mu^2,\ E_{(\mu, v)}[M_n^2] = \dfrac{v}{n} + \mu^2$$ $$\begin{aligned} E_{(\mu, v)}[\bar{S}_n^2] &= \dfrac{1}{n} E_{(\mu, v)} \bigg[ \sum_{i=1}^n X_i^2 - 2M_n \sum_{i=1}^n X_i + nM_n^2 \bigg] \\ &= E_{(\mu, v)} \bigg[ \dfrac{1}{n}\sum_{i=1}^n X_i^2 - 2M_n^2 + M_n^2 \bigg] \\ &= v + \mu^2 - \dfrac{v}{n} - \mu^2 \\ &= \dfrac{n-1}{n}v \end{aligned}$$ thus, $\bar{S}_n^2$ is not an unbiased estimator of $v$, although it is asymptotically unbiased; we can obtain an unbiased variance estimator after some suitable scaling $$\hat{S}_n^2 = \dfrac{1}{n-1} \sum_{i=1}^n (X_i - M_n)^2 = \dfrac{n}{n-1} \bar{S}_n^2$$
### 9.1.4 Confidence Intervals
- A confidence interval (CI) for a scalar unknown parameter $\theta$ is an interval whose endpoints $\hat{\Theta}_n^{-}$ and $\hat{\Theta}_n^{+}$ bracket $\theta$ with a given high probability
- $\hat{\Theta}_n^{-}$ and $\hat{\Theta}_n^{+}$ are random variables that depend on the observations $X_1,\dots,X_n$
- A $1-\alpha$ CI is one that satisfies $$P_{\theta}(\hat{\Theta}_n^{-} \leq \theta \leq \hat{\Theta}_n^{+}) \geq 1-\alpha$$ for all possible values of $\theta$
- CI for the estimation of the mean:
Suppose that the observations $X_i$ are i.i.d. normal, with unknown mean $\theta$ and known variance $v$. Then, the sample mean estimator $$\hat{\Theta}_n = \dfrac{X_1+\cdots+X_n}{n}$$ is normal (the sum of independent normal r.v.'s is normal), with mean $\theta$ and variance $v/n$. Let $\alpha=0.05$, we have $\Phi(1.96)=0.975=1-\alpha/2$ $$P_{\theta} \bigg( \dfrac{| \hat{\Theta}_n - \theta |}{\sqrt{v/n}} \leq 1.96 \bigg) = 0.95$$ $$P_{\theta} \bigg( \hat{\Theta}_n - 1.96\sqrt{\dfrac{v}{n}} \leq \theta \leq \hat{\Theta}_n + 1.96\sqrt{\dfrac{v}{n}} \bigg) = 0.95$$
### 9.1.5 Confidence Intervals Based on Estimator Variance Approximations
- Suppose that the observations $X_i$ are i.i.d. with mean $\theta$ and variance $v$ that are unknown:
estimate $\theta$ with the sample mean $$\hat{\Theta}_n = \dfrac{X_1+\cdots+X_n}{n}$$ estimate $v$ with the unbiased estimator $$\hat{S}_n^2 = \dfrac{1}{n-1} \sum_{i=1}^n (X_i-\hat{\Theta}_n)^2$$ estimate the variance $v/n$ of the sample mean by $\hat{S}_n^2/n$ then for a given $\alpha$, we may use these estimates and the CLT to construct an approximate $1-\alpha$ confidence interval $$\bigg[ \hat{\Theta}_n - z \dfrac{\hat{S}_n}{\sqrt{n}}, \hat{\Theta}_n + z \dfrac{\hat{S}_n}{\sqrt{n}} \bigg]$$ where $z$ is obtained from the relation $$\Phi(z) = 1 - \dfrac{\alpha}{2}$$ Note that in this approach, there are two different approximations in effect. First, $\hat{\Theta}_n$ is treated as a normal random variable; second, the true variance $v/n$ of $\hat{\Theta}_n$ is replaced by its estimate $\hat{S}_n^2/n$
- Even in the special case where the $X_i$ are normal random variables, the CI produced by the preceding procedure is still approximate. The reason is that $\hat{S}_n^2$ is only an approximation to the true variance $v$ and the random variable $T_n = \dfrac{\hat{\Theta}_n - \theta}{\hat{S}_n/\sqrt{n}}$ is not normal. However, for normal $X_i$ it can be shown that the PDF of $T_n$ does not depend on $\theta$ and $v$. It is called the $t$-distribution with $n-1$ degrees of freedom. Thus, when the $X_i$ are normal (or nearly normal) and $n$ is relatively small, a more accurate CI is $$\bigg[ \hat{\Theta}_n - z \dfrac{\hat{S}_n}{\sqrt{n}}, \hat{\Theta}_n + z \dfrac{\hat{S}_n}{\sqrt{n}} \bigg]$$ where $z$ is obtained from the relation $$\Psi_{n-1}(z) = 1-\dfrac{\alpha}{2}$$
***
## <u>9.2 Linear Regression</u>
- First consider the case of only two variables. To model the relation between two variables, $x$ and $y$, based on a collection of data pairs $(x_i,y_i),\ i=1,\dots,n$, build a linear model of the form $$y \approx \theta_0 + \theta_1 x$$ where $\theta_0$ and $\theta_1$ are unknown parameters to be estimated. Given some estimates $\hat{\theta}_0$ and $\hat{\theta}_1$ of the resulting parameters, the value $y_i$ corresponding to $x_i$ as predicted by the model is $$\hat{y_i} = \hat{\theta}_0 + \hat{\theta}_1 x_i$$ Generally, $\hat{y_i}$ will be different from the given value $y_i$, and the corresponding difference is called the $i$th residual $$\tilde{y_i} = y_i - \hat{y_i}$$ The linear regression approach chooses the parameter estimates $\hat{\theta}_0$ and $\hat{\theta}_1$ that minimizes the sum of the squared residuals over all $\theta_0$ and $\theta_1$ $$\sum_{i=1}^n (y_i - \hat{y}_i)^2 = \sum_{i=1}^n (y_i - \theta_0 - \theta_1 x_i)^2$$ $$\hat{\theta}_1 = \dfrac{\sum\limits_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sum\limits_{i=1}^n (x_i - \bar{x})^2},\ \hat{\theta}_0 = \bar{y} - \hat{\theta}_1 \bar{x}$$ $$where\ \bar{x} = \dfrac{1}{n} \sum_{i=1}^n x_i,\ \bar{y} = \dfrac{1}{n} \sum_{i=1}^n y_i$$
### 9.2.1 Justification of the Least Squares Formulation
- (a) Maximum likelihood (linear model, normal noise):
Assume that the $x_i$ are given numbers (not random variables), and $y_i$ is the realization of a random variable $Y_i$, generated according to a model of the form $$Y_i = \theta_0 + \theta_1 x_i + W_i,\ i=1,\dots,n$$ where the $W_i$ are i.i.d. normal random variables with mean zero and variance $\sigma^2$. It follows that the $Y_i$ are independent normal variables with mean $\theta_0 + \theta_1 x_i$ and variance $\sigma^2$. The likelihood function takes the form $$f_Y(y;\theta) = \prod_{i=1}^n \dfrac{1}{\sigma \sqrt{2\pi}} exp \bigg\{ - \dfrac{(y_i - \theta_0 - \theta_1 x_i)^2}{2\sigma^2} \bigg\}$$ Maximizing the likelihood function is the same as minimizing the sum of the squard residuals. Thus, the linear regression estimates can be viewed as ML estimates within a suitable linear/normal context. In fact, they can be shown to be unbiased estimates in this context.
- (b) Approximate Bayesian LLMS estimation (under a possibly nonlinear model): 
Suppose that both $x_i$ and $y_i$ are realizations of random variables $X_i$ and $Y_i$. The different pairs $(X_i,Y_i)$ are i.i.d., but with unknown joint distribution. Consider an additional independent pair $(X_0,Y_0)$, with the same joint distribution. Suppose we observe $X_0$ and wish to estimate $Y_0$ using a linear estimator of the form $\hat{Y}_0 = \theta_0 + \theta_1 X_0$. The LLMS estimator of $Y_0$ given $X_0$ is $$\hat{Y}_0 = E[Y_0] + \dfrac{cov(X_0,Y_0)}{var(X_0)}(X_0-E[X_0])$$ yielding $$\theta_1 = \dfrac{cov(X_0,Y_0)}{var(X_0)},\ \theta_0 = E[Y_0] - \theta_1 E[X_0]$$ Since the distribution of $(X_0,Y_0)$ is unknown, we use
$\bar{x}$ as an estimator of $E[X_0]$;
$\bar{y}$ as an estimator of $E[Y_0]$;
$\dfrac{1}{n} \sum\limits_{i=1}^n (x_i-\bar{x})(y_i-\bar{y})$ as an estimator of $cov(X_0,Y_0)$;
$\dfrac{1}{n} \sum\limits_{i=1}^n (x_i-\bar{x})^2$ as an estimator of $var(X_0)$;
by substituting these estimates into the above formulas for $\theta_0$ and $\theta_1$, we recover the expressions for the linear regression parameter estimates.
- (c) Approximate Bayesian LMS estimation (linear model): 
Let the pairs $(X_i,Y_i)$ be random and i.i.d. as in (b) above. Assume that the pairs satisfy a linear model of the form $$Y_i = \theta_0 + \theta_1 X_i + W_i$$ where $W_i$ are i.i.d. zero mean noise terms, independent of $X_i$. From LMS property of conditional expectations, $E[Y_0|X_0]$ minimizes the MSE $E[(Y_0 - g(X_0))^2]$, over all functions $g$. Under given assumptions, $E[Y_0|X_0] = \theta_0 + \theta_1 X_0$. Thus, the true parameters $\theta_0$ and $\theta_1$ minimize $$E[(Y_0 - \theta_0^{'} - \theta_1^{'}X_0)^2]$$ over all $\theta_0^{'}$ and $\theta_1^{'}$. By WLLN, this expression is the limit as $n \to \infty$ of $$\dfrac{1}{n} \sum_{i=1}^n (Y_i - \theta_0^{'} - \theta_1^{'}X_i)^2$$ This indicates that we will obtain a good approximation of the minimizers of $E[(Y_0 - \theta_0^{'} - \theta_1^{'}X_0)^2]$ (the true parameters), by minimizing the above expression (with $X_i$ and $Y_i$ replaced by their observed values $x_i$ and $y_i$ respectively), which is the same as minimizing the sum of the squared residuals.
### 9.2.2 Bayesian Linear Regression
- Model:
    - (a) Assume a linear relation $Y_i = \Theta_0 + \Theta_1 x_i + W_i$
    - (b) The $x_i$ are modeled as known constants
    - (c) The random variables $\Theta_0,\Theta_1,W_1,\dots,W_n$ are normal and independent
    - (d) The random variables $\Theta_0$ and $\Theta_1$ have mean zero and variances $\sigma_0^2,sigma_1^2$ respectively
    - (e) The random variables $W_i$ have mean zero and variance $\sigma^2$
- Estimation Formulas:
Given the data pairs $(x_i,y_i)$, the MAP estimates of $\Theta_0$ and $\Theta_1$ are $$\hat{\theta}_1 = \dfrac{\sigma_1^2 \sum\limits_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sigma^2+\sigma_1^2 \sum\limits_{i=1}^n (x_i - \bar{x})^2}$$ $$\hat{\theta}_0 = \dfrac{n\sigma_0^2}{\sigma^2+n\sigma_0^2}(\bar{y}-\hat{\theta}_1\bar{x})$$ $$where\ \bar{x} = \dfrac{1}{n}\sum_{i=1}^n x_i,\ \bar{y} = \dfrac{1}{n}\sum_{i=1}^n y_i$$
    - If $\sigma^2$ is very large compared to $\sigma_0^2$ and $\sigma_1^2$, we obtain $\theta_0 \approx 0$ and $\theta_1 \approx 0$. What is happening here is that the observations are too noisy and are essentially ignored, so that the estimates become the same as the prior means, which we assumed to be zero.
    - If we let the prior variances $\sigma_0^2$ and $\sigma_1^2$ increase to infinity, we are indicating the absence of any useful prior information on $\Theta_0$ and $\Theta_1$. In this case, the MAP estimates become independent of $\sigma^2$, and they agree with the classical linear regression formulas.
    - Suppose, for simplicity, that $\bar{x}=0$. When estimating $\Theta_1$, the values of $y_i$ of the observations $Y_i$ are weighted in proportion to the associated values $x_i$. When $x_i$ is large, the contribution of $\Theta_1 x_i$ to $Y_i$ is relatively large, and therefore $Y_i$ contains useful information on $\Theta_1$. Conversely, if $x_i$ is zero, teh observation $Y_i$ is independent of $\Theta_1$ and can be ignored.
    - The estimates $\hat{\theta}_0$ and $\hat{\theta}_1$ are linear functions of the $y_i$, but not of the $x_i$. Recall that the $x_i$ are treated as exogenous, non-random quantities, whereas the $y_i$ are observed values of the random variables $Y_i$. Thus the MAP estimators $\hat{\Theta}_0$ and $\hat{\Theta}_1$ are linear estimators. In view of normality assumptions, the estimators are also Bayesian LLMS estimators as well as LMS estimators.
### 9.2.3 Multiple Linear Regression
- $$y \approx \theta_0 + \sum_{j=1}^m \theta_j h_j(x)$$ where the $h_j$ are functions that capture the general form of the anticipated dependence of $y$ on $x$. We may then obtain parameters $\hat{\theta}_0,\hat{\theta}_1,\dots,\hat{\theta}_m$ by minimizing over $\theta_0, \theta_1, \dots, \theta_m$ the expression $$\sum_{i=1}^n \bigg( y_i - \theta_0 - \sum_{j=1}^m \theta_j h_j(x_i) \bigg)^2$$ The minimization problem is known to admit closed form as well as efficient numerical solutions.
### 9.2.4 Nonlinear Regression
- $$y \approx h(x;\theta)$$ where $h$ is a given function and $\theta$ is a parameter to be estimated. Given data pairs $(x_i,y_i),\ i=1,\dots,n$, we seek a value of $\theta$ that minimizes the sum of the squared residuals $$\sum_{i=1}^n \big( y_i - h(x_i;\theta) \big)^2$$ Unlike linear regression, this minimization problem does not admit a closed form solution. Similar to linear regression, nonlinear least squares can be motivated as ML estimation with a model of the form $$Y_i = h(x_i;\theta) + W_i$$ where the $W_i$ are i.i.d. normal random variables with zero mean and $\sigma^2$ variance. The likelihood function takes the form $$f_Y(y;\theta) = \prod_{i=1}^n \dfrac{1}{\sigma \sqrt{2\pi}} exp \bigg\{ -\dfrac{\big( y_i-h(x_i;\theta) \big)^2}{2\sigma^2} \bigg\}$$ Maximizing the likelihood function is the same as minimizing the sum of the squared residuals.
### 9.2.5 Practical Considerations
- Heteroscedasticity: 
The motivation of linear regression as ML estimation in the presence of normal noise terms $W_i$ contains the assumption that the variance of $W_i$ is the same for all $i$. Quite often, however, the variance of $W_i$ varies substantially over the data pairs. For example, the variance of $W_i$ may be strongly affected by the value of $x_i$. In this case, a few noise terms with large variance may end up having an undue influence on the parameter estimates. An appropriate remedy is to consider a weighted least squares criterion of the form $\sum\limits_{i=1}^n \alpha_i(y_i - \theta_0 - \theta_1 x_i)^2$, where the weights $\alpha_i$ are smaller for those $i$ for which the variance of $W_i$ is large.
- Nonlinearity:
Often a variable $x$ can explain the values of a variable $y$, but the effect is nonlinear. A regression model based on data pairs of the form $(h(x_i),y_i)$ may be more appropriate, with a suitably chosen function $h$.
- Multicollinearity:
Suppose that we use two explanatory variabels $x$ and $z$ in a model that predicts another variable $y$. If the two variables $x$ and $z$ bear a strong relation, the estimation procedure may be unable to distinguish reliably the relative effects of each explanatory variable.
- Overfitting:
Multiple regression with a large number of explanatory variables and a corresponding large number of parameters to be estimated runs the danger of producing a model that fits the data well, but is otherwise useless. For example, suppose that a linear model is valid but we choose to fit 10 given data pairs with a polynomial of degree 9. The resulting polynomial model will provide a perfect fit to the data, but will nevertheless be incorrect. As a rule of thumb, there should be at least five times (preferably ten times) more data points than there are parameters to be estimated.
- Causality:
The discovery of a linear relation between two variables $x$ and $y$ should not be mistaken for a discovery of a causal relation. A tight fit may be due to the fact that variable $x$ has a causal effect on $y$, but may be equally due to a causal effect of $y$ on $x$. Alternatively, there may be some external effect, described by yet another variable $z$, that affects both $x$ and $y$ in similar ways.
***
## <u>9.3 Binary Hypothesis Testing</u>
<img src="https://s1.ax1x.com/2020/05/13/YaOpCj.png" width="500" />

- Hypotheses:
    - $H_0$: null hypothesis
    - $H_1$: alternative hypothesis
- Type of Errors:
    - Type I error (false rejection): $$\alpha(R) = P(X \in R; H_0)$$
    - Type II error (false acceptance): $$\beta(R) = P(X \notin R; H_1)$$
- Analogy with Bayesian hypothesis testing involving two hypothesis $\Theta=\theta_0$ and $\Theta=\theta_1$:
    - The overall probability of error is minimized by using the MAP rule: given the observed value $x$ of $X$, declare $\Theta=\theta_1$ to be true if $$p_{\Theta}(\theta_0)p_{X|\Theta}(x|\theta_0) < p_{\Theta}(\theta_1)p_{X|\Theta}(x|\theta_1)$$
    - This decision rule can be rewritten as follows: define the likelihood ratio $L(x)$ by $$L(x) = \dfrac{p_{X|\Theta}(x|\theta_1)}{p_{X|\Theta}(x|\theta_0)}$$ and declare $\Theta=\theta_1$ to be true if the realized value $x$ of the observation vector $X$ satisfies $$L(x) > \xi$$ where the critical value $\xi$ is $$\xi = \dfrac{p_{\Theta}(\theta_0)}{p_{\Theta}(\theta_1)}$$
    - Motivated by the preceding form of the MAP rule, consider rejection regions of the form $$R = \{ x | L(x) > \xi \}$$ where the likelihood ratio $L(x)$ is defined similar to the Bayesian case $$L(x) = \dfrac{p_X(x;H_1)}{p_X(x;H_0},\ or\ L(x) = \dfrac{f_X(x;H_1)}{f_X(x;H_0}$$ The critical value $\xi$ remains free to be chosen on the basis of other considerations. The special case where $\xi = 1$ corresponds to the ML rule.
- Choosing $\xi$ trades off the probabilities of the two types of errors. As $\xi$ increases, the rejection region becomes smaller. As a result, the false rejection probility $\alpha(R)$ decreases, while the false acceptance probability $\beta(R)$ increases. Because of the trade off, there is no single best way of choosing the critical value.
<img src="https://s1.ax1x.com/2020/05/13/YdAgxK.png" width="500" />
The most popular approach is **Likelihood Ratio Test (LRT)**
    - Start with a target value $\alpha$ for the false rejection probability
    - Choose a value for $\xi$ such that the false rejection probability is equal to $\alpha$: $$P(L(X)>\xi ; H_0) = \alpha$$
    - Once the value $x$ of $X$ is observed, reject $H_0$ if $L(x) > \xi$

    Typical choices for $\alpha$ are $\alpha=0.1,\ \alpha=0.05,\ or\ \alpha=0.01$, depending on the degree of undesirability of false rejection. To be able to apply the LRT to a given problem, the following are required:
    - (a) $L(x)$ for any given observation value $x$ must be able to compute
    - (b) We must either have a closed form expression for the distribution of $L(X)$ or of a related random variable such as $\ln{L(X)}$ or we must be able to approximate it analytically, computationally or through simulation; this is needed to determine the critical value $\xi$ that corresponds to a given false rejection probability $\alpha$
When $L(X)$ is a continuous random variable, the probability $P(L(X)>\xi;H_0)$ moves continuously from 1 to 0 as $\xi$ increases. Thus, we can find a value of $\xi$ for which the requirement $P(L(X)>\xi ; H_0) = \alpha$ is satisfied. However, if $L(X)$ is a discrete random variable, it may be impossible to satisfy the equality $P(L(X)>\xi ; H_0) = \alpha$ exactly. In such cases, there are several possibilities:
    - (a) Strive for approximate equality
    - (b) Choose the smallest value of $\xi$ that satisfies $P(L(X)>\xi ; H_0) \leq \alpha$
    - (c) Use an exogenous source of randomness to choose between two alternative candidate critical values. (randomized likelihood ratio test)
- For a given false rejection probability, the LRT offers the smallest possible false acceptance probability:
Neyman-Pearson Lemma
Consider a particular choice of $\xi$ in the LRT, which results in error probabilities $$P(L(X)>\xi;H_0) = \alpha,\ P(L(X) \leq \xi;H_1) = \beta$$ Suppose that some other test, with rejection region $R$, achieves a smaller or equal false rejection probability: $$P(X \in R;H_0) \leq \alpha$$ Then, $$P(X \notin R;H_1) \geq \beta$$ with strict inequality $P(X \notin R;H_1) > \beta$ when $P(X \in R;H_0) < \alpha$
<img src="https://s1.ax1x.com/2020/05/13/Yd897q.png" width="500" />
The Neyman-Pearson Lemma states that all pairs $(\alpha(\xi),\beta(\xi))$ corresponding to LRTs lie on the efficient frontier
***

## <u>9.4 Significance Testing</u>
- Restrict the scope of discussion to situations with the following characteristics:
    - (a) Parametric models: Assume that the observations $X_1,\dots,X_n$ have a distribution governed by a joint PMF/PDF, which is completely determined by an unknown parameter $\theta$ (scalar or vector), belonging to a given set $\mathcal{M}$ of possible parameters
    - (b) Simple null hypothesis: The null hypothesis asserts that the true value of $\theta$ is equal to a given element $\theta_0$ of $\mathcal{M}$
    - (c) Alternative hypothesis: The alternative hypothesis $H_1$ is just the statement that $H_0$ is not true, i.e., that $\theta \neq \theta_0$
### 9.4.1 The General Approach
- Significance Testing Methodology:
A statistical test of a hypothesis $"H_0: \theta = \theta^*"$ is to be performed, based on the observations $X_1,\dots,X_n$
    - Before the data are observed:
    (a) Choose a **statistic** $S$, that is, a scalar random variable that will summarize the data to be obtained. Mathematically, this involves the choice of a function $h$: $\mathcal{R}^n \to \mathcal{R}$ resulting in the statistics $S=h(X_1,\dots,X_n)$
    (b) Determine the **shape of the rejection region** by specifying the set of values of $S$ for which $H_0$ will be rejected as a function of a yet undetermined critical value $\xi$
    (c) Choose the **significance level**, i.e., the desired probability $\alpha$ of a false rejection of $H_0$
    (d) Choose the **critical value** $\xi$ so that the probability of false rejection is equal (or approximately equal) to $\alpha$; tt this point, the rejection region is completely determined
    <img src="https://s1.ax1x.com/2020/05/14/Y0MbQJ.png" width="500" />
    - Once the values $x_1,\dots,x_n$ of $X_1,\dots,X_n$ are observed:
    (i) Calculate the value $s=h(x_1,\dots,x_n)$ of the statistics $S$
    (ii) Reject the hypothesis $H_0$ if $s$ belongs to the rejection region
- Quite often, statisticians skip step (c) and (d) and calculate the realized value $s$ of $S$; determine and report an associated $p$-value $$p-value = \min \{ \alpha | H_0\ would\ be\ rejected\ at\ the\ \alpha\ significance\ level \}$$
### 9.4.2 Generalized Likelihood Ratio and Goodness of Fit Tests
- Generalized likelihood ratio test: "is there a model compatible with $H_1$ that provides a better explanation for the observed data than that provided by the model corresponding to $H_0$"
    - (a) Estimate a model by ML, i.e., determine a parameter vector $\hat{\theta} = (\hat{\theta}_1,\dots,\hat{\theta}_m)$ that maximizes the likelihood function $p_X(x;\theta)$ over all vectors $\theta$
    - (b) Carry out a LRT that compares the likelihood $p_X(x;\theta^*)$ under $H_0$ to the likelihood $p_X(x;\hat{\theta})$ corresponding to the estimated model; form the generalized likelihood ratio $$\dfrac{p_X(x;\hat{\theta})}{p_X(x;\theta^*)}$$ and if it exceeds a critical value $\xi$, reject $H_0$. As in binary hypothesis testing, we choose $\xi$ so that the probability of false rejection is (approximately) equal to a given significance level $\alpha$
- Goodness of fit test: test whether a given PMF conforms with observed data
Consider a random variable that takes values in the finite set $\{ 1,\dots,m \}$, and let $\theta_k$ be the probability of outcome $k$. Thus, the distribution (PMF) of this random variable is described by the vector parameter $\theta = (\theta_1,\dots,\theta_m)$. Consider the hypotheses $$H_0:\ \theta = (\theta_1^*,\dots,\theta_m^*),\ H_1:\ \theta \neq (\theta_1^*,\dots,\theta_m^*)$$ where the $\theta_k^*$ are given nonnegative numbers that sum to 1. We draw $n$ independent samples of the random variable and let $N_k$ be the number of samples that result in outcome $k$. Thus, our observation is $X=(N_1,\dots,N_m)$ and we denote its realized value by $X=(n_1,\dots,n_m)$. $N_1+\cdots+N_m = n_1+\cdots+n_m=1$
    - ML estimation, a maximization over the set of probability distributions $(\theta_1,\dots,\theta_m)$; the PMF of the observation vector $X$ is multinomial and the likelihood function is $$p_X(x;\theta) = \underbrace{{n \choose n_1,\dots,n_m}}_c \theta_1^{n_1} \cdots \theta_m^{n_m}$$ $$\ln{p_X(x;\theta)} = \ln{c} + n_1 \ln{\theta_1} + \cdots + n_{m-1} \ln{\theta_{m-1}} + n_m \ln{(1-\theta_1- \cdots - \theta_{m-1})}$$ Assume that the vector $\hat{\theta}$ that maximizes the log-likelihood has positive components, it can be found by setting the derivatives with respect to $\theta_1, \dots, \theta_{m-1}$ to zero $$\dfrac{\partial}{\partial \theta_1} p_X(x;\theta) = \dfrac{n_1}{\theta_1} + \dfrac{n_m}{1-\theta_1 - \cdots - \theta_{m-1}} \cdot (-1) = 0$$ $$similarly,\ \dfrac{n_k}{\hat{\theta_k}} = \dfrac{n_m}{1-\hat{\theta}_1 - \cdots - \hat{\theta}_{m-1}},\ k=1,\dots,m-1$$ Since the term on the right-hand side is equal to $\dfrac{n_m}{\hat{\theta}_m}$, all ratios $\dfrac{n_k}{\hat{\theta}_k}$ must be equal. Using the fact $n_1 + \cdots + n_m = n$ $$\hat{\theta}_k = \dfrac{n_k}{n},\ k=1,\dots,m$$
    - The generalized likelihood ratio test $$reject\ H_0\ if\ \dfrac{p_X(x;\hat{\theta})}{p_X(x;\theta^*)} = \prod_{k=1}^m \dfrac{(n_k/n)^{n_k}}{(\theta_k^*)^{n_k}} > \xi$$ By taking logarithms, the test reduces to $$reject\ H_0\ if\ \sum_{k=1}^m n_k \ln{\dfrac{n_k}{n \theta_k^*}} > \ln{\xi}$$ We need to determine $\xi$ by taking into account the required significance level, that is $$P(S>\ln{\xi};H_0) = \alpha,\ where\ S=\sum_{k=1}^m N_k \ln{\dfrac{N_k}{n \theta_k^*}}$$ The distribution of $S$ under $H_0$ is not readily available and can only be simulated
    - Major simplifications are possible when $n$ is large. In this case, the observed frequencies $\hat{\theta}_k = n_k/n$ will be close to $\theta_k^*$ under $H_0$, with high probability. Then, a second order Taylor series expansion shows that statistic $S$ can be approximated well by $T/2$, where $$T = \sum_{k=1}^m \dfrac{(N_k-n\theta_k^*)^2}{n\theta_k^*}$$ When $n$ is large, it is known that under the hypothesis $H_0$. The distribution of $T$ ($2S$) approaches $\chi^2$ distribution with $m-1$ degrees of freedom. Thus, approximately correct values of $P(2S>\gamma;H_0)=\alpha$ can be obtained from the $\chi^2$ tables.