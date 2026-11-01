# Stock Investment Optimisation with Metaheuristics

Choosing how many shares to buy across **18 bank stocks** to minimise total cost under a minimum-portfolio-size constraint. The problem is formulated as an objective function and solved with nature-inspired optimisers: **Particle Swarm Optimisation (PSO)**, **Grey Wolf Optimiser (GWO)** and **Multi-Verse Optimiser (MVO)**.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white)

## Problem formulation

```python
def new_obj(L):                       # L = shares to buy for each of the 18 banks (0–5)
    price = numpy.array([...])        # share prices
    L = numpy.round(L)                # whole shares only
    total = numpy.sum(L * price)
    if L.sum() < 10:                  # constraint: buy at least 10 shares
        return 9999999                # penalty
    return total
```

- **Decision variables:** 18 integers in [0, 5]
- **Constraint handling:** a penalty for portfolios with fewer than 10 shares
- **Optimisers:** PSO, GWO and MVO, each with a population of 30 over 50 iterations and repeated runs

## Results

The notebook compares the optimisers using convergence curves and box plots (see the timestamped result folders in `EvoloPy-master/`). The best solution found converges on the cheapest feasible mix of shares, buying 5 shares each of the two lowest-priced banks.

## Project structure

```
Precpective.ipynb        → problem definition, experiment runs and result analysis
EvoloPy-master/          → EvoloPy optimisation framework, extended with the custom objective
  benchmarks.py          → custom `new_obj` objective added here
  2023-06-06-*/          → experiment outputs (CSV results, convergence and box plots)
```

## Run it

```bash
pip install -r EvoloPy-master/requirements.txt
jupyter notebook Precpective.ipynb
```

## Credits and license

The optimisers come from **[EvoloPy](https://github.com/7ossam81/EvoloPy)** by Faris et al., included under its [Apache 2.0 license](EvoloPy-master/LICENSE.txt). My contribution is the problem formulation, the custom objective, the experiments and the analysis, which are released under [MIT](LICENSE).
