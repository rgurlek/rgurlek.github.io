---
title: "sine-NHPP"
excerpt: "Python software for predicting customer arrivals with sine waves. Cycles are
automatically discovered and coefficients are estimated accordingly. <br/><img src='/images/sineNHPP.png'>"
collection: software
---

sine-NHPP is a Python software for predicting customer arrivals with sine waves. Cycles are
automatically discovered and coefficients are estimated accordingly. It implements the estimation procedure from [Chen et al. (2023)](#suggested-citations).
The installation guide can be found [here](https://github.com/rgurlek/sine-NHPP#configuring-the-python-environment).
[This tutorial](https://rgurlek.github.io/sine-NHPP/) demonstrates how to estimate the arrival rate of customers from a simulated dataset.

Please refer to Appendix A of [Chen et al. (2023)](#suggested-citations) for details of the procedure,
which is a simpler variant of the one proposed in [Chen, Lee, and Negahban (2019)](#suggested-citations).

![](/images/FAIR.png){:class="img-responsive"}

## Suggested citations
- Chen, Gurlek, Lee, Shen (2023): [Can customer arrival rates be modelled by sine waves?](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3125120) (Joint issue in *Service Science* and *Stochastic Systems*, forthcoming)

- Chen, Lee, Negahban (2019): [Super-resolution estimation of cyclic arrival rates](https://projecteuclid.org/journals/annals-of-statistics/volume-47/issue-3/Super-resolution-estimation-of-cyclic-arrival-rates/10.1214/18-AOS1736.full) (*Annals of Statistics*  47:3:1754-1775)