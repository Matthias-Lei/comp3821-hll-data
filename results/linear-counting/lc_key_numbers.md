# Linear Counting: key numbers

- **Merge:** the OR of the two halves' bitmaps equals the bitmap of the whole stream in **231,680 of 231,680** trials.

## Predictions inside the measured 95% interval (n >= 100, no seed saturated)

| Streams, budget | RMSE | Bias |
|---|---|---|
| synthetic, team observations generator, 1 KiB | 249 of 291 | 291 of 291 |
| synthetic, team observations generator, 4 KiB | 284 of 326 | 309 of 326 |
| synthetic, team observations generator, 8 KiB | 265 of 343 | 343 of 343 |
| synthetic, team observations generator, 16 KiB | 335 of 356 | 341 of 356 |
| real SQL query results, 1 KiB | 42 of 47 | 45 of 47 |
| real SQL query results, 4 KiB | 45 of 49 | 47 of 49 |
| real SQL query results, 8 KiB | 47 of 51 | 49 of 51 |
| real SQL query results, 16 KiB | 45 of 52 | 50 of 52 |
| synthetic, team distribution generator, 1 KiB | 145 of 160 | 152 of 160 |
| synthetic, team distribution generator, 4 KiB | 154 of 164 | 155 of 164 |
| synthetic, team distribution generator, 8 KiB | 147 of 164 | 160 of 164 |
| synthetic, team distribution generator, 16 KiB | 149 of 164 | 164 of 164 |

## By distribution of repeats (all budgets)

| Distribution | RMSE | Bias | Median measured / predicted RMSE |
|---|---|---|---|
| bernoulli | 39 of 45 | 43 of 45 | 0.960 |
| bernoulli-p=0.02 | 39 of 45 | 43 of 45 | 0.960 |
| bernoulli-p=0.3 | 39 of 45 | 43 of 45 | 0.960 |
| beta | 17 of 20 | 20 of 20 | 0.957 |
| beta-alpha=2-beta=98 | 17 of 20 | 20 of 20 | 0.957 |
| beta-alpha=8-beta=2 | 17 of 20 | 20 of 20 | 0.957 |
| binomial | 38 of 44 | 42 of 44 | 0.962 |
| binomial-n=30-p=0.2 | 38 of 44 | 42 of 44 | 0.962 |
| binomial-n=365-p=0.05 | 36 of 42 | 40 of 42 | 0.961 |
| chi_squared | 17 of 20 | 20 of 20 | 0.957 |
| chi_squared-df=1 | 21 of 24 | 24 of 24 | 0.951 |
| chi_squared-df=10 | 17 of 20 | 20 of 20 | 0.957 |
| exponential | 21 of 24 | 24 of 24 | 0.951 |
| exponential-lambda=0.005 | 21 of 24 | 24 of 24 | 0.951 |
| exponential-lambda=0.1 | 21 of 24 | 24 of 24 | 0.951 |
| gamma | 21 of 24 | 24 of 24 | 0.951 |
| gamma-alpha=0.5-lambda=0.1 | 21 of 24 | 24 of 24 | 0.951 |
| gamma-alpha=2-lambda=0.001 | 21 of 24 | 24 of 24 | 0.951 |
| geometric | 39 of 45 | 43 of 45 | 0.960 |
| geometric-p=0.05 | 36 of 42 | 40 of 42 | 0.961 |
| geometric-p=0.3 | 39 of 45 | 43 of 45 | 0.960 |
| lognormal | 23 of 28 | 28 of 28 | 0.951 |
| lognormal-mu=11-sigma=0.7 | 21 of 24 | 24 of 24 | 0.951 |
| lognormal-mu=5.3-sigma=0.5 | 21 of 24 | 24 of 24 | 0.951 |
| negative_binomial | 36 of 42 | 40 of 42 | 0.961 |
| negative_binomial-k=2-p=0.2 | 38 of 44 | 42 of 44 | 0.962 |
| negative_binomial-k=5-p=0.05 | 30 of 36 | 35 of 36 | 0.958 |
| normal | 17 of 20 | 20 of 20 | 0.957 |
| normal-mu=170-sigma=10 | 17 of 20 | 20 of 20 | 0.957 |
| normal-mu=8000-sigma=3000 | 17 of 20 | 20 of 20 | 0.957 |
| pareto | 23 of 28 | 28 of 28 | 0.951 |
| pareto-alpha=1.16-lambda=10000 | 33 of 39 | 38 of 39 | 0.958 |
| pareto-alpha=1.5-lambda=1000 | 30 of 36 | 35 of 36 | 0.958 |
| poisson | 79 of 87 | 83 of 87 | 0.986 |
| poisson-lambda=4 | 38 of 44 | 42 of 44 | 0.962 |
| poisson-lambda=50 | 33 of 39 | 38 of 39 | 0.958 |
| t | 17 of 20 | 20 of 20 | 0.957 |
| t-df=10 | 17 of 20 | 20 of 20 | 0.957 |
| t-df=3 | 17 of 20 | 20 of 20 | 0.957 |
| uniform | 17 of 20 | 20 of 20 | 0.957 |
| uniform-a=0-b=1000000000 | 17 of 20 | 20 of 20 | 0.957 |
| uniform-a=0-b=86400 | 17 of 20 | 20 of 20 | 0.957 |
| real SQL | 179 of 199 | 191 of 199 | 0.982 |

## Saturation

| Budget | m ln m | Smallest n with a saturated seed |
|---|---|---|
| 1 KiB | 73,817 | 62,643 |
| 4 KiB | 340,696 | 295,998 |
| 8 KiB | 726,817 | 637,423 |
| 16 KiB | 1,544,487 | 1,365,698 |
