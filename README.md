# LLR_MCinHEP
PY3 notebooks for Monte Carlo methods in HEP course at Ecole Polytechnique 


# Exercises 

**1)** Generate pseudo-random numbers distributed according to an exponentil pdf:

$$ f(x; \lambda) = \lambda e^{-\lambda x}, \quad \lambda > 0$$
- With the hit-or-miss method 
- With the Inverse Cumulative Distribution Function method 

<br/><br/>

**2)** Estimate numerically, via Monte Carlo integration, the Cumulative Distribution Function of the Poisson pdf 

$$ P(k; \lambda) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad \lambda=10, \quad k \in \{ 0, 1, 2, 3, ..., 20\} $$

-  Where $CDF(k;\lambda) = \int_{0}^{k} P(k; \lambda) dk$


<br/><br/>

**3)**  Vector bosons $1^{-}$ are characterized by an angular distribution in the coordinate space $\theta \in [0, \pi], \phi \in [0, 2\pi]$ which has the following expression:


$$  F(\theta, \phi) = \frac{3}{4\pi} \left[ \frac{1}{2}(1-\alpha) + \frac{1}{2}(3\alpha -1)\cos^2(\theta) - \beta \sin^2(\theta)\cos(2\phi) - \sqrt{2}\gamma \sin(2\theta)\cos(\phi) \right]$$

The model parameters are theoretically fixed at the following values:
$$ \alpha=0.65 \quad,\quad \beta=0.06 \quad,\quad  \gamma=−0.18$$

Generate 100.000  Monte Carlo events distributed according to the previous law and perform the following exercises:

- Determine the values of $\alpha, \beta, \gamma$ with the extended maximum likelihood method (iMinuit).
- Test the Central Limit Theorem repeating $N=1000$ experiments each of $n=50000$ events
- Make an hypothesis test using the Likelihood ratio against a uniform distribution ($0^{-}$)


**4)** Use MadGraph to generate pseudorandom events of W boson production and decay to a muon-neutrino pair at the LHC:  $p p \rightarrow \mu\nu$. The nominal W boson mass is `MW=80.387 GeV`, generate 50000 events from 10 mass points from -2 to 2 GeV with respect to the nominal mass Use the events generated at mass point `MW=80.387 GeV` as your data.
- For each mass point, use the $p_T(\mu)$ distribution to estimate the W boson mass. As a metric use the $\chi^2$ test statistic $\chi^2 = \sum_{bin=1}^{nbins} (Obs_{i} - Exp_{i})^2 / Exp_i$
- Build the transverse mass of the muon-neutrino system $m_T = \sqrt{2p_{T}^{\mu}p_T^{\nu}(1 - cos\phi)}$ and repeat the same $\chi^2$ test. Which observable is more sensitive to modification of the $W$ boson masss?

```
import model loop_sm
generate p p > mu+ vm [QCD] @0
output Wboson

launch -n 78p387
set MW 78.387
set nevents 50000
launch -n 79p387
set MW 79.387
set nevents 50000
launch -n 80p387
set MW 80.387
set nevents 50000
launch -n 81p387
set MW 81.387
set nevents 50000
launch -n 82p387
set MW 82.387
set nevents 50000
```
