# Review of Information Theory

## Lecture 1: Entropy, Prefix-Free Codes and Kraft's inequality
**Lemma 1.1. Jensen's Inequality**  
Let $S \subseteq \mathbb{R}^{n}$ be a convex set and let $X$ be a random variable taking values inside $S$. Then, for a convex function $f: S \rightarrow \mathbb{R}$, we have that:
$$\mathbb{E}[f(X)] \geq f(\mathbb{E}[X]).$$
Equivalently, for a concave function $f: S \rightarrow \mathbb{R}$, we have that:
$$\mathbb{E}[f(X)] \leq f(\mathbb{E}[X]).$$
<br>

**Proposition 1.2. Lower and Upper Bound of Entropy**  
Let $X$ be a random variable supported on a finite set $\mathcal{X}$ as above. Then:
$$
0 \leq H(X) \leq \log (|\mathcal{X}|).
$$
<br>

**Proposition 1.3. Kraft's Inequality**   
Let $|\mathcal{X}|=n$. There exists a prefix-free code for $\mathcal{X}$ over \{0,1\} with codeword lengths $\ell_{1}, \ldots, \ell_{n}$ if and only if:
$$
\sum_{i=1}^{n} \frac{1}{2^{\ell_{i}}} \leq 1.
$$
For codes over a larger alphabet $\Sigma$, we replace $2^{\ell_{i}}$ above by $|\Sigma|^{\ell_{i}}$.


## Lecture 2: Conditional and Joint Entropy, Subadditivity of Entropy, Source Coding Theorem
**Claim 2.1. Minimal Bits to Communicate a Random Variable**  
Let $X$ be a random variable taking values in $\mathcal{X}$ and let $C: \mathcal{X} \rightarrow\{0,1\}$ be a prefix-free code. Then the expected number of bits used by $\mathrm{C}$ to communicate the value of $\mathrm{X}$ is at least $H(X)$.
<br>

**Definition 2.2. The Shannon Code**  
We now construct a (prefix-free) code for conveying the value of $X$, using at most $H(X)+1$ bits on average (over the distribution of $X)$. For an element $x \in \mathcal{X}$ which occurs with probability $p(x)$, we will use a codeword of length $\lceil\log (1 / p(x))$ ]. By Kraft's inequality, there exists a prefix-free code with these codeword lengths, since
$$
\sum_{x \in \mathcal{X}} \frac{1}{2^{|C(x)|}}=\sum_{x \in \mathcal{X}} \frac{1}{2^{\lceil\log (1 / p(x))\rceil}} \leq \sum_{x \in \mathcal{X}} \frac{1}{2^{\log (1 / p(x))}}=\sum_{x \in \mathcal{X}} p(x)=1
$$
Also, the expected number of bits used is
$$
\sum_{x \in \mathcal{X}} p(x) \cdot\lceil\log (1 / p(x))\rceil \leq \sum_{x \in \mathcal{X}} p(x) \cdot(\log (1 / p(x))+1)=H(X)+1
$$
This code is known as the Shannon code.
<br>

**Proposition 2.3. Information Never Hurts**  
$$
H(Y) \geq H(Y \mid X)
$$
<br>

**Proposition 2.4. Fundamental Source Coding Theorem**  
For all $\varepsilon>0$ there exists a $n_{0}$ such that for all $n \geq n_{0}$ and given $n$ copies of $X, X_{1}, \ldots, X_{n}$ sampled i.i.d., it is possible to communicate $\left(X_{1}, \ldots, x_{n}\right)$ using at most $H(X)+\varepsilon$ bits per copy on average.
<br>

**Proposition 2.5. Cauchy-Schwarz Inequality**  
$$
\left(\sum_{i=1}^{n} a_{i} \cdot b_{i}\right) \leq\left(\sum_{i=1}^{n} a_{i}^{2}\right) \cdot\left(\sum_{i=1}^{n} b_{i}^{2}\right)
$$


## Lecture 3: Shearer's Lemma and Mutual Information
**Lemma 3.1. Shearer's Lemma**  
Let $\left\{X_{1}, \ldots, X_{n}\right\}$ be a set of random variables. For any $S \subset[n],$ let us denote $X_{S}=\left\{X_{i}: i \in S\right\} .$ Let $\mathcal{F} \subseteq 2^{[n]}$ be a collection of subsets of $[n]$ with the property that for all $i \in[n],$ we have that $|\{S \in \mathcal{F} \mid S \ni i\}| \geq t$. Then
$$
t \cdot H\left(X_{1}, \ldots, X_{n}\right) \leq \sum_{S \in \mathcal{F}} H\left(X_{S}\right)
$$
<br>

**Lemma 3.2. Shearer's Lemma: Distribution Version**  
Let $\left\{X_{1}, \ldots, X_{n}\right\}$ be a set of random variables. For any $S \subset[n],$ let us denote $X_{S}=\left\{X_{i}: i \in S\right\} .$ Let $D$ be an arbitrary distribution on $2^{[n]}$ (set of all subsets of $\left.[n]\right)$ and let $\mu$ be such that $\forall i \in[n] \mathbb{P}_{S \sim D}[i \in S] \geq \mu$. Then:
$$
\mu \cdot H\left(X_{1}, \ldots, X_{n}\right) \leq \underset{S \sim D}{\mathbb{E}}\left[H\left(X_{S}\right)\right]
$$
<br>

**Proposition 3.3. Bounding the Volume of a Body**  
Let $S \subseteq \mathbb{R}^{d}$ be a finite set of points in dimensions, and let $S_{1}, \ldots, S_{d}$ denote the set of projections orthogonal to each of the d coordinate axes. Then we have
$$
|S| \leq\left(\prod_{i=1}^{d}\left|S_{i}\right|\right)^{1 /(d-1)}
$$
<br>

**Proposition 3.4. Loomis-Whitney Inequality**  
Let $B \subseteq \mathbb{R}^{d}$ be a measurable body and let $B_{1}, \ldots, B_{d}$ denote its projections orthogonal to each of the coordinate axes. Then, we have
$$
\operatorname{Vol}_{d}(B) \leq\left(\prod_{i=1}^{d} \operatorname{Vol}_{d-1}\left(B_{i}\right)\right)^{1 /(d-1)}
$$
<br>

**Lemma 3.5. Chain Rule of Mutual Information**  
$$
I\left(\left(X_{1}, \ldots, X_{m}\right) ; Y\right)=\sum_{i=1}^{m} I\left(X_{i} ; Y \mid X_{1}, \ldots, X_{i-1}\right)
$$
<br>

**Lemma 3.6. Data Processing Inequality**  
Let $X \rightarrow Y \rightarrow Z$ be a Markov chain. Then:
$$
I(X ; Y) \geq I(X ; Z)
$$
<br>

**Definition 3.7. Sufficient Statistics**  
For random variables $X$ and $Y,$ a function $g(Y)$ is called a sufficient statistic $(o f$ $Y$ ) for $X$ if $I(X ; Y)=I(X ; g(Y))$ i.e., $g(Y)$ contains all the relevant information about $X$.
<br>

## Lecture 4: Fana's inequality, Graph Entropy, KL Divergence, TV Distance and Pinsker's Inequality
**Lemma 4.1. Fano's Inequality**  
Let $X \rightarrow Y \rightarrow \widehat{X}$ be a Markov chain, and let $p_{e}=\mathbb{P}[\hat{X} \neq X]$. Let $\mathrm{H}_{2}\left(\mathrm{p}_{e}\right)$ denote the binary entropy function computed at $p_{e}$. Then,
$$
H_{2}\left(p_{e}\right)+p_{e} \cdot \log (|\mathcal{X}|-1) \geq H(X \mid \widehat{X}) \geq H(X \mid Y)
$$
<br>

**Definition 4.2. Graph Entropy**  
Given a graph $G=(\mathcal{V}, \mathcal{E}),$ we define the graph entropy $H(G)$ as
$$
\min _{X, Y} I(X ; Y)
$$
s.t. $X$ is uniformly distributed over $\mathcal{V}$; and $Y$ is an independent set in $G$ containing $X$.
<br>

**Proposition 4.3. Subadditivity of Graph Entropy**  
Let $G_{1}=\left(\mathcal{V}, \mathcal{E}_{1}\right)$ and $G_{2}=\left(\mathcal{V}, \mathcal{E}_{2}\right)$ be two graphs, and let $G=\left(\mathcal{V}, \mathcal{E}_{1} \cup \mathcal{E}_{2}\right),$ which we denote by $G=G_{1} \cup G_{2}$. Then,
$$
H(G)=H\left(G_{1} \cup G_{2}\right) \leq H\left(G_{1}\right)+H\left(G_{2}\right)
$$
<br>

**Definition 4.4. KL Divergence**  
$$D(P \| Q):=\sum_{x \in U} p(x) \log \left(\frac{p(x)}{q(x)}\right)$$
<br>

**Lemma 4.5. Non-negativity of KL Divergence**  
Let $P$ and $Q$ be distributions on a finite universe $\mathcal{X} .$ Then $D(P \| Q) \geq 0$ with equality if and only if $P=Q$.
<br>

**Lemma 4.6. Chain Rule for KL Divergence**  
Let $P(X, Y)$ and $Q(X, Y)$ be two distributions for a pair of variables $X$ and $Y$. Then,
$$
\begin{aligned}
D(P(X, Y) \| Q(X, Y)) &=D(P(X) \| Q(X))+\underset{x \sim P}{\mathbb{E}}[D(P(Y \mid X=x) \| Q(Y \mid X=x))] \\
&=D(P(X) \| Q(X))+D(P(Y \mid X) \| Q(Y \mid X))
\end{aligned}
$$
<br>

**Definition 4.7. Total Variation**  
Let $P$ and $Q$ be two distributions on a finite universe $\mathcal{X}$. Then the *total-variation distance* or *statistical distance* between $P$ and $Q$ is defined as
$$
\delta_{T V}(P, Q)=\frac{1}{2} \cdot\|P-Q\|_{1}=\frac{1}{2} \cdot \sum_{x \in \mathcal{X}}|p(x)-q(x)|
$$
The quantity $\|P-Q\|_{1}$ is referred to as the $\ell_{1}$-*distance* between $P$ and $Q$.
<br>

**Lemma 4.8. The Classifier's Behavior Over Two Distributions**  
Let $P, Q$ be any distributions on $\mathcal{X} .$ Let $f: \mathcal{X} \rightarrow[0, B] .$ Then:
$$
|\underset{P}{\mathbb{E}}[f(x)]-\underset{Q}{\mathbb{E}}[f(x)]| \leq \frac{B}{2} \cdot\|P-Q\|_{1}=B \cdot \delta_{T V}(P, Q)
$$
<br>

**Lemma 4.9. Pinsker's Inequality / TV as Lower Bound for KL Divergence**  
Let $P$ and $Q$ be two distributions defined on a universe $\mathcal{X}$. Then:
$$
D(P \| Q) \geq \frac{1}{2 \ln 2} \cdot\|P-Q\|_{1}^{2}.
$$
<br>

**Proposition 4.10. Pinsker's Inequality for $\mathcal{X}=\{0,1\}$**  
Consider when $\mathcal{X}=$ \{0,1\} and $P, Q$ are distributions as below
$$
P=\left\{\begin{array}{ll}
1 & \text { w.p. } p \\
0 & \text { w.p. } 1-p
\end{array} \quad\right. \text { and } \quad Q=\left\{\begin{array}{ll}
1 & \text { w.p. } q \\
0 & \text { w.p. } 1-q
\end{array}\right.
$$
Then,
$$D(P \| Q)=p \cdot \log \left(\frac{p}{q}\right)+(1-p) \cdot \log \left(\frac{1-p}{1-q}\right) \quad,$$
$$\quad\|P-Q\|_{1}=2  \mid p-q \mid,$$
$$p \cdot \log \left(\frac{p}{q}\right)+(1-p) \cdot \log \left(\frac{1-p}{1-q}\right) \geq \frac{2}{\ln 2} \cdot(p-q)^{2}.$$
<br>

**Proposition 4.10. TV and KL Divergence on $\{0,1\}$**  
Let $P$ and $Q$ be distributions on a finite set $\mathcal{X} .$ Then, there exist distributions $P^{\prime}, Q^{\prime}$ on \{0,1\} such that
$$
\left\|P^{\prime}-Q^{\prime}\right\|_{1}=\|P-Q\|_{1} \text { and } D(P \| Q) \geq D\left(P^{\prime} \| Q^{\prime}\right)
$$
<br>

## Lecture 5: Convexity of KL, Lower Bound for Distinguishing Coins and Bandit Problems
**Proposition 5.1. Log-Sum Inequality**  
For $a_{1}, a_{2}, b_{1}, b_{2} \geq 0$
$$
\left(a_{1}+a_{2}\right) \cdot \log \left(\frac{a_{1}+a_{2}}{b_{1}+b_{2}}\right) \leq a_{1} \cdot \log \left(\frac{a_{1}}{b_{1}}\right)+a_{2} \cdot \log \left(\frac{a_{2}}{b_{2}}\right).
$$
<br>

**Proposition 5.2. Convexity of KL Divergence**  
Let $P_{1}, P_{2}, Q_{1}, Q_{2}$ be distributions on a finite universe $\mathcal{X},$ and let $\alpha \in[0,1].$ Then,
$$
D\left(\alpha \cdot P_{1}+(1-\alpha) \cdot P_{2} \| \alpha \cdot Q_{1}+(1-\alpha) \cdot Q_{2}\right) \leq \alpha \cdot D\left(P_{1} \| Q_{1}\right)+(1-\alpha) \cdot D\left(P_{2} \| Q_{2}\right).
$$
<br>

**Proposition 5.3. Upper Bound for TV**  
$$\min \{D(P \| Q), D(Q \| P)\} \geq \frac{1}{2 \ln 2} \cdot\|P-Q\|_{1}^{2}$$
<br>

**Proposition 5.4. Lower Bound for Expected Regret for Two-Armed Bandits**  
$$\mathbb{E}[$ regret $] \geq\left(\frac{1}{2}+\varepsilon\right) \cdot n-\mathbb{E}\left[\sum_{t=1}^{n} X_{C_{t}, t}\right]$$
<br>

**Proposition 5.5. Lower Bound for Expected Regret for Two-Armed Bandits**    
$$
\mathbb{E}[\text { regret }] \geq \varepsilon \cdot \mathbb{E}\left[\left|\left\{t \mid C_{t} \neq H\right\}\right|\right]
$$
<br>

**Proposition 5.6. Lower Bound for Expected Regret for Two-Armed Bandits (Cont'd)**   
$$
\mathbb{E}\left[\left|\left\{t \mid C_{t} \neq H\right\}\right|\right] \geq \frac{n}{2} \cdot\left(1-\frac{1}{2} \cdot\left\|P_{\ell}\left(Z_{1}, \ldots, Z_{n}\right)-P_{r}\left(Z_{1}, \ldots, Z_{n}\right)\right\|_{1}\right)
$$
<br>

**Proposition 5.7. Lower Bound for Expected Regret for Two-Armed Bandits (Cont'd)**  
$$
\left\|P_{\ell}\left(Z_{1}, \ldots, Z_{n}\right)-P_{r}\left(Z_{1}, \ldots, Z_{n}\right)\right\|_{1}^{2} \leq c \cdot \varepsilon^{2} \cdot n
$$
<br>

**Proposition 5.8. Lower Bound for Expected Regret for Two-Armed Bandits (Cont'd)**  
$$
\begin{aligned}
\mathbb{E}[\text { regret }] & \geq \frac{\varepsilon n}{2} \cdot\left(1-\frac{1}{2} \cdot\left\|P_{\ell}\left(Z_{1}, \ldots, Z_{n}\right)-P_{r}\left(Z_{1}, \ldots, Z_{n}\right)\right\|_{1}\right) \\
& \geq \frac{\varepsilon n}{2} \cdot\left(1-\sqrt{c \cdot \varepsilon^{2} \cdot n}\right)\\
&=\varepsilon n \cdot\left(\frac{1}{2}-c_{0} \cdot \sqrt{\varepsilon^{2} \cdot n}\right)
\end{aligned}
$$
<br>

## Lecture 6: Differential Entropy and Gaussian Computation
**Definition 6.1. Differential Entropy**  
Let $X$ be a random variable taking values in $\mathbb{R}^{n},$ with density $p .$ Then the differential entropy of $X$ is defined to be the following integral (if it exists):
$$
h(X):=\int p(x) \cdot \log \left(\frac{1}{p(x)}\right) d x
$$
<br>

**Definition 6.2. Differential KL Divergence**  
$$
D(P \| Q):=\int p(x) \cdot \log \left(\frac{p(x)}{q(x)}\right) d x
$$
<br>

**Proposition 6.3. Change of Variables**  
Exercise 2.1 (Change of variables). Let $X$ be a random variable over $\mathbb{R}^{n}$ with associated density function $p_{X}$. Using the Jacobian for change of variables in integrals, check that
- If $c \in \mathbb{R}^{n}$ is a fixed vector, then the density function for $Y=X+c$ is given by $p_{Y}(y)=$ $p_{X}(y-c)$
- If $A \in \mathbb{R}^{n \times n}$ is a nonsingular matrix, then the density function for $Y=A X$ is given by $p_{Y}(y)=\frac{p_{X}\left(A^{-1} y\right)}{|A|},$ where $|A|$ denotes $|\operatorname{det}(A)|$
<br>

**Proposition 6.4. Change of Entropy**  
Let $X$ be a continuous random variable over $\mathbb{R}^{n} .$ Let $c \in \mathbb{R}^{n}$ and let $A \in \mathbb{R}^{n \times n}$ be a non-singular matrix. Then
- $h(X+c)=h(X)$
- $h(A X)=h(X)+\log |A|$
<br>

**Fact 6.5. Entropy of Gaussians**  
Using the fact that $Y \sim N(\mu, \Sigma)$ can be written as $Y=\Sigma^{1 / 2} X+\mu,$ where $X=N\left(0, I_{n}\right)$ (check this!) we get that
$$
h(Y)=h(X)+\log \left(\left|\Sigma^{1 / 2}\right|\right)=\frac{n}{2} \cdot \log (2 \pi \cdot e)+\frac{1}{2} \cdot \log |\Sigma|
$$
<br>

## Lecture 7: Type Method, Chernoff Bound and Sanov's Theorem
**Definition 7.1. Type**  
The type $P_{\bar{x}}$ of $\overline{\mathbf{x}},$ also called the empirical distribution of $\overline{\mathbf{x}},$ is a distribution $\hat{P}$ on $\mathcal{X},$ defined as
$$
\hat{P}(a):=\frac{\left|\left\{i: x_{i}=a\right\}\right|}{n} \quad \forall a \in \mathcal{X}
$$
We use $\mathcal{T}_{n}$ to denote the set of all types coming from sequences of length $n .$ We also use $\mathcal{C}_{P}$ to denote the set of all sequences with the type $P . \mathcal{C}_{P}$ is called the type class of $P$.
$$
\mathcal{C}_{P}:=\left\{\overline{\mathbf{x}} \in \mathcal{X}^{n} \mid P_{\overline{\mathbf{x}}}=P\right\}
$$
<br>

**Fact 7.2. Size of Type Class**    
$$
\left|\mathcal{T}_{n}\right|=\left(\begin{array}{c}
n+r-1 \\
r-1
\end{array}\right) \leq(n+1)^{r}
$$
<br>

**Proposition 7.3. Size of Type Class**  
For any type $P \in \mathcal{T}_{n}$, we have
$$
\frac{2^{n \cdot H(P)}}{(n+1)^{r}} \leq\left|\mathcal{C}_{P}\right| \leq 2^{n \cdot H(P)}
$$
<br>

**Proposition 7.4. Product Distribution**  
 Let $Q$ be any distribution on $U$ and let $Q^{n}$ the product distribution on $\mathcal{X}^{n} .$ Let $\overline{\mathbf{x}}, \overline{\mathbf{y}} \in \mathcal{X}^{n}$ be such that $P_{\overline{\mathbf{x}}}=P_{\overline{\mathbf{y}}}$. Then, $Q^{n}(\overline{\mathbf{x}})=Q^{n}(\overline{\mathbf{y}})$
<br>

**Theorem 7.5. Bound for the Probability of Type**  
For any product distribution $Q^{n}$ and type $P$ on $\mathcal{X}^{n},$ we have
$$
\frac{2^{-n \cdot D(P \| Q)}}{(n+1)^{r}} \leq \underset{\overline{\mathbf{x}} \sim Q^{n}}{\mathbb{P}}\left[P_{\overline{\mathbf{x}}}=P\right] \leq 2^{-n \cdot D(P \| Q)}
$$
<br>

**Theorem 7.6. Chernoff Bound**  
For $\overline{\mathbf{X}}=\left(X_{1}, \ldots, X_{n}\right) \sim_{Q^{n}} U^{n}$ with $Q$ the uniform distribution on $\mathcal{X}=\{0,1\},$ we have
$$
\underset{Q^{n}}{\mathbb{P}}\left[\sum_{i=1}^{n} X_{i} \geq \frac{n}{2}+\varepsilon n\right] \leq(n+1) \cdot 2^{-c \cdot n \cdot \varepsilon^{2}}
$$
<br>

**Theorem 7.7. Sanov's Theorem**  
Let $\Pi$ be a set of distributions on $\mathcal{X},$ and $|\mathcal{X}|=r .$ Then
$$
\underset{Q^{n}}{\mathbb{P}}\left[P_{\overline{\mathbf{x}}} \in \Pi\right] \leq(n+1)^{r} \cdot 2^{-n \cdot \delta}
$$
where $\delta=\inf _{P \in \Pi} D(P \| Q) .$ Moreover, if $\Pi$ is the closure of an open set and
$$
P^{*}:=\underset{P \in \Pi}{\arg \min } D(P \| Q)
$$
then
$$
\frac{1}{n} \cdot \log \left(\underset{\overline{\mathbf{x}} \sim Q^{n}}{\mathbb{P}}\left[P_{\overline{\mathbf{x}}} \in \Pi\right]\right) \rightarrow-D\left(P^{*} \| Q\right)
$$
<br>

## Lecture 8: Binary and Multiple Hypothesis Testing
**Definition 8.1. Definition of Two Errors**  
$$
\begin{array}{ll}
\alpha(T):=\underset{\overline{\mathbf{x}} \sim P_{0}^{n}}{\mathbb{P}}[T(\overline{\mathbf{x}})=1] & \text { (False Positive) } \\
\beta(T):=\underset{\frac{P}{\mathbf{x}} \sim p_{n}}{\mathbb{P}}[T(\overline{\mathbf{x}})=0] & \text { (False Negative) }
\end{array}
$$
<br>

**Proposition 8.2. Minimum of the Sum of Two Errors**  
$$
\min _{T}\{\alpha(T)+\beta(T)\}=1-\delta_{T V}\left(P_{0}^{n}, P_{1}^{n}\right)=1-\frac{1}{2} \cdot\left\|P_{0}^{n}-P_{1}^{n}\right\|_{1}
$$
<br>

**Lemma 8.3. Neyman-Pearson Lemma**  
Let $T$ be a test of the form
$$
T(\overline{\mathbf{x}})=\left\{\begin{array}{l}
1 \text { if } P_{1}^{n}(\overline{\mathbf{x}}) / P_{0}^{n}(\overline{\mathbf{x}}) \geq \Delta \\
0 \text { if } P_{0}^{n}(\overline{\mathbf{x}}) / P_{1}^{n}(\overline{\mathbf{x}})<\Delta
\end{array}\right.
$$
for some constant $\Delta>0 .$ Let $T^{\prime}$ be any other test. Then,
$$
\alpha\left(T^{\prime}\right) \geq \alpha(T) \quad \text { or } \quad \beta\left(T^{\prime}\right) \geq \beta(T)
$$
<br>

**Remark 8.4. Another Perspective on Test**  
The test $T(\overline{\mathbf{x}})$ considered above can be written in the following form
$$
\frac{P_{1}^{n}(\overline{\mathbf{x}})}{P_{0}^{n}(\overline{\mathbf{x}})} \geq \Delta \quad \Leftrightarrow \quad D\left(P_{\overline{\mathbf{x}}} \| P_{0}\right)-D\left(P_{\overline{\mathbf{x}}} \| P_{1}\right) \geq \frac{1}{n} \cdot \log \Delta
$$
We define the following sets of probability distributions.
$$
\begin{aligned}
\Pi &:=\left\{P \mid D\left(P \| P_{0}\right)-D\left(P \| P_{1}\right) \geq \frac{1}{n} \cdot \log \Delta\right\} \\
\Pi^{c} &:=\left\{P \mid D\left(P \| P_{0}\right)-D\left(P \| P_{1}\right)<\frac{1}{n} \cdot \log \Delta\right\}
\end{aligned}
$$
<br>

**Remark 8.5. Estimation of Two Errors**  
$$
\begin{array}{l}
\alpha(T)=\underset{\overline{\mathbf{x}} \sim P_{0}^{n}}{\mathbb{P}}\left[P_{\overline{\mathbf{x}}} \in \Pi\right] \approx 2^{-n \cdot D\left(P_{0}^{*} \| P_{0}\right)} \\
\beta(T)=\underset{\overline{\mathbf{x}} \sim P_{1}^{n}}{\mathbb{P}}\left[P_{\overline{\mathbf{x}}} \in \Pi^{c}\right] \approx 2^{-n \cdot D\left(P_{1}^{*} \| P_{1}\right)}
\end{array}
$$
$$
P_{0}^{*}(x)=P_{1}^{*}(x)=P^{*}=\frac{P_{0}^{\lambda}(x) \cdot P_{1}^{1-\lambda}(x)}{\sum_{y \in \mathcal{X}} P_{0}^{\lambda}(y) \cdot P_{1}^{1-\lambda}(y)}
$$
<br>

**Lemma 8.6. Fano's Inequality**  
Let $Z \rightarrow Y \rightarrow \widehat{Z}$ be a Markov chain with $Z$ taking values in a finite set $\mathcal{Z},$ and let $p_{e}=\mathbb{P}[\hat{Z} \neq Z] .$ Let $H_{2}\left(p_{e}\right)$ denote the binary entropy function computed at $p_{e} .$ Then,
$$
H_{2}\left(p_{e}\right)+p_{e} \cdot \log (|\mathcal{Z}|-1) \geq H(Z \mid \widehat{Z}) \geq H(Z \mid Y)
$$
<br>

**Proposition 8.7. Bound on the Binary Error**  
Let $V \rightarrow \overline{\mathbf{X}} \rightarrow \widehat{V}$ be the Markov chain as above. Then,
$$
p_{e}=\mathbb{P}[V \neq \widehat{V}] \geq 1-\frac{n \cdot \mathbb{E}_{v_{1}, v_{2} \in \mathcal{V}}\left[D\left(P_{v_{1}} \| P_{v_{2}}\right)\right]+1}{\log |\mathcal{V}|}
$$
<br>



## Lecture 9: Minimax's Rate and Le Cam's Method
**Definition 9.1. Minimax Risk**  
$$
\mathcal{M}_{n}(\Pi, \ell):=\inf _{\widehat{\theta}} \sup _{P \in \Pi} \underset{\mathbf{x} \sim P^{n}}{\mathbb{E}}[\ell(\widehat{\theta}(\overline{\mathbf{x}}), \theta(P))]
$$
<br>

**Lemma 9.2. Bound for the Minimax Risk**  
 Let $\left\{P_{v}\right\}_{v \in \mathcal{V}} \subseteq \Pi$ be a finite set of distributions such that $\forall v_{1}, v_{2} \in \mathcal{V}$ with $v_{1} \neq v_{2}$, $\rho\left(\theta\left(P_{v_{1}}, P_{v_{2}}\right)\right) \geq 2 \delta$. Let $\ell$ be as above. Then,
$$
\mathcal{M}(\Pi, \ell) \geq \Phi(\delta) \cdot \inf _{T}\{\mathbb{P}[T(\overline{\mathbf{x}}) \neq V]\}
$$
Note that the setting in the RHS above is exactly as considered in hypothesis testing. We think of $V$ as uniformly distributed over the set $\mathcal{V}$ and $\overline{\mathbf{x}}$ as drawn from $P_{v}^{n}$
<br>

**Exercise 9.3. Bound for Expectation**  
Let $P:\{0,1\} \rightarrow[0,1]$ be any distribution with $\mathbb{E}_{x \sim P}[x]=p(1)=\mu .$ Show that
$$
\underset{\left(x_{1}, \ldots, x_{n}\right) \sim P^{n}}{\mathbb{E}}\left[\left|\frac{1}{n} \cdot \sum_{i \in[n]} x_{i}-\mu\right|^{2}\right]=O\left(\frac{1}{n}\right)
$$
<br>

**Fact 9.4. Lower Bound for Classifier Error**  
We now consider a high-dimensional problem, where we can prove lower bounds using bounds for testing multiple hypotheses. Recall that for a random variable $V$ uniformly distrbuted over a set of hypotheses $\mathcal{V}$, the probability of of error for any classifier $T(\overline{\mathbf{x}})$ with input $\overline{\mathbf{x}}$ coming from $P_{v}^{n}$ for a randomly chosen $v \in \mathcal{V}$, is lower bounded as
$$
\mathbb{P}[T(\overline{\mathbf{x}}) \neq V] \geq 1-\frac{n \cdot \mathbb{E}_{v_{1}, v_{2} \in \mathcal{V}}\left[D\left(P_{v_{1}} \| P_{v_{2}}\right)\right]+1}{\log |\mathcal{V}|}
$$
As before, we will combine the above bound with Lemma 1.1 to prove the desired lower bound on the minimax rate using
$$
\mathcal{M}_{n}(\Pi, \ell)=\inf _{\widehat{\theta}} \sup _{P \in \Pi} \underset{\overline{\mathbf{x}} \sim P^{n}}{\mathbb{E}}[\ell(\widehat{\theta}(\overline{\mathbf{x}}), \theta(P))] \geq \Phi(\delta) \cdot \inf _{T}\{\mathbb{P}[T(\overline{\mathbf{x}}) \neq V]\}
$$
<br>

**Proposition 9.5. Gaussian Mean Estimation**  
Let $\widehat{\theta}\left(x_{1}, \ldots, x_{n}\right)=\frac{1}{n} \cdot \sum_{i \in[n]} x_{i} .$ Then, for any $\mu \in \mathbb{R}^{d},$ we have that
$$
\underset{\overline{\mathrm{X}} \sim\left(N\left(\mu, I_{d}\right)\right)^{n}}{\mathbb{E}}\left[\left\|\frac{1}{n} \sum_{i \in[n]} X_{i}-\mu\right\|_{2}^{2}\right]=\frac{d}{n}
$$
<br>

**Fact 9.6. Chain Rule on KL for Gaussians**  
$$
D\left(N\left(\mu_{1}, I_{d}\right) \| N\left(\mu_{2}, I_{d}\right)\right)=\frac{1}{2 \ln 2} \cdot\left\|\mu_{1}-\mu_{2}\right\|_{2}^{2}
$$
<br>

**Lemma 9.7. Packing Lemma**  
There exists a collection of vectors $\mathcal{V} \subseteq \mathbb{R}^{d}$ such that $|\mathcal{V}| \geq 2^{d}$ and for all $v_{1}, v_{2} \in \mathcal{V}, v_{1} \neq v_{2},$ we have
$$
\frac{1}{2} \leq\left\|v_{1}-v_{2}\right\|_{2} \leq 2
$$
<br>

**Definition 9.8. Covering and Packing of Numbers**  
Let $S$ be a set of points with a metric $\rho(\cdot, \cdot) .$ A collection of points $\mathcal{C} \subseteq S$ is called a $\delta$ -covering of $S$ (with respect to the metric $\rho$ ) if
$$
\forall x \in S, \exists y \in \mathcal{C} \quad \rho(x, y) \leq \delta
$$
$A$ set of points $\mathcal{P}$ is called a $\delta$ -packing if
$$
\forall x, y \in \mathcal{P}, x \neq y \quad \rho(x, y)>\delta
$$
The size of the minimal $\delta$ -covering, denoted as $N(\delta, S, \rho)$, is called the $\delta$ -covering number of $S$ and the size of the maximal $\delta$ -packing is called the $\delta$ -packing number. The quantity $\log N(\delta, S, \rho)$ is also called the metric entropy of $S$.
<br>

**Exercise 9.9. Bound on Packing and Covering**  
$$
M(2 \delta, S, \rho) \leq N(\delta, S, \rho) \leq M(\delta, S, \rho)
$$
<br>

**Lemma 9.10. Proof on Packing Lemma**  
Lemma 3.7. There exists a collection of vectors $\mathcal{V} \subseteq \frac{1}{\sqrt{d}} \cdot\{-1,1\}^{d}$ such that $|\mathcal{V}| \geq 2^{d / 20}$ and for all $v_{1}, v_{2} \in \mathcal{V}, v_{1} \neq v_{2},$ we have
$$
\frac{1}{2} \leq\left\|v_{1}-v_{2}\right\|_{2} \leq 2
$$
<br>


## Lecture 10: Sparse Mean Estimation and I-Projection
**Proposition 10.1. Distribution for the Difference**  
Let $\overline{\mathbf{x}} \sim\left(N\left(\mu, I_{d}\right)\right)^{n}$ be a sequence of $n$ independent samples, and let $\eta=$ $\frac{1}{n} \cdot \sum_{i=1}^{n} x_{i}$ be the empirical mean. Then $\eta-\mu$ is distributed according to the Gaussian distribution $N\left(0, \frac{1}{n} \cdot I_{d}\right)$
<br>

**Corollary 10.2. Tail Bound**  
Let $\overline{\mathbf{x}}=\left(x_{1}, \ldots, x_{n}\right) \sim\left(N\left(\left(\mu, I_{d}\right)\right)^{n}\right.$ as above. Then,
$$
\mathbb{P}\left[\exists j \in[d] \quad\left|\mu_{j}-\eta_{j}\right| \geq t\right] \leq 2 d \cdot \exp \left(-n t^{2} / 2\right)
$$
<br>

**Claim 10.3. Concentration Bound for the Estimator**  
For the estimator $\widehat{\mu}$ as above
$$
\mathbb{P}\left[\|\mu-\widehat{\mu}\|_{2} \geq t\right] \leq 2 d \cdot \exp \left(-n t^{2} / 18\right)
$$
<br>

**Claim 10.4. Expectation on the Concentration**  
$$
\underset{\overline{\mathrm{x}} \sim\left(N\left(\mu, I_{d}\right)\right)^{n}}{\mathbb{E}}\left[\|\mu-\widehat{\mu}(\overline{\mathbf{x}})\|_{2}^{2}\right]=O\left(\frac{\log d}{n}\right)
$$
<br>

**Definition 10.5. I-Projection**  
Let $\Pi$ be a closed convex set of distributions over $U$. In addition, assume that $\operatorname{Supp}(Q)=U$. Then
$$
\operatorname{Proj}_{\Pi}(Q):=\underset{P \in \Pi}{\arg \min } D(P \| Q)=P^{*}
$$
<br>

**Theorem 10.6. Lower Bound for KL Divergence**  
Let $P^{*}=\operatorname{Proj}_{\Pi}(Q) .$ Then, for all $P \in \Pi$
$$
\begin{aligned}
\operatorname{Supp}(P) & \subseteq \operatorname{Supp}\left(P^{*}\right) \\
D(P \| Q) & \geq D\left(P \| P^{*}\right)+D\left(P^{*} \| Q\right)
\end{aligned}
$$
<br>

**Definition 10.7. Linear Family of Distributions**  
For any given real-valued functions $f_{1}, f_{2}, \ldots, f_{k}$ on $\mathcal{X}$ and $\alpha_{1}, \alpha_{2}, \ldots, \alpha_{k} \in \mathbb{R},$ the set
$$
\mathcal{L}=\left\{P \mid \sum_{x \in \mathcal{X}} p(x) \cdot f_{i}(x)=\underset{x \sim P}{\mathbb{E}}\left[f_{i}(x)\right]=\alpha_{i}, \forall i \in[k]\right\}
$$
is called a linear family of distributions.
<br>

**Lemma 10.8. Tight Bound for Linear Family**  
Let $\mathcal{L}$ be a linear family given by
$$
\mathcal{L}=\left\{P: \sum_{x \in U} p(x) \cdot f_{i}(x)=\alpha_{i}, i \in[k]\right\}
$$
and $\bigcup_{P \in \mathcal{L}} \operatorname{Supp}(P)=U .$ Let $P^{*}=\operatorname{Proj}_{\mathcal{L}}(Q) .$ Then, for all $P \in \mathcal{L}$
- There exists $\beta>0$ such that for $t \in[-\beta, 0], P_{t}=t P+(1-t) P^{*} \in \mathcal{L}$.
- $D(P \| Q)=D\left(P \| P^{*}\right)+D\left(P^{*} \| Q\right)$

Then the I-Projection $P^{*}$ of $Q$ onto $\mathcal{L}$ satisfies the Pythagorean identity
$$
D(P \| Q)=D\left(P \| P^{*}\right)+D\left(P^{*} \| Q\right)
$$
<br>

**Definition 10.9. Exponential Family**  
Let $Q$ be a given distribution. For any given functions $g_{1}, g_{2}, \ldots, g_{k}$ on $\mathcal{X},$ the set
$\mathcal{E}_{Q}\left(g_{1}, \ldots, g_{k}\right):=\left\{P \mid \exists \lambda_{1}, \ldots, \lambda_{k} \in \mathbb{R} \forall x \in \mathcal{X}, \quad p(x)=c \cdot q(x) \cdot \exp \left(\sum_{i=1}^{k} \lambda_{i} g_{i}(x)\right)\right\}$
is called an exponential family of distributions.
<br>

## Lecture 11: Matrix Scaling and Error-Correcting Codes
**Definition 11.1. Rate**  
We define the rate of a code as above to be
$$
R:=\frac{\log M}{n} \text{   (bits per transmission)}.
$$

We say that a rate $R$ is achievable for a channel, if there exists a sequence of codes for $n \geq n_{0}$ with rates at least $R$ and error probabilities $p_{e}^{(n)}$ such that $p_{e}^{(n)} \rightarrow 0$ as $n \rightarrow \infty$. We define the maximum achievable rate for a channel as $R^{*}=\sup \{R \mid R$ is achievable $\}$.
<br>

**Definition 11.2. Channel Capacity**  
$$
C:=\max _{P(X)} I(X ; Y)
$$
<br>

**Theorem 11.3. Channel Capacity and Best Rate**  
For any discrete memoryless channel, we have $R^{*}=C$.
<br>

**Proposition 11.4. Channel Capacity as an Upper Bound**  
Let $R$ be any achievable rate for a given channel with capacity $\mathrm{C}$. Then, $R \leq \mathrm{C}$.
<br>

**Claim 11.5. Upper Bound on Expected Error Probability**  
Let $C$ be random code constructed as above in the random setting. Then
$$
\underset{C}{\mathbb{E}}\left[p_{e}\right] \leq n \cdot 2^{-n \cdot D(p+\delta \| p)}+2^{n R} \cdot n \cdot 2^{-n \cdot D\left(p+\delta \| \frac{1}{2}\right)}
$$
where $D(p \| q)$ denotes $D(\operatorname{Bern}(p) \| \operatorname{Bern}(q))$ as usual.
<br>

## Lecture 12: Linear Codes and Explicit Constructions
**Definition 12.1. Parity Check Matrix**  
Definition 1.1 (Parity Check Matrix). Let $b_{1}, \ldots, b_{n-k} \in \mathbb{F}_{q}^{n}$ be a basis for the null space of $G^{T}$ corresponding to a linear code
C. Then $H \in \mathbb{F}_{q}^{(n-k) \times n}$, defined by
$$
H^{T}=\left[\begin{array}{l|l|l|l}
b_{1} & b_{2} & \ldots & b_{n-k}
\end{array}\right]
$$
is called a parity check matrix for $\mathrm{C}$.
<br>

**Proposition 12.2. Decoding Algorithm with Vanishing Probability**  
Let $H \in \mathbb{F}_{2}^{m \times n}$ and Decom $: \mathbb{F}_{2}^{m} \rightarrow \mathbb{F}_{2}^{n}$ define a linear compression scheme as above. Then the linear code $\mathrm{C}=\{x \mid H x=0\}$ has a decoding algorithm with vanishing probability of error, for transmission through the channel $B S C(p)$.
<br>

**Definition 12.3. Polarizing**  
An invertible matrix $P \in \mathbb{F}_{2}^{n \times n}$ is said to be $(\varepsilon, \tau)$ -polarizing for the random variable $Z \sim(\operatorname{Bern}(p))^{n}$ if for
$$
W=P Z \quad \text { and } \quad S_{\tau}=\left\{i \in[n] \mid H\left(W_{i} \mid W_{<i}\right) \geq \tau\right\}
$$
we have that $\left|S_{\tau}\right| \leq\left(H_{2}(p)+\varepsilon\right) \cdot n$
<br>

**Theorem 12.4. Speed of Polarization**  
For all $\gamma>0,$ there exist constant $\alpha \in(0,1), \beta>0$ such that for all $t \in \mathbb{N},$ we have
$$
\mathbb{P}\left[X_{t} \in\left(\gamma^{t}, 1-\gamma^{t}\right)\right] \leq \beta \cdot \alpha^{t}
$$
<br>


## Lecture 13: Adversarial Error Models and Reed-Solomon Codes
**Definition 13.1. Distance of a Code**  
Let $C \subseteq \mathcal{X}^{n}$ be a code. We define the distance of a code $\Delta(C)$ as
$$
\Delta(C):=\min _{x, y \in C \atop x \neq y} \Delta(x, y) .
$$
The distance can be used to understand the number of errors one can correct. Note that there are no probabilities in the error correcting model. Thus, we take the meaning of "correcting" $y$ to finding the closest $x_{0} \in C$ i.e., $x_{0}=\operatorname{argmin}_{z \in C}(\Delta(y, z))$. The questions is if this correctly recovers the $x$ that was sent (and corrupted to $y$ by at most $t$ errors).
<br>

**Proposition 13.2. Correction of Errors**  
$A$ code $C \subseteq \mathcal{X}^{n}$ can correct t errors if and only if $\Delta(C) \geq 2 t+1$
<br>

**Proposition 13.3. Bound on Code Length**  
Let $C \subseteq \mathbb{F}_{2}^{n}$ be any distance-3 code, i.e., $\Delta(C) \geq 3$. Then
$$
|C| \leq \frac{2^{n}}{n+1}
$$
<br>

**Proposition 13.4. Hamming Bound**  
Let $C \subseteq \mathcal{X}^{n}$ be any code with $\Delta(C) \geq d$. Then
$$
|C| \leq \frac{|\mathcal{X}|^{n}}{\left|B\left(\cdot,\left\lfloor\frac{d-1}{2}\right\rfloor\right)\right|}
$$
where $|B(\cdot, r)|$ denotes the size of a ball $B(x, r),$ which is the same for all $x \in \mathcal{X}^{n}$.
<br>

**Remark 13.5. Hamming Bound in terms of Entropy**  
Remark 1.8. The Hamming bound also gives us a bound on the rate of the code in terms of entropy. Let $\mathcal{X}=\mathbb{F}_{2}, d=\delta n$ for $\delta \leq \frac{1}{2},$ and let $|C|=2^{k} .$ Since $|B(\cdot, r)|=\sum_{i=1}^{r}\left(\begin{array}{l}n \\ i\end{array}\right) \geq \frac{1}{n} \cdot 2^{n} \cdot H_{2}\left(\frac{r}{n}\right)$ for $r \leq \frac{n}{2}$ (why?), we have
$$
2^{k} \leq n \cdot 2^{n-H_{2}(\delta / 2)} \Rightarrow \frac{k}{n} \leq 1-H_{2}(\delta / 2)+o(1)
$$
<br>

**Theorem 13.6. Singleton Bound**  
Let $C \subseteq \mathcal{X}^{n}$ be a distance-d code, with $|C| \geq|\mathcal{X}|^{k}$. Then
$$
d \leq n-k+1
$$
<br>

**Definition 13.7. Reed-Solomon Code**  
Definition 2.1 (Reed-Solomon Code). Assume $q \geq n$ and fix $S=\left\{a_{1}, \ldots, a_{n}\right\} \subseteq \mathbb{F}_{q}$, distinct
s.t. $|S|=n .$ For each message $\left(m_{0}, \ldots, m_{k-1}\right) \in \mathbb{F}_{q}^{k}$, consider the polynomial $f_{m}(X)=m_{0}+m_{1}X+\cdots+m_{k-1} X^{k-1} .$ Then the Reed-Solomon Code is defined by its encoding as:
$$
C\left(m_{0}, \ldots, m_{k-1}\right)=\left(f_{m}\left(a_{1}\right), \ldots, f_{m}\left(a_{n}\right)\right)
$$
Alternatively, we can also define the code directly as the subspace
$$
C=\left\{\left(f\left(a_{1}\right), \ldots, f\left(a_{n}\right)\right) \mid f \in \mathbb{F}_{q}^{\leq(k-1)}[X]\right\}
$$
Let's compute the distance of the Reed-Solomon Code:
<br>

**Claim 13.8. Distance of Reed-Solomon Code**  
$$
\Delta(C) \geq n-k+1
$$
<br>

**Remark 13.9. Linearity of Reed-Solomon Code**  
The Reed-Solomon Code is a linear code, as can be seen from the encoding map
$$
C\left(m_{0}, \ldots, m_{k-1}\right)=\left[\begin{array}{ccccc}
1 & a_{1} & a_{1}^{2} & \ldots & a_{1}^{k-1} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
1 & a_{n} & a_{n}^{2} & \ldots & a_{n}^{k-1}
\end{array}\right]\left[\begin{array}{c}
m_{0} \\
m_{1} \\
\vdots \\
m_{k-1}
\end{array}\right]
$$
<br>

**Algorithm 12.10 Unique Decoding for Reed-Solomon Codes**  
**Input**: $\left\{\left(a_{i}, y_{i}\right)\right\}_{i=1, \ldots, n}$
- Find $e, g \in \mathbb{F}_{q}[X]$ such that $E \neq 0, \operatorname{deg}(e) \leq t, \operatorname{deg}(g) \leq k-1+t$
$$
\forall i \in[n] \quad g\left(a_{i}\right)=y_{i} \cdot e\left(a_{i}\right)
$$
- Output $\frac{g}{\rho}$
<br>

**Lemma 12.11. Existence for Pairs**  
There exists $(E, Q)$ that satisfies the conditions in Step 1 of the algorithm.
<br>

**Lemma 12.12. Equality from Solutions**  
For any two solutions $\left(g_{1}, e_{1}\right)$ and $\left(g_{2}, e_{2}\right)$ that satisfy the conditions in Step $1,$
$$
\frac{g_{1}}{e_{1}}=\frac{g_{2}}{e_{2}}
$$
<br>
