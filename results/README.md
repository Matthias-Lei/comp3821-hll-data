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

To unpack the raw results:

```bash
tar -xzf raw/all-results.tar.gz
```

## Headline numbers

Share of rows where the measured RMSE matched the theory (n ≥ 100, where the theory applies):

| Sketch | Confirmed |
|---|---|
| Bloom filter | 96% |
| K-Minimum Values | 97% |
| Linear Counting | 88% |
| HyperLogLog | 84% |
| HyperLogLog++ (dense mode only) | 75% |

Merging two half-sketches gave the same estimate as one sketch built over the whole stream:

- Linear Counting: 231,680 of 231,680 trials;
- HyperLogLog: 231,680 of 231,680 trials;
- HyperLogLog++: 231,405 of 231,680 trials. The 275 mismatches are all at n ≈ 0.3 × registers,
  where HLL++ switches from sparse to dense.
