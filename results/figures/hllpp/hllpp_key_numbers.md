# HyperLogLog++: key numbers

- **Merge:** the merged sketch gives the same estimate as one built over the whole stream in **231,676 of 231,680** trials.

## Predictions inside the measured 95% interval (n >= 100, where the theory is judged)

| Streams, budget | RMSE | Bias |
|---|---|---|
| synthetic, team observations generator, 1 KiB | 102 of 125 | 125 of 125 |
| synthetic, team observations generator, 4 KiB | 76 of 89 | 89 of 89 |
| synthetic, team observations generator, 8 KiB | 46 of 89 | 88 of 89 |
| synthetic, team observations generator, 16 KiB | 43 of 68 | 63 of 68 |
| real SQL query results, 1 KiB | 19 of 21 | 20 of 21 |
| real SQL query results, 4 KiB | 11 of 14 | 14 of 14 |
| real SQL query results, 8 KiB | 7 of 9 | 9 of 9 |
| real SQL query results, 16 KiB | 4 of 4 | 4 of 4 |
| synthetic, team distribution generator, 1 KiB | 55 of 70 | 69 of 70 |
| synthetic, team distribution generator, 4 KiB | 28 of 36 | 36 of 36 |
| synthetic, team distribution generator, 8 KiB | 9 of 11 | 11 of 11 |
| synthetic, team distribution generator, 16 KiB | 0 of 0 | 0 of 0 |

## By distribution of repeats (all budgets)

| Distribution | RMSE | Bias | Median measured / predicted RMSE |
|---|---|---|---|
| bernoulli | 14 of 21 | 21 of 21 | 0.908 |
| bernoulli-p=0.02 | 14 of 21 | 21 of 21 | 0.908 |
| bernoulli-p=0.3 | 14 of 21 | 21 of 21 | 0.908 |
| binomial | 12 of 17 | 17 of 17 | 0.955 |
| binomial-n=30-p=0.2 | 12 of 17 | 17 of 17 | 0.955 |
| binomial-n=365-p=0.05 | 10 of 13 | 13 of 13 | 0.957 |
| geometric | 14 of 21 | 21 of 21 | 0.908 |
| geometric-p=0.05 | 10 of 13 | 13 of 13 | 0.957 |
| geometric-p=0.3 | 14 of 21 | 21 of 21 | 0.908 |
| lognormal | 1 of 1 | 1 of 1 | 0.908 |
| negative_binomial | 10 of 13 | 13 of 13 | 0.957 |
| negative_binomial-k=2-p=0.2 | 12 of 17 | 17 of 17 | 0.955 |
| negative_binomial-k=5-p=0.05 | 4 of 5 | 5 of 5 | 0.908 |
| pareto | 1 of 1 | 1 of 1 | 0.908 |
| pareto-alpha=1.16-lambda=10000 | 6 of 9 | 9 of 9 | 0.902 |
| pareto-alpha=1.5-lambda=1000 | 4 of 5 | 5 of 5 | 0.908 |
| poisson | 97 of 129 | 123 of 129 | 0.920 |
| poisson-lambda=4 | 12 of 17 | 17 of 17 | 0.955 |
| poisson-lambda=50 | 6 of 9 | 9 of 9 | 0.902 |
| real SQL | 41 of 48 | 47 of 48 | 0.967 |
