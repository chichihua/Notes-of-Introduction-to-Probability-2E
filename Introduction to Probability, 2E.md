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
## 1.2 <u>Probabilistic Models</u>
### 1.2.1 Sample Space and Event
- Sample space ($S \ or \ \Omega$): the set of all possible outcomes of an experiment, 试验的所有可能结果
- Event ($A$): a subset of the sample space, 某些试验结果的集合
### 1.2.2 Choose Appropriate Sample Space
- 确定样本空间时，不同试验结果必须是**互斥**的（e.g. 试验为掷一枚骰子，不能同时把“1或3”以及“1或4”定义为一个结果）
### 1.2.3 Sequential Model
### 1.2.4 Axioms of Probability（非负性、可加性、归一性）
- **Probability Space** consists of $S$ and $P$, where $S$ is a sample space and $P$ is a function which takes an event $A \subseteq S$ as input, returns $P(A) \in [0,1]$ as output, such that: 
    - $$P(\varnothing) = 0,\ P(S) = 1$$
    - $$P(\bigcup_{n=1}^\infin A_n) = \sum_{n=1}^\infin P(An)$$ if $A_1, A_2, \dots, A_n$ are disjoint (non-overlapping)
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
    &= 1 - \dfrac{1}{2!} + \dfrac{1}{3!} - \dots + (-1)^{n+1} \cdot \dfrac{1}{n!} \stackrel{e^x=\sum_{n=0}^\infin \frac{1}{n!}x^n}{\approx} 1 - \dfrac{1}{e}
    \end{aligned}$$
    $$P(no\ match)=P(\bigcap_{j=1}^n A_j^c)=1-1+\dfrac{1}{2!}-\dfrac{1}{3!}+\dots+(-1)^n\dfrac{1}{n!} \approx \dfrac{1}{e}$$
    </details>

### 1.2.8 Model and Reality
- 贝特朗悖论：同一事件由于样本空间不同，有不同概率；解决实际问题时，必须明确样本空间，建立无歧义的概率模型
***
## 1.3 <u>Conditional Probability</u>
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
## 1.4 <u>Total Probability Theorem & Bayes' Rule</u>
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
{n \choose n_1,n_2,\dots n_r} &= {n \choose n_1}{n-n_1 \choose n_2} \cdots {n-n_1-\cdots n_{r-1} \choose n_r}
\\ &= \dfrac{n!}{n_1!n_2! \cdots n_r!}
\end{aligned}$$



# Chapter 2 Discrete Random Variables
***
## <u>2.1 Basic Concepts</u>
- A function from sample space $S$ to real line $\mathbb{R}$
***
## <u>2.2 Distributions</u>
Random Variable<br>$X$ | Definition | Probability Mass Function<br>$p_X(k),\ P(X=k)$ | Expectation<br>$E[X]=\sum_xxp_X(x)$ | Variance<br>$var(X)=E[X^2]-(E[X])^2$ | Moment Generating Function<br>$M_X(s)=E[e^{sX}]$
- | - | - | - | - | -
**Discrete Uniform**<br>$X \sim Unif\{a,b\}$ | a finite number of values are equally likely to be observed<br>(e.g. dice) | $$p_X(k)= \begin{cases} \dfrac{1}{b-a+1} &, \ if\ k=a,a+1,\dots,b \\ 0 &, \ otherwise \end{cases}$$ | $$\dfrac{a+b}{2}$$ | $$\dfrac{(b-a)(b-a+2)}{12}$$ | $$M_X(s)=\dfrac{e^{as}}{b-a+1} \cdot \dfrac{e^{(b-a+1)s}-1}{e^s-1}$$
**Bernoulli**<br>$X\sim Bern(p)$ | $X$ has only 2 possible value, 0 and 1 | $$p_X(k)= \begin{cases} p &, \ if\ k=1 \\ 1-p &, \ if\ k=0 \end{cases}$$ | $$p$$ | $$p(1-p)$$ | $$M_X(s)=1-p+pe^{s}$$
**Binomial**<br>$X\sim Bin(n,p)$ | $X$ is #successes in $n$ independent Bern(p) trials | $$p_X(k)= {n \choose k}p^k(1-p)^{n-k} ,\ k=0,1,\dots,n$$ | $$np$$ | $$np(1-p)$$ | $$M_X(s)=(1-p+pe^{s})^n$$
**Geometric**<br>$X\sim Geo(p)$ | indepedent Bern(p) trials, keep failing until suceed at the $k$th trial | $$p_X(k)= (1-p)^{k-1}p,\ k=1,2,\dots$$ | $$\dfrac{1}{p}$$ | $$\dfrac{1-p}{p^2}$$ | $$M_X(s)=\dfrac{pe^s}{1-(1-p)e^s}$$
**Poisson**<br>$X\sim Pois(\lambda)$ | Bin(n,p) converges to Pois($\lambda$) as $n\rightarrow \infin, p \rightarrow 0$ | $$p_X(k)= e^{-\lambda}\dfrac{\lambda^k}{k!},\ k=0,1,2,\dots$$ | $$\lambda$$ | $$\lambda$$ | $$M_X(s)=e^{\lambda(e^s-1)}$$
<details>
<summary>Poisson Paradigm</summary>

Proof that Bin(n,p) converged to Pois($\lambda$) as $n\rightarrow \infin, p \rightarrow 0, constant\ \lambda = np\ (p=\dfrac{\lambda}{n})$:
$$\begin{aligned}
p_X(k) &= \dfrac{n!}{(n-k)!k!}p^k(1-p)^{n-k}
\\ &= \dfrac{n(n-1) \cdots (n-k+1)}{n^k} \cdot \dfrac{\lambda^k}{k!} \cdot (1-\dfrac{\lambda}{n})^{n-k}
\end{aligned}$$ $$Let\ k\ fixed,\ j=1,2,\dots,k,\ \because n \rightarrow \infin,\ \therefore \dfrac{n-k+j}{n} \rightarrow 1,\ (1-\dfrac{\lambda}{n})^{-k} \rightarrow 1,\ (1-\dfrac{\lambda}{n})^{n} \rightarrow e^{-\lambda}$$ $$p_X(k) \rightarrow e^{-\lambda} \dfrac{\lambda^k}{k!}$$
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
Random Variable<br>$X$ | Definition | Probability Density Function<br>$f_X(x)$ | Cumulative Distribution Function<br>$F_X(x)$ | Expectation<br>$E[X]=\int_{-\infin}^{\infin} xf_X(x)dx$ | Variance<br>$var(X)=E[X^2]-(E[X])^2$ |  Moment Generating Function<br>$M_X(s)=E[e^{sX}]$
- | - | - | - | - | - | -
**Continuous Uniform**<br>$X\sim Unif(a,b)$ |  | $$f_X(x)= \begin{cases} \dfrac{1}{b-a} &, \ if\ a \leq x \leq b \\ 0 &, \ otherwise \end{cases}$$ | $$F_X(x)=\dfrac{x-a}{b-a}$$ | $$\dfrac{a+b}{2}$$ | $$\dfrac{(b-a)^2}{12}$$ | $$M_X(s)=\dfrac{1}{b-a} \cdot \dfrac{e^{sb}-e^{sa}}{s}$$
**Exponential**<br>$X\sim Exp(\lambda)$ | Memoryless | $$f_X(x)= \lambda e^{-\lambda x} , \ if\ x \geq 0$$ | $$F_X(x)=1-e^{-\lambda x}$$ | $$\dfrac{1}{\lambda}$$ | $$\dfrac{1}{\lambda^2}$$ | $$M_X(s)=\dfrac{\lambda}{\lambda-s},\ (s<\lambda)$$
**Normal**<br>$X\sim N(\mu,\sigma)$ | The sum of a large number of independent and identically distributed r.v.'s has an approximately normal CDF | $$f_X(x)=\dfrac{1}{\sigma \sqrt{2\pi}}e^{\frac{-(x-\mu)^2}{2\sigma^2}}$$ | $$F_X(x)=\dfrac{1}{\sigma \sqrt{2\pi}} \int_{-\infin}^x e^{\frac{-(t-\mu)^2}{2\sigma^2}} dt$$ | $$\mu$$ | $$\sigma^2$$ | $$M_X(s)=e^{(\sigma^2s^2/2)+\mu s}$$
**Standard Normal**<br>$X\sim Z(0,1)$ |  | $$f_X(x)=\dfrac{1}{\sqrt{2\pi}}e^{\frac{-x^2}{2}}$$ | $$\Phi(x)=\dfrac{1}{\sqrt{2\pi}} \int_{-\infin}^x e^{\frac{-t^2}{2}} dt$$ | $$0$$ | $$1$$ | $$M_X(s)=e^{s^2/2}$$
- CDFs of geometric and exponential r.v.'s:
$$X \sim Geo(p):\ F_{geo}(n)=\sum_{k=1}^n(1-p)^{k-1}p=p \cdot \dfrac{1-(1-p)^n}{1-(1-p)}=1-(1-p)^n,\ n=1,2,\dots$$ $$X \sim Exp(\lambda):\ F_{exp}(x)=\int_0^x \lambda e^{-\lambda t}dt=-e^{-\lambda t} \big|_0^x = 1-e^{-\lambda x},\ x>0$$ $$Let\ \delta=-\dfrac{ln(1-p)}{\lambda},\ so\ that\ \pmb{e^{-\lambda \delta}=1-p}$$ $$\Longrightarrow F_{exp}(n\delta)=F_{geo}(n),\ when\ n=1,2,\dots$$
[![GjAWkt.md.png](https://s1.ax1x.com/2020/04/13/GjAWkt.md.png)](https://imgchr.com/i/GjAWkt)
***
## <u>3.2 Cumulative Distribution Functions (CDF)</u>
- $$F_X(x) = P(X \leq x) = \begin{cases} \sum_{k \leq x}p_X(k) &,\ if\ X\ is\ discrete \\ \int_{-\infin}^x f_X(t)dt &,\ if\ X\ is\ continuous \end{cases}$$
- If $X$ is discrete and integer:
    - $$F_X(k) = \sum_{i=-\infin}^kp_X(i)$$
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
$$f_X(x)=\int_{-\infin}^{\infin}f_{X,Y}(x,y)dy$$ $$f_Y(y)=\int_{-\infin}^{\infin}f_{X,Y}(x,y)dx$$
- Two-dimensional uniform PDF: uniform joint PDF on subset $S$ of the two-dimensional plane $$f_{X,Y}(x,y) = \begin{cases} \dfrac{1}{area\ of\ S} &,\ if\ (x,y)\in S \\ 0 &,\ otherwise \end{cases}$$ For any set $A \subset S$, the probability that $(X,Y)$ lies in $A$ is $$P((X,Y)\in A)=\iint\limits_{(x,y)\in A} f_{X,Y}(x,y)dxdy=\dfrac{1}{area\ of\ S}\int_{(X,Y)\in A} \int dxdy=\dfrac{area\ of\ A}{area\ of\ S}$$
### 3.4.1 Joint CDFs
- $$F_{X,Y}(x,y)=P(X\leq x,Y\leq y)=\int_{-\infin}^x \int_{-\infin}^y f(s,t)dtds$$
- $$f_{X,Y}(x,y)=\dfrac{\partial^2 F_{X,Y}}{\partial x \partial y}(x,y)$$
### 3.4.2 Expectation
- $If\ Z=g(X,Y),$ $$E[g(X,Y)]=\int_{-\infin}^{\infin} \int_{-\infin}^{\infin} g(x,y)f_{X,Y}(x,y)dxdy$$
- $If\ Z=aX+bY+c,$ $$E[aX+bY+c]=aE[X]+bE[Y]+c$$
### 3.4.3 More than Two Random Variables
- Joint PDF: nonnegative function $f_{X,Y,Z}(x,y,z)$ satisfies
$$P((X,Y,Z)\in B)=\iiint\limits_{(x,y,z)\in B} f_{X,Y,Z}(x,y,z)dxdydz$$
- Marginal PDF: $$f_{X,Y}(x,y)=\int_{-\infin}^{\infin} f_{X,Y,Z}(x,y,z)dz$$ $$f_{X}(x)=\int_{-\infin}^{\infin} \int_{-\infin}^{\infin} f_{X,Y,Z}(x,y,z)dydz$$
***
## <u>3.5 Conditioning</u>
### 3.5.1 Conditioning a Random Variable on an Event
- $$f_{X|A}(x) = \begin{cases} \dfrac{f_X(x)}{P(X \in A)} &,\ if\ x \in A \\ 0 &,\ otherwise \end{cases}$$
- $$f_{X,Y|C}(x,y) = \begin{cases} \dfrac{f_{X,Y}(x,y)}{P(C)} &,\ if\ x,y \in A \\ 0 &,\ otherwise \end{cases}$$
    - $$f_{X|C}(x) = \int_{-\infin}^{\infin} f_{X,Y|C}(x,y)dy$$
- Total probability Theorem: $$f_X(x)=\sum_{i=1}^n P(A_i)f_{X|A_i}(x)$$
### 3.5.2 Conditioning one Random Variable on Another
- $$f_{X|Y}(x|y) = \dfrac{f_{X,Y}(x,y)}{f_Y(y)} \ if\ f_Y(y)>0$$
    - Think of value of $Y$ as fixed at some $y$
    shape of $f_{X|Y}(\cdot|y)$: slice of joint PDF $f_{X,Y}(x,y)$
    [![GjAftP.md.png](https://s1.ax1x.com/2020/04/13/GjAftP.md.png)](https://imgchr.com/i/GjAftP)
    - $$\int_{-\infin}^{\infin} f_{X|Y}(x|y)=\dfrac{\int_{-\infin}^{\infin} f_{X,Y}(x,y)}{f_Y(y)}=1,\ f_Y(y):scaling\ factor$$
- Intuitive way to understand conditional PDF:
    - Let $\delta,\epsilon$ be small positive numbers $$P(x \leq X \leq x+\delta|A) \approx f_{X|A}(x) \cdot \delta$$ $$P(x \leq X \leq x+\delta|y \leq Y \leq y+\epsilon) \approx \dfrac{f_{X,Y}(x,y)\cdot \delta \cdot \epsilon}{f_Y(y) \cdot \epsilon}=f_{X|Y}(x|y) \cdot \delta$$ $$when\ \epsilon \rightarrow 0,\ P(x \leq X \leq x+\delta|Y=y) \approx f_{X|Y}(x|y) \cdot \delta$$ $$more\ generally,\ P(X \in A|Y=y) = \int_A f_{X|Y}(x|y)dx$$
### 3.5.3 Conditional Expectation
- $$E[X|A]=\int_{-\infin}^{\infin} xf_{X|A}(x)dx$$ $$E[X|Y=y]=\int_{-\infin}^{\infin} xf_{X|Y}(x|y)dx$$
- Total Expectation Theorem: $$E[X]=\int_{-\infin}^{\infin} f_Y(y)E[X|Y=y]dy$$
### 3.5.4 Independence
- $X$ and $Y$ are independent if: 
    - $$f_{X,Y}(x,y) = f_X(x)f_Y(y),\ for\ all\ x,y$$
    - $$f_{X|Y}(x|y) = f_X(x),\ for\ all\ x\ and\ all\ y\ with\ f_Y(y)>0$$
    - $$F_{X,Y}(x,y) = F_X(x)F_Y(y),\ for\ all\ x,y$$
    - $$E[XY] = E[X]E[Y]$$
    - $$var(X+Y) = var(X)+var(Y)$$
***
## <u>3.6 The Continuous Bayes' Rule</u>
- $$f_{X|Y}(x|y) = \dfrac{f_X(x)f_{Y|X}(y|x)}{f_Y(y)}$$ $$f_{X|Y}(x|y) = \dfrac{f_X(x)f_{Y|X}(y|x)}{\int_{-\infin}^{\infin} f_X(t)f_{Y|X}(y|t)dt}$$
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
- Suppose that $g$ is **strictly monotonic** and for all $x$ in the range of $X$ we have $$y=g(x)\ if\ and\ only\ if\ x=h(y)$$ Assume that $h$ is differentiable, then $$f_Y(y)=f_X(h(y))\bigg|\dfrac{dh}{dy}(y)\bigg|$$
### 4.1.3 Multiple Random Variables
- Laplace (two-sided exponential) PDF:
Romeo and Juliet have a date at a given time, and each, independently, will be late by an amount of time that is exponentially distributed with parameter $\lambda$. What is the PDF of the difference between their times of arrival?
Let $X,Y$ be the amounts by which Romeo and Juliet are late. We want to find the PDF of $Z=X-Y$. We will first calculate the CDF $F_Z(z)$ by considering seperately the cases $z \geq 0$ and $z<0$.
[![GjA2TI.png](https://s1.ax1x.com/2020/04/13/GjA2TI.png)](https://imgchr.com/i/GjA2TI)
$$f_{X,Y}(x,y)=f_X(x)f_Y(y)=\lambda e^{-\lambda x} \lambda e^{-\lambda y},\ x,y \geq 0$$
    - For $z \geq 0$:
    $$\begin{aligned}
    F_Z(z) &= P(Z \leq z) = P(X-Y \leq z) = 1 - P(X-Y > z)
    \\ &= 1 - \int_0^{\infin} \int_{z+y}^{\infin} \lambda e^{-\lambda x} \lambda e^{-\lambda y} dxdy
    \\ &= 1 - \int_0^{\infin} \lambda e^{-\lambda y} \bigg[ -e^{-\lambda x}\bigg]_{z+y}^{\infin} dy
    \\ &= 1 - \int_0^{\infin} \lambda e^{-\lambda y} e^{-\lambda (z+y)} dy
    \\ &= 1 - e^{-\lambda z}\bigg[ -\dfrac{1}{2} e^{-2\lambda y} \bigg]_0^{\infin}
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
- Continuous convolution: $$f_Z(z) = \int_{-\infin}^{\infin} f_{X,Z}(x,z) dx = \int_{-\infin}^{\infin} f_X(x)f_Y(z-x) dx$$
    - Graphical Calculation of Convolution 
    [![Gj1cn0.png](https://s1.ax1x.com/2020/04/13/Gj1cn0.png)](https://imgchr.com/i/Gj1cn0)
- Sum of independent normal r.v.'s: $X \sim N(\mu_x,\sigma_x^2), Y \sim N(\mu_y,\sigma_y^2)$ $$\begin{aligned} f_Z(z) &= \int_{-\infin}^{\infin} \dfrac{1}{\sigma_x \sqrt{2\pi}} exp \bigg( -\dfrac{(x-\mu_x)^2}{2\sigma_x^2} \bigg) \dfrac{1}{\sigma_y \sqrt{2\pi}} exp \bigg( -\dfrac{(z-x-\mu_y)^2}{2\sigma_y^2} \bigg) dx \\ &= \dfrac{1}{\sqrt{2\pi(\sigma_x^2+\sigma_y^2)}} exp \bigg( -\dfrac{(z-\mu_x-\mu_y)^2}{2(\sigma_x^2+\sigma_y^2)} \bigg) \end{aligned}$$ $\Longrightarrow Z \sim N(\mu_x+\mu_y, \sigma_x^2+\sigma_y^2)$
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
- The transform associated with a r.v. $X$ is a function $M_X(s)$ (associated MGF) of a scalar parameter $s$: $$M_X(s)=E[e^{sX}]= \begin{cases} \sum\limits_x e^{sx}p_X(x) &,\ if\ X\ is\ discrete \\ \int_{-\infin}^{\infin} e^{sx}f_X(x) dx &,\ if\ X\ is\ continuous \end{cases}$$
- $X \sim Pois(\lambda):$ $$M(s)=e^{\lambda(e^s-1)}$$
- $X \sim Exp(\lambda):$ $$M(s)=\dfrac{\lambda}{\lambda-s},\ only\ if\ s<\lambda$$
- $Y=aX+b$: $$M_Y(s)=E[e^{s(aX+b)}]=e^{sb}E[e^{saX}]=e^{sb}M_X(sa)$$
- $Y \sim Z(0,1):$ $$M_Y(s)=e^{s^2/2}$$
$X \sim N(\mu, \sigma^2),\ X=\sigma Y + \mu$ $$M_X(s)=e^{s\mu}M_Y(s\sigma)=e^{s^2\sigma^2/2 + \mu s}$$
### 4.4.1 From Transforms(MGFs) to Moments
- $$\dfrac{d}{ds}M(s)=\dfrac{d}{ds}\int_{-\infin}^{\infin} e^{sx}f_X(x) dx=\int_{-\infin}^{\infin} xe^{sx}f_X(x) dx$$
- $$\dfrac{d}{ds}M(s) \bigg|_{s=0} = \int_{-\infin}^{\infin} xf_X(x) dx=E[X]$$
- $$\dfrac{d^n}{ds^n}M(s) \bigg|_{s=0} = \int_{-\infin}^{\infin} x^nf_X(x) dx=E[X^n]$$
- **Why does MGF work?** $$Recall\ e^x=1+x+\dfrac{x^2}{2!}+\dfrac{x^3}{3!}+\cdots$$ $$and\ e^{sx}=1+sx+\dfrac{s^2}{2!}t^2+\dfrac{s^3}{3!}t^3+\cdots$$ $$\Longrightarrow E[e^{sX}]=1+sE[X]+\dfrac{s^2}{2!}E[X^2]+\dfrac{s^3}{3!}E[X^3]+\cdots$$ $$\begin{aligned} \Longrightarrow \dfrac{d}{ds}E[e^{sX}]\bigg|_{s=0} &= 0+E[X]+sE[X^2]+\dfrac{3s^2}{3!}E[X^3]+\cdots \\ &=0+E[X]+0+0+\cdots \\ &= E[X] \end{aligned}$$ $$\begin{aligned} and\ \dfrac{d^2}{ds^2}E[e^{sX}]\bigg|_{s=0} &= 0+0+E[X^2]+\dfrac{3!s}{3!}E[X^3]+\cdots \\ &=0+0+E[X^2]+0+\cdots \\ &= E[X^2] \end{aligned}$$
- Properties of MGF:
    - $M_X(0)=E[e^{0X}]=1$
    - $If\ X\ only\ takes\ nonnegative\ integer\ values,\ \lim\limits_{s \to -\infin}M_X(s)=P(X=0)$
- Convergence of MGFs $\Longrightarrow$ Convergence of CDFs: 
That is, let $X_1,X_2,\dots$ be a sequence of r.v.'s, each with MGF $M_{X_i}(s)$ and CDF $F_{X_i}(x)$
Suppose $\lim\limits_{i \to \infin} M_{X_i}(s)=M_X(s)$, $\forall s$ in a neighborhood of $0$, and $M_X(s)$ is an MGF
Then there exists a r.v. $X$ with CDF $F_X(x)$ where
$\lim\limits_{i \to \infin} F_{X_i}(x) = F_X(x)$
and this r.v. $X$ has moments determined by MGF $M_X(s)$
    <details>
    <summary>Example: Convergence of Binomial and Poisson MGFs$</summary>

    $Bin(n,p)$ can be approx by $Pois(\lambda)$ using $\lambda=np$,
    Let $X \sim Bin(n,p)$, $Y \sim Pois(np)$,
    $M_X(s)=(1-p+pe^s)^n$
    $M_Y(s)=e^{np(e^s-1)}$
    $$\begin{aligned} M_X(s) &= (1-p+pe^s)^n \\ &= (1+p(e^s-1))^n \\ &= (1+\dfrac{np(e^s-1)}{n})^n \\ &= e^{np(e^s-1)},\ when\ n \to \infin \\ &= M_Y(s) \end{aligned}$$
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

        $$\begin{aligned} E[e^{sY}|N=n] &= E[e^{s(X_1+\cdots+X_N)}|N=n] \\ &=  E[e^{sX_1} \cdots e^{sX_n}] \\ &= E[e^{sX_1}] \cdots E[e^{sX_n}] \\ &= \big( M_X(s) \big)^n \end{aligned}$$ $$\Longrightarrow E[e^{sY}|N]=\big( M_X(s) \big)^N$$ $$\stackrel{Law\ of\ Iterated\ Expectations}{\Longrightarrow} M_Y(s) = E[e^{sY}] = E[E[e^{sY}|N]] = E[\big( M_X(s) \big)^N] = \sum_{n=1}^{\infin} \big( M_X(s) \big)^n P_N(n)$$ $$while,\ M_N(s) = E[e^{sN}] = \sum_{n=1}^{\infin} (e^s)^n P_N(n)$$ $$when\ M_X(s)=e^s,\ s=\log{M_X(s)}$$ $$M_N \big( \log{M_X(s)} \big)=M_Y(s)$$
        </details>

# Chapter 5 Limit Theorems
***
## <u>5.1 Markov and Chebyshev Inequalities</u>
- Markov Inequality (based on the mean): use a bit of information about a distribution to learn something about probabilities of "extreme events" 
"If $X \geq 0$ and $E[X]$ is small, then $X$ is unlikely to be very large" 
$$If\ X \geq 0\ and\ a > 0,\ then\ P(X \geq a) \leq \dfrac{E[X]}{a}$$
    <details>
    <summary>Proof</summary>

    (1) $$E[X]=\int_0^{\infin} xf_X(x)dx \geq \int_a^{\infin} xf_X(x)dx \geq \int_a^{\infin} af_X(x)dx = a P(X \geq a)$$

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
        - Chernoff bound $$P(X \geq a)=P(e^{sX} \geq e^{sa}) \leq \dfrac{E[e^{sX}]}{e^{sa}}=e^{-sa}M_X(s)$$
        - Hoeffding's Inequality: If i.i.d. $X_i$ is equally likely to be $-1$ or $1$, and $a>0$,then $$P(X_1+\cdots+X_n \geq na) \leq e^{-na^2/2}$$
            <details>
            <summary>Proof</summary>

            
            $$P(e^{s(X_1+\cdots+X_n)} \geq e^{sna}) \leq \dfrac{E[e^{s(X_1+\cdots+X_n)}]}{e^{sna}} = \dfrac{\prod\limits_{i=1}^n E[e^{sX_i}]}{e^{sna}} = \bigg( \dfrac{E[e^{sX_i}]}{e^{sa}} \bigg)^n = \bigg( \dfrac{\dfrac{1}{2}(e^s+e^{-s})}{e^{sa}} \bigg)^n$$ $$\because e^s=1+s+\dfrac{s^2}{2!}+\dfrac{s^3}{3!}+\cdots=\sum_{i=0}^{\infin} \dfrac{s^i}{i!}$$ $$\therefore \dfrac{1}{2}(e^s+e^{-s}) = \dfrac{1}{2}(1+s+\dfrac{s^2}{2!}+\dfrac{s^3}{3!}+\cdots) + \dfrac{1}{2}(1-s+\dfrac{s^2}{2!}-\dfrac{s^3}{3!}+\cdots) = \sum_{i=0}^{\infin} \dfrac{s^{2i}}{(2i)!}$$ $$\because (2i)!=\underbrace{1 \cdot 2 \cdot \cdots \cdot i}_{i\ terms} \underbrace{\cdot (i+1) \cdot \cdots \cdot (2i)}_{i\ terms} \geq i! \cdot 2^i$$ $$\therefore \sum_{i=0}^{\infin} \dfrac{s^{2i}}{(2i)!} \leq \sum_{i=0}^{\infin} \dfrac{s^{2i}}{i! \cdot 2^i} = \sum_{i=0}^{\infin} \dfrac{(\dfrac{s^2}{2})^i}{i!} = e^{s^2/2}$$ $$\bigg( \dfrac{\dfrac{1}{2}(e^s+e^{-s})}{e^{sa}} \bigg)^n \leq \bigg( \dfrac{e^{s^2/2}}{e^{sa}} \bigg)^n = \bigg( e^{s^2/2-sa} \bigg)^n \stackrel{Let\ s=a}{=} e^{-na^2/2}$$
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
        - Apply the Chebyshev Inequality and obtain $$P(|M_n-\mu| \geq \epsilon) \leq \dfrac{\sigma^2}{n\epsilon^2} \stackrel{n \to \infin}{\longrightarrow} 0$$
    - **WLLN:** $$For\ \epsilon >0,\ P(|M_n-\mu| \geq \epsilon)=P \Big( \Big| \dfrac{X_1+\cdots+X_n}{n}-\mu \Big| \geq \epsilon \Big) \longrightarrow 0,\ as\ n \to \infin$$
- Probabilities and Frequencies: consider an event $A$ defined the conext of some probabilistic experiment. Let $p=P(A)$ be the probability of this event. We consider $n$ independent repetitions of the experiment, and let $M_n$ be the fraction of time that event $A$ occurs; in this context, $M_n$ is often called the **empirical frequency** of $A$. $$M_n=\dfrac{X_1+\cdots+X_n}{n}$$ $$X_i= \begin{cases} 1 &,\ if A\ occurs \\ 0 &,\ otherwise \end{cases}$$ $E[X_i]=p$, the WLLN applies and shows that when $n$ is large, the empirical frequency is most likely to be within $\epsilon$ of $p$. This allows us to conclude that empirical frequencies are faithful estimates of $p$.
***
## <u>5.3 Convergence in Probability</u>
- Convergence of a Deterministic Sequence:
Let $a_1,a_2,\dots$ be a sequence of real numbers, and let $a$ be another real number. We say that the sequence $a_n$ converges to $a$, or $\lim\limits_{n \to \infin} a_n = a$, if for every $\epsilon>0$ there exists some $n_0$ such that $$|a_n-a|\leq \epsilon,\ for\ all\ n \geq n_0$$ [![JSMSk8.md.png](https://s1.ax1x.com/2020/04/14/JSMSk8.md.png)](https://imgchr.com/i/JSMSk8)
- Convergence in Probability:
Let $Y_1,Y_2,\dots$ be a sequence of r.v.'s (not necessarily independent), and let $a$ be a real number. We say that the sequence $Y_n$ converges to $a$ in probability, if for every $\epsilon > 0$, we have $$\lim_{n \to \infin} P(|Y_n-a| \geq \epsilon)=0$$ [![JS8okt.md.png](https://s1.ax1x.com/2020/04/14/JS8okt.md.png)](https://imgchr.com/i/JS8okt) 
"Almost all of the PMF/PDF of $Y_n$ eventually gets concentrated arbitrarily close to $a$"
- Convergence in probability **does not** imply convergence of expectations: convergence in probability only cares about that the tail of the distribution has small probability; the expectation is highly sensitive to the tail of the distribution
    <details>
    <summary>Example</summary>

    [![JSUpSP.png](https://s1.ax1x.com/2020/04/14/JSUpSP.png)](https://imgchr.com/i/JSUpSP)
    </details>
- Convergence in probability of the sum of two r.v.'s: $$If\ X_n \to a\ and\ Y_n \to b,\ then\ X_n+Y_n \to a+b$$
- Related Topics:
    - Different types of convergene
        - Convergence "with probability 1": when an outcome of the experiment is obtained, the resulting sequence of the values of the r.v.'s $Y_n$ will converge to the value of the r.v. $Y$ $$P( \{ \omega: Y_n(\omega) \stackrel{n \to \infin}{\longrightarrow} Y(\omega) \} ) = 1$$
        - Strong law of large numbers
        - Convergence of a sequence of distributions (CDFs) to a limiting CDF
***
## <u>5.4 Central Limit Theorem</u>
- Different scaling of the sum of i.i.d. r.v.'s:
    - $S_n=X_1+\cdots+X_n$ $$E[S_n]=n\mu,\ var(S_n)=n\sigma^2$$
    - $M_n=\dfrac{S_n}{n}=\dfrac{X_1+\cdots+X_n}{n}$ $$E[M_n]=\mu,\ var(M_n)=\dfrac{\sigma^2}{n}$$
    - $Z_n=\dfrac{S_n-n\mu}{\sqrt{n}\sigma}$ $$E[Z_n]=0,\ var(Z_n)=1$$
- **Central Limit Theorem:** $$\lim_{n \to \infin} P(Z_n \leq z)=\Phi(z)=\dfrac{1}{\sqrt{2\pi}} \int_{-\infin}^{z} e^{-t^2/2} dt,\ for\ all\ z$$
    <details>
    <summary>Proof using convergence of MGF</summary>

    Let $X_1,\dots,X_n$ be a sequence of i.i.d. r.v.'s with mean $0$, variance $\sigma^2$ and associated transform (MGF) $M_X(s)$. Assume that $M_X(s)$ is finite when $-d<s<d$, where $d$ is some positive number. Let $$Z_n=\dfrac{X_1+\cdots+X_n}{\sigma \sqrt{n}}$$
    (a) The transform associated with $Z_n$ satisfies $$M_{Z_n}(s)=\bigg( M_X \big( \dfrac{s}{\sigma \sqrt{n}} \big)  \bigg)^n$$ Derivation: 
    $$\begin{aligned} M_{Z_n}(s) = E[e^{sZ_n}] &= E \bigg[ exp \bigg\{ \dfrac{S}{\sigma \sqrt{n}} \sum_{i=1}^n X_i \bigg\} \bigg] \\ &= \prod_{i=1}^n \bigg[ exp \bigg\{ \dfrac{S}{\sigma \sqrt{n}} X_i \bigg\} \bigg] \\ &= \bigg( M_X \big( \dfrac{s}{\sigma \sqrt{n}} \big)  \bigg)^n \end{aligned}$$
    (b) Suppose that the transform $M_X(s)$ has a second order Tyler series expansion around $s=0$, of the form $$M_X(s) = a + bs + cs^2 + o(s^2)$$ where $o(s^2)$ is a function that satisfies $\lim\limits_{s \to 0} o(s^2)/s^2=0$. Find $a,b,c$.
    Derivation: $$a=M_X(0)=1$$ $$b = \dfrac{d}{ds} M_X(s) \bigg|_{s=0} = E[X] = 0$$ $$c = \dfrac{1}{2!} \dfrac{d^2}{ds^2} M_X(s) \bigg|_{s=0} = \dfrac{1}{2} E[X^2] = \dfrac{\sigma^2}{2}$$
    (c) Combine the results of (a) and (b) to show that the transform $M_{Z_n}(s)$ converges to the transform associated with a standard normal random variable, that is, $$\lim_{n \to \infin} M_{Z_n}(s) = e^{s^2/2} ,\ for\ all\ s$$ Derivation: $$\begin{aligned} M_{Z_n}(s)=\bigg( M_X \big( \dfrac{s}{\sigma \sqrt{n}} \big)  \bigg)^n &= \bigg( a + \dfrac{bs}{\sigma \sqrt{n}} + \dfrac{cs^2}{\sigma^2 n} + o\big( \dfrac{s^2}{\sigma^2 n} \big) \bigg)^n \\ &= \bigg( 1 + \dfrac{s^2}{2 n} + o\big( \dfrac{s^2}{\sigma^2 n} \big) \bigg)^n \end{aligned}$$ $$\lim_{n \to \infin} M_{Z_n}(s)=\lim_{n \to \infin} \bigg( 1 + \dfrac{\frac{s^2}{2}}{n} \bigg)^n=e^{s^2/2}$$
    </details>

## 5.4.1 Approximations Based on the CLT
- Let $S_n=X_1+\cdots+X_n$, where the $X_i$ are i.i.d. r.v.'s with mean $\mu$ and variance $\sigma^2$. If $n$ is large, the probability $P(S_n \leq c)$ can be approximated by treating $S_n$ as if it were normal, according to the following procedure.
    - 1. Calculate the mean $n\mu$ and the variance $n\sigma^2$ of $S_n$
    - 2. Calculate the normalized value $z=\dfrac{c-n\mu}{\sqrt{n} \sigma}$
    - 3. Use the approximation $$P(S_n \leq c) \approx \Phi(z)$$ where $\Phi(z)$ is available from standard normal CDF tables
- The normal approximation is increasingly accurate as $n \to \infin$
- How large $n$ should be depends on whether the distribution of $X_i$ is close to normal and whether it is symmetric
- The normal approximation to $P(S_n \leq c)$ tends to be more faithful when $c$ is in the vicinity of the mean of $S_n$
### 5.4.2 De Moivre-Laplace Approximation to the Binomial
- If $S_n$ is a binomial r.v. with parameters $n$ and $p$, $n$ is large, and $k,l$ are nonnegative integers, then $$P(k \leq S_n \leq l) \approx \Phi \bigg( \dfrac{l+\frac{1}{2}-np}{\sqrt{np(1-p)}} \bigg)-\Phi \bigg( \dfrac{k-\frac{1}{2}-np}{\sqrt{np(1-p)}} \bigg)$$
***
## <u>5.5 The Strong Law of Large Numbers</u>
- Let $X_1,X_2,\dots$ be a sequence of i.i.d. r.v.'s with mean $\mu$. Then, the sequence of sample means $M_n=(X_1+\cdots+X_n)/n$ converges to $\mu$, with probability 1 $$P\bigg( \lim_{n \to \infin} \dfrac{X_1+\cdots+X_n}{n}=\mu \bigg)=1$$
- Convergence with Probability 1:
Let $Y_1,Y_2,\dots$ be a sequence of r.v.'s (not necessarily independent). Let $c$ be a real number. $Y_n$ converges to $c$ with probability 1 (or almost surely) if $$P(\lim_{n \to \infin} Y_n = c) = 1$$
- Convergence with probability 1 implies convergence in probability, but the converse is not necessarily true

# Chapter 6 The Bernoulli and Poisson Processes
***
