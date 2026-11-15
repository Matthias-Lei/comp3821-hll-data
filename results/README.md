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

HyperLogLog and HyperLogLog++ were rerun on all 905 streams with master's code after it changed
on 15 Nov (f30b84a: byte registers, the paper's bias table). The other three sketches' results
are from the first run; their code did not change. HyperLogLog's estimates are the same as before.

Master's HyperLogLog++ is very slow on long streams with many repeats: in sparse mode almost every
value triggers a full compaction of the sparse list. One 5,000-value stream took over 1 h 47 min
instead of about 4 min. The rerun therefore used master's code plus `hllpp-speed-fix.patch`:

- the patch caches the compressed list's lookup table and drops entries the list already holds;
- estimates and merge results are identical to master's (checked entry by entry on finished streams);
- the only value that changes is HLL++'s `bits_used` in sparse mode, which is a little lower
  (e.g. 11,680 instead of 13,728 bits) because duplicates no longer sit in the buffer;
- the timings are for the patched code.

Where each stream's HyperLogLog-family results come from:

- 253 streams finished on unpatched master before the patch, and their results are kept. The 88
  distribution generator (nsample) streams among them were rerun with the patch, so every timing
  in the speed figures comes from patched code.
- 83 streams ran on a first version of the patch that only cached the lookup table, so their
  `bits_used` matches master's.
- The rest ran on `hllpp-speed-fix.patch` as committed here.

## Files

| Path | What it is |
|---|---|
| `raw/all-results.tar.gz` | The raw Google Benchmark JSON, one file per stream (905 files, 1.2 GB unpacked). |
| `analysis/summary.csv` | `results_analyser.py` output: one row per stream, sketch and budget (28,960 rows). Each row has the bias and RMSE with 95% CIs, the theory's prediction, whether the theory was confirmed, the timing and the merge results. |
| `analysis/summary.md` | The same table as Markdown. |
| `linear-counting/` | The Linear Counting figures (PDF and PNG) and `lc_key_numbers.md`, made by `plot_linear_counting.py` from `analysis/summary.csv`. |
| `figures/bloom/`, `figures/kmv/`, `figures/hll/`, `figures/hllpp/` | The same figures for the Bloom filter, K-Minimum Values, HyperLogLog and HyperLogLog++ (RMSE against theory, bias, by distribution, saturation for the Bloom filter) and each sketch's key numbers, made by `plot_sketches.py`. |
| `figures/comparison/` | The sketches against each other, made by `plot_comparison.py`: relative RMSE and bias against n, accuracy at equal memory, absolute RMSE against n at 16 KiB on one axis (`rmse_vs_n_16kib`), how often the theory is confirmed, measured / predicted RMSE, merge exactness, time per value, and `comparison_key_numbers.md`. Where HyperLogLog++ equals HyperLogLog exactly (n ≥ 5 × registers) it is drawn just to the right of it; hollow markers on the top edge are labelled saturated. `equal_memory_skewed_ids` is the single skewed_ids stream (n = 20,000), made by `plot_results.py`. |
| `hllpp-speed-fix.patch` | The HyperLogLog++ speed patch the rerun used (see above). |

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
| HyperLogLog++ (dense mode only) | 75% | 78% |

Merging two half-sketches gave the same estimate as one sketch built over the whole stream:

- Linear Counting: 231,680 of 231,680 trials;
- HyperLogLog: 231,680 of 231,680 trials;
- HyperLogLog++: 231,676 of 231,680 trials. The 4 mismatches are at 1 KiB with n ≈ 0.27 ×
  registers, where HLL++ switches from sparse to dense. The first run's code had 275.

Median time per value on streams of 1,000,000+ values: HyperLogLog 10.2–10.5 ns, HyperLogLog++
17.6–26.9 ns (rising with the budget, because it stays sparse longer), Linear Counting 6.5 ns.
