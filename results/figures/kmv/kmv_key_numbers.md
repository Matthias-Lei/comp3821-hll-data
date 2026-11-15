# K-Minimum Values: key numbers

- **Merge:** not benchmarked for this sketch.
- **Exact below k:** every seed gave exactly n in **2063 of 2063** stream and budget groups with n < k.

## Predictions inside the measured 95% interval (n >= 100, where the theory is judged)

| Streams, budget | RMSE | Bias |
|---|---|---|
| synthetic, team observations generator, 1 KiB | 356 of 363 | 298 of 363 |
| synthetic, team observations generator, 4 KiB | 339 of 363 | 363 of 363 |
| synthetic, team observations generator, 8 KiB | 361 of 363 | 360 of 363 |
| synthetic, team observations generator, 16 KiB | 363 of 363 | 358 of 363 |
| real SQL query results, 1 KiB | 46 of 52 | 51 of 52 |
| real SQL query results, 4 KiB | 49 of 52 | 51 of 52 |
| real SQL query results, 8 KiB | 49 of 52 | 49 of 52 |
| real SQL query results, 16 KiB | 49 of 52 | 51 of 52 |
| synthetic, team distribution generator, 1 KiB | 157 of 164 | 154 of 164 |
| synthetic, team distribution generator, 4 KiB | 155 of 164 | 154 of 164 |
| synthetic, team distribution generator, 8 KiB | 157 of 164 | 159 of 164 |
| synthetic, team distribution generator, 16 KiB | 157 of 164 | 157 of 164 |

## By distribution of repeats (all budgets)

| Distribution | RMSE | Bias | Median measured / predicted RMSE |
|---|---|---|---|
| bernoulli | 51 of 52 | 50 of 52 | 1.019 |
| bernoulli-p=0.02 | 51 of 52 | 50 of 52 | 1.019 |
| bernoulli-p=0.3 | 51 of 52 | 50 of 52 | 1.019 |
| beta | 20 of 20 | 19 of 20 | 1.048 |
| beta-alpha=2-beta=98 | 20 of 20 | 19 of 20 | 1.048 |
| beta-alpha=8-beta=2 | 20 of 20 | 19 of 20 | 1.048 |
| binomial | 47 of 48 | 46 of 48 | 1.024 |
| binomial-n=30-p=0.2 | 47 of 48 | 46 of 48 | 1.024 |
| binomial-n=365-p=0.05 | 43 of 44 | 43 of 44 | 1.024 |
| chi_squared | 20 of 20 | 19 of 20 | 1.048 |
| chi_squared-df=1 | 24 of 24 | 23 of 24 | 1.048 |
| chi_squared-df=10 | 20 of 20 | 19 of 20 | 1.048 |
| exponential | 24 of 24 | 23 of 24 | 1.048 |
| exponential-lambda=0.005 | 24 of 24 | 23 of 24 | 1.048 |
| exponential-lambda=0.1 | 24 of 24 | 23 of 24 | 1.048 |
| gamma | 24 of 24 | 23 of 24 | 1.048 |
| gamma-alpha=0.5-lambda=0.1 | 24 of 24 | 23 of 24 | 1.048 |
| gamma-alpha=2-lambda=0.001 | 24 of 24 | 23 of 24 | 1.048 |
| geometric | 51 of 52 | 50 of 52 | 1.019 |
| geometric-p=0.05 | 43 of 44 | 43 of 44 | 1.024 |
| geometric-p=0.3 | 51 of 52 | 50 of 52 | 1.019 |
| lognormal | 28 of 28 | 27 of 28 | 1.024 |
| lognormal-mu=11-sigma=0.7 | 24 of 24 | 23 of 24 | 1.048 |
| lognormal-mu=5.3-sigma=0.5 | 24 of 24 | 23 of 24 | 1.048 |
| negative_binomial | 43 of 44 | 43 of 44 | 1.024 |
| negative_binomial-k=2-p=0.2 | 47 of 48 | 46 of 48 | 1.024 |
| negative_binomial-k=5-p=0.05 | 36 of 36 | 35 of 36 | 1.052 |
| normal | 20 of 20 | 19 of 20 | 1.048 |
| normal-mu=170-sigma=10 | 20 of 20 | 19 of 20 | 1.048 |
| normal-mu=8000-sigma=3000 | 20 of 20 | 19 of 20 | 1.048 |
| pareto | 28 of 28 | 27 of 28 | 1.024 |
| pareto-alpha=1.16-lambda=10000 | 39 of 40 | 39 of 40 | 1.048 |
| pareto-alpha=1.5-lambda=1000 | 36 of 36 | 35 of 36 | 1.052 |
| poisson | 145 of 164 | 141 of 164 | 0.978 |
| poisson-lambda=4 | 47 of 48 | 46 of 48 | 1.024 |
| poisson-lambda=50 | 39 of 40 | 39 of 40 | 1.048 |
| t | 20 of 20 | 19 of 20 | 1.048 |
| t-df=10 | 20 of 20 | 19 of 20 | 1.048 |
| t-df=3 | 20 of 20 | 19 of 20 | 1.048 |
| uniform | 20 of 20 | 19 of 20 | 1.048 |
| uniform-a=0-b=1000000000 | 20 of 20 | 19 of 20 | 1.048 |
| uniform-a=0-b=86400 | 20 of 20 | 19 of 20 | 1.048 |
| real SQL | 193 of 208 | 202 of 208 | 0.977 |
