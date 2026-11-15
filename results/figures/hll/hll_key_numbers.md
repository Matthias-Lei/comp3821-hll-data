# HyperLogLog: key numbers

- **Merge:** the register-wise maximum of the two halves gives the same estimate as the whole stream in **231,680 of 231,680** trials.

## Predictions inside the measured 95% interval (n >= 100, where the theory is judged)

| Streams, budget | RMSE | Bias |
|---|---|---|
| synthetic, team observations generator, 1 KiB | 312 of 335 | 335 of 335 |
| synthetic, team observations generator, 4 KiB | 314 of 327 | 327 of 327 |
| synthetic, team observations generator, 8 KiB | 261 of 346 | 303 of 346 |
| synthetic, team observations generator, 16 KiB | 192 of 342 | 211 of 342 |
| real SQL query results, 1 KiB | 34 of 40 | 39 of 40 |
| real SQL query results, 4 KiB | 43 of 49 | 47 of 49 |
| real SQL query results, 8 KiB | 44 of 47 | 43 of 47 |
| real SQL query results, 16 KiB | 40 of 47 | 42 of 47 |
| synthetic, team distribution generator, 1 KiB | 139 of 159 | 156 of 159 |
| synthetic, team distribution generator, 4 KiB | 130 of 144 | 140 of 144 |
| synthetic, team distribution generator, 8 KiB | 129 of 134 | 125 of 134 |
| synthetic, team distribution generator, 16 KiB | 133 of 146 | 130 of 146 |

## By distribution of repeats (all budgets)

| Distribution | RMSE | Bias | Median measured / predicted RMSE |
|---|---|---|---|
| bernoulli | 36 of 47 | 43 of 47 | 0.952 |
| bernoulli-p=0.02 | 36 of 47 | 43 of 47 | 0.952 |
| bernoulli-p=0.3 | 36 of 47 | 43 of 47 | 0.952 |
| beta | 16 of 20 | 16 of 20 | 0.959 |
| beta-alpha=2-beta=98 | 16 of 20 | 16 of 20 | 0.959 |
| beta-alpha=8-beta=2 | 16 of 20 | 16 of 20 | 0.959 |
| binomial | 34 of 43 | 39 of 43 | 0.956 |
| binomial-n=30-p=0.2 | 34 of 43 | 39 of 43 | 0.956 |
| binomial-n=365-p=0.05 | 32 of 39 | 35 of 39 | 0.957 |
| chi_squared | 16 of 20 | 16 of 20 | 0.959 |
| chi_squared-df=1 | 19 of 23 | 19 of 23 | 0.961 |
| chi_squared-df=10 | 16 of 20 | 16 of 20 | 0.959 |
| exponential | 19 of 23 | 19 of 23 | 0.961 |
| exponential-lambda=0.005 | 19 of 23 | 19 of 23 | 0.961 |
| exponential-lambda=0.1 | 19 of 23 | 19 of 23 | 0.961 |
| gamma | 19 of 23 | 19 of 23 | 0.961 |
| gamma-alpha=0.5-lambda=0.1 | 19 of 23 | 19 of 23 | 0.961 |
| gamma-alpha=2-lambda=0.001 | 19 of 23 | 19 of 23 | 0.961 |
| geometric | 36 of 47 | 43 of 47 | 0.952 |
| geometric-p=0.05 | 32 of 39 | 35 of 39 | 0.957 |
| geometric-p=0.3 | 36 of 47 | 43 of 47 | 0.952 |
| lognormal | 22 of 26 | 22 of 26 | 0.954 |
| lognormal-mu=11-sigma=0.7 | 19 of 23 | 19 of 23 | 0.961 |
| lognormal-mu=5.3-sigma=0.5 | 19 of 23 | 19 of 23 | 0.961 |
| negative_binomial | 32 of 39 | 35 of 39 | 0.957 |
| negative_binomial-k=2-p=0.2 | 34 of 43 | 39 of 43 | 0.956 |
| negative_binomial-k=5-p=0.05 | 26 of 31 | 27 of 31 | 0.956 |
| normal | 16 of 20 | 16 of 20 | 0.959 |
| normal-mu=170-sigma=10 | 16 of 20 | 16 of 20 | 0.959 |
| normal-mu=8000-sigma=3000 | 16 of 20 | 16 of 20 | 0.959 |
| pareto | 22 of 26 | 22 of 26 | 0.954 |
| pareto-alpha=1.16-lambda=10000 | 28 of 35 | 31 of 35 | 0.952 |
| pareto-alpha=1.5-lambda=1000 | 26 of 31 | 27 of 31 | 0.956 |
| poisson | 120 of 155 | 145 of 155 | 0.927 |
| poisson-lambda=4 | 34 of 43 | 39 of 43 | 0.956 |
| poisson-lambda=50 | 28 of 35 | 31 of 35 | 0.952 |
| t | 16 of 20 | 16 of 20 | 0.959 |
| t-df=10 | 16 of 20 | 16 of 20 | 0.959 |
| t-df=3 | 16 of 20 | 16 of 20 | 0.959 |
| uniform | 16 of 20 | 16 of 20 | 0.959 |
| uniform-a=0-b=1000000000 | 16 of 20 | 16 of 20 | 0.959 |
| uniform-a=0-b=86400 | 16 of 20 | 16 of 20 | 0.959 |
| real SQL | 161 of 183 | 171 of 183 | 0.983 |
