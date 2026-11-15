# Bloom filter: key numbers

- **Merge:** not benchmarked for this sketch.

## Predictions inside the measured 95% interval (n >= 100, where the theory is judged)

| Streams, budget | RMSE | Bias |
|---|---|---|
| synthetic, team observations generator, 1 KiB | 274 of 274 | 274 of 274 |
| synthetic, team observations generator, 4 KiB | 297 of 297 | 297 of 297 |
| synthetic, team observations generator, 8 KiB | 325 of 326 | 284 of 326 |
| synthetic, team observations generator, 16 KiB | 313 of 332 | 332 of 332 |
| real SQL query results, 1 KiB | 34 of 38 | 37 of 38 |
| real SQL query results, 4 KiB | 43 of 48 | 45 of 48 |
| real SQL query results, 8 KiB | 46 of 48 | 46 of 48 |
| real SQL query results, 16 KiB | 47 of 51 | 50 of 51 |
| synthetic, team distribution generator, 1 KiB | 120 of 128 | 124 of 128 |
| synthetic, team distribution generator, 4 KiB | 151 of 164 | 156 of 164 |
| synthetic, team distribution generator, 8 KiB | 152 of 164 | 155 of 164 |
| synthetic, team distribution generator, 16 KiB | 154 of 164 | 154 of 164 |

## By distribution of repeats (all budgets)

| Distribution | RMSE | Bias | Median measured / predicted RMSE |
|---|---|---|---|
| bernoulli | 38 of 39 | 38 of 39 | 1.005 |
| bernoulli-p=0.02 | 38 of 39 | 38 of 39 | 1.005 |
| bernoulli-p=0.3 | 38 of 39 | 38 of 39 | 1.005 |
| beta | 20 of 20 | 19 of 20 | 1.021 |
| beta-alpha=2-beta=98 | 20 of 20 | 19 of 20 | 1.021 |
| beta-alpha=8-beta=2 | 20 of 20 | 19 of 20 | 1.021 |
| binomial | 38 of 39 | 38 of 39 | 1.005 |
| binomial-n=30-p=0.2 | 38 of 39 | 38 of 39 | 1.005 |
| binomial-n=365-p=0.05 | 38 of 39 | 38 of 39 | 1.005 |
| chi_squared | 20 of 20 | 19 of 20 | 1.021 |
| chi_squared-df=1 | 24 of 24 | 23 of 24 | 1.018 |
| chi_squared-df=10 | 20 of 20 | 19 of 20 | 1.021 |
| exponential | 24 of 24 | 23 of 24 | 1.018 |
| exponential-lambda=0.005 | 24 of 24 | 23 of 24 | 1.018 |
| exponential-lambda=0.1 | 24 of 24 | 23 of 24 | 1.018 |
| gamma | 24 of 24 | 23 of 24 | 1.018 |
| gamma-alpha=0.5-lambda=0.1 | 24 of 24 | 23 of 24 | 1.018 |
| gamma-alpha=2-lambda=0.001 | 24 of 24 | 23 of 24 | 1.018 |
| geometric | 38 of 39 | 38 of 39 | 1.005 |
| geometric-p=0.05 | 38 of 39 | 38 of 39 | 1.005 |
| geometric-p=0.3 | 38 of 39 | 38 of 39 | 1.005 |
| lognormal | 27 of 28 | 27 of 28 | 1.016 |
| lognormal-mu=11-sigma=0.7 | 24 of 24 | 23 of 24 | 1.018 |
| lognormal-mu=5.3-sigma=0.5 | 24 of 24 | 23 of 24 | 1.018 |
| negative_binomial | 38 of 39 | 38 of 39 | 1.005 |
| negative_binomial-k=2-p=0.2 | 38 of 39 | 38 of 39 | 1.005 |
| negative_binomial-k=5-p=0.05 | 34 of 35 | 34 of 35 | 1.005 |
| normal | 20 of 20 | 19 of 20 | 1.021 |
| normal-mu=170-sigma=10 | 20 of 20 | 19 of 20 | 1.021 |
| normal-mu=8000-sigma=3000 | 20 of 20 | 19 of 20 | 1.021 |
| pareto | 27 of 28 | 27 of 28 | 1.016 |
| pareto-alpha=1.16-lambda=10000 | 36 of 37 | 36 of 37 | 1.005 |
| pareto-alpha=1.5-lambda=1000 | 34 of 35 | 34 of 35 | 1.005 |
| poisson | 63 of 65 | 64 of 65 | 1.013 |
| poisson-lambda=4 | 38 of 39 | 38 of 39 | 1.005 |
| poisson-lambda=50 | 36 of 37 | 36 of 37 | 1.005 |
| t | 20 of 20 | 19 of 20 | 1.021 |
| t-df=10 | 20 of 20 | 19 of 20 | 1.021 |
| t-df=3 | 20 of 20 | 19 of 20 | 1.021 |
| uniform | 20 of 20 | 19 of 20 | 1.021 |
| uniform-a=0-b=1000000000 | 20 of 20 | 19 of 20 | 1.021 |
| uniform-a=0-b=86400 | 20 of 20 | 19 of 20 | 1.021 |
| real SQL | 170 of 185 | 178 of 185 | 0.998 |

## Saturation

| Budget | Predicted saturation n | Smallest n with a saturated seed |
|---|---|---|
| 1 KiB | 24,606 | 21,779 |
| 4 KiB | 113,565 | 100,000 |
| 8 KiB | 242,272 | 212,140 |
| 16 KiB | 514,829 | 468,554 |
