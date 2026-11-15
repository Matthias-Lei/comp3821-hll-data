# Benchmark results: all five sketches

Linear Counting, Bloom filter, K-Minimum Values, HyperLogLog and HyperLogLog++ were each run on
905 streams. Every stream was run at 4 memory budgets (1, 4, 8 and 16 KiB = 8192, 32768, 65536
and 131072 bits) with 64 hash seeds. That is 1,853,440 trials in total, and none failed.

The streams were:

- the 200 streams in `data/streams/` (synthetic and SQL query results);
- 705 more synthetic streams made by `python/create_analysis_streams.py` on the
  `sid-linear-counting` branch of the code repo. They use the team's `DistributionGenerator`
  and `ObservationsGenerator`, two realistic parameter sets per distribution, and 64, 1024 and
  65536 bins.

HyperLogLog++ is Daniel's implementation from `daniel/hyperloglogplus`, added to the benchmark
for this run.

## Files

| Path | What it is |
|---|---|
| `raw/all-results.tar.gz` | The raw Google Benchmark JSON, one file per stream (905 files, 1.2 GB unpacked). |
| `analysis/summary.csv` | `results_analyser.py` output: one row per stream, sketch and budget (28,960 rows). Each row has the bias and RMSE with 95% CIs, the theory's prediction, whether the theory was confirmed, the timing and the merge results. |
| `analysis/summary.md` | The same table as Markdown. |
| `linear-counting/` | The Linear Counting figures (PDF and PNG) and `lc_key_numbers.md`, made by `plot_linear_counting.py` from `analysis/summary.csv`. |
| `figures/bloom/`, `figures/kmv/`, `figures/hll/`, `figures/hllpp/` | The same figures for the Bloom filter, K-Minimum Values, HyperLogLog and HyperLogLog++ (RMSE against theory, bias, by distribution, saturation for the Bloom filter) and each sketch's key numbers, made by `plot_sketches.py`. |
| `figures/comparison/` | The sketches against each other, made by `plot_comparison.py`: relative RMSE and bias against n, accuracy at equal memory, how often the theory is confirmed, measured / predicted RMSE, merge exactness, time per value, and `comparison_key_numbers.md`. |

To redraw every figure from `analysis/summary.csv` (code on the `sid-linear-counting` branch of the
code repo):

```bash
python3 python/plot_sketches.py --summary analysis/summary.csv
python3 python/plot_comparison.py --summary analysis/summary.csv
```

To unpack the raw results:

```bash
tar -xzf raw/all-results.tar.gz
```

## Headline numbers

Share of rows where the predicted RMSE lies inside the measured 95% interval (n ≥ 100, where the
theory is judged). Every observations stream with the same n holds the same values, so its copies
for the other distributions of repeats repeat one result; the second column counts each such n once.

| Sketch | Every row | Each observations n once |
|---|---|---|
| Bloom filter | 96% | 93% |
| K-Minimum Values | 97% | 94% |
| Linear Counting | 88% | 91% |
| HyperLogLog | 84% | 88% |
| HyperLogLog++ (dense mode only) | 75% | 79% |

Merging two half-sketches gave the same estimate as one sketch built over the whole stream:

- Linear Counting: 231,680 of 231,680 trials;
- HyperLogLog: 231,680 of 231,680 trials;
- HyperLogLog++: 231,405 of 231,680 trials. The 275 mismatches are all at n ≈ 0.3 × registers,
  where HLL++ switches from sparse to dense.
