# Sketch comparison: key numbers

Relative RMSE is on the observations streams (one per n). Theory confirmed counts every stream and budget group with n >= 100 where the theory is judged.

## Bits of sketch state actually used

| Sketch | 1 KiB | 4 KiB | 8 KiB | 16 KiB |
|---|---|---|---|---|
| Linear Counting | 8,192 | 32,768 | 65,536 | 131,072 |
| Bloom filter | 8,192 | 32,768 | 65,536 | 131,072 |
| K-Minimum Values | 8,192 | 32,768 | 65,536 | 131,072 |
| HyperLogLog | 6,144 | 24,576 | 49,152 | 98,304 |
| HyperLogLog++ | 0 to 6,752 | 0 to 25,552 | 0 to 49,152 | 0 to 107,664 |

## Relative RMSE at n = 1,000

| Sketch | 1 KiB | 4 KiB | 8 KiB | 16 KiB |
|---|---|---|---|---|
| Linear Counting | 0.90% | 0.36% | 0.26% | 0.18% |
| Bloom filter | 0.78% | 0.37% | 0.29% | 0.21% |
| K-Minimum Values | 7.83% | 3.79% | 0 (exact) | 0 (exact) |
| HyperLogLog | 2.54% | 1.23% | 0.83% | 0.61% |
| HyperLogLog++ | 2.50% | 0.01% | 0.01% | 0.01% |

## Relative RMSE at n = 10,000

| Sketch | 1 KiB | 4 KiB | 8 KiB | 16 KiB |
|---|---|---|---|---|
| Linear Counting | 1.00% | 0.41% | 0.24% | 0.17% |
| Bloom filter | 1.81% | 0.42% | 0.27% | 0.17% |
| K-Minimum Values | 8.78% | 4.11% | 3.07% | 1.87% |
| HyperLogLog | 2.95% | 2.76% | 0.86% | 0.55% |
| HyperLogLog++ | 2.95% | 1.29% | 0.86% | 0.55% |

## Relative RMSE at n = 100,000

| Sketch | 1 KiB | 4 KiB | 8 KiB | 16 KiB |
|---|---|---|---|---|
| Linear Counting | saturated | 0.73% | 0.39% | 0.21% |
| Bloom filter | saturated | saturated | 0.81% | 0.34% |
| K-Minimum Values | 8.74% | 5.43% | 3.19% | 2.12% |
| HyperLogLog | 3.11% | 1.45% | 0.99% | 0.69% |
| HyperLogLog++ | 3.11% | 1.45% | 0.99% | 0.69% |

## Relative RMSE at n = 1,000,000

| Sketch | 1 KiB | 4 KiB | 8 KiB | 16 KiB |
|---|---|---|---|---|
| Linear Counting | saturated | saturated | saturated | 1.44% |
| Bloom filter | saturated | saturated | saturated | saturated |
| K-Minimum Values | 8.07% | 4.33% | 2.81% | 1.95% |
| HyperLogLog | 2.55% | 1.48% | 1.02% | 0.62% |
| HyperLogLog++ | 2.55% | 1.48% | 1.02% | 0.62% |

## Predicted RMSE inside the measured 95% interval

| Sketch | 1 KiB | 4 KiB | 8 KiB | 16 KiB | All budgets |
|---|---|---|---|---|---|
| Linear Counting | 436 of 498 (88%) | 483 of 539 (90%) | 459 of 558 (82%) | 529 of 572 (92%) | 1907 of 2167 (88%) |
| Bloom filter | 428 of 440 (97%) | 491 of 509 (96%) | 523 of 538 (97%) | 514 of 547 (94%) | 1956 of 2034 (96%) |
| K-Minimum Values | 559 of 579 (97%) | 543 of 579 (94%) | 567 of 579 (98%) | 569 of 579 (98%) | 2238 of 2316 (97%) |
| HyperLogLog | 485 of 534 (91%) | 487 of 520 (94%) | 434 of 527 (82%) | 365 of 535 (68%) | 1771 of 2116 (84%) |
| HyperLogLog++ | 176 of 216 (81%) | 115 of 139 (83%) | 62 of 109 (57%) | 48 of 72 (67%) | 401 of 536 (75%) |

The same, counting each observations stream's n once (its copies for other distributions of repeats hold the same values and repeat one result):

| Sketch | 1 KiB | 4 KiB | 8 KiB | 16 KiB | All budgets |
|---|---|---|---|---|---|
| Linear Counting | 195 of 216 (90%) | 216 of 231 (94%) | 217 of 241 (90%) | 225 of 250 (90%) | 853 of 938 (91%) |
| Bloom filter | 162 of 174 (93%) | 209 of 227 (92%) | 215 of 230 (93%) | 224 of 239 (94%) | 810 of 870 (93%) |
| K-Minimum Values | 237 of 257 (92%) | 235 of 257 (91%) | 245 of 257 (95%) | 247 of 257 (96%) | 964 of 1028 (94%) |
| HyperLogLog | 204 of 239 (85%) | 208 of 232 (90%) | 199 of 221 (90%) | 201 of 229 (88%) | 812 of 921 (88%) |
| HyperLogLog++ | 100 of 126 (79%) | 68 of 83 (82%) | 36 of 53 (68%) | 27 of 32 (84%) | 231 of 294 (79%) |

## Smallest n with a saturated seed

| Sketch | 1 KiB | 4 KiB | 8 KiB | 16 KiB |
|---|---|---|---|---|
| Linear Counting | 62,643 | 295,998 | 637,423 | 1,365,698 |
| Bloom filter | 21,779 | 100,000 | 212,140 | 468,554 |
| K-Minimum Values | none | none | none | none |
| HyperLogLog | none | none | none | none |
| HyperLogLog++ | none | none | none | none |

## Merge: seeds where the merged sketch gives the same estimate as the direct one

| Sketch | Trials |
|---|---|
| Linear Counting | 231,680 of 231,680 |
| Bloom filter | not benchmarked |
| K-Minimum Values | not benchmarked |
| HyperLogLog | 231,680 of 231,680 |
| HyperLogLog++ | 231,405 of 231,680 |

## Median nanoseconds per value (streams of 1,000,000+ values)

| Sketch | 1 KiB | 4 KiB | 8 KiB | 16 KiB |
|---|---|---|---|---|
| Linear Counting | 6.5 | 6.6 | 6.6 | 6.5 |
| Bloom filter | 14.3 | 14.2 | 14.3 | 14.4 |
| K-Minimum Values | 21.8 | 27.9 | 23.0 | 22.9 |
| HyperLogLog | 5.5 | 5.6 | 5.7 | 5.7 |
| HyperLogLog++ | 19.7 | 17.9 | 19.0 | 18.2 |
