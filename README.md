[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)]() [![numpy](https://img.shields.io/badge/numpy-1.24+-blue.svg)]() [![scipy](https://img.shields.io/badge/scipy-1.11+-blue.svg)]() [![soundfile](https://img.shields.io/badge/soundfile-0.12+-blue.svg)]() [![matplotlib](https://img.shields.io/badge/matplotlib-3.7+-blue.svg)]() [![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

# HOA Seven-Year Corpus - IEEE Access Analysis Pipeline

Supplementary materials for the paper:

***"A Seven-Year Higher-Order Ambisonics Recording Corpus: Dataset, Methodology, and a Co-Located Spherical Microphone Array Comparison"***
Bartłomiej Mróz, Szymon Zaporowski · *IEEE Access* (under review)

This repository contains:
- The corpus-wide figure and LaTeX-macro pipeline (geographic distribution, recording timeline, room acoustics, loudness distribution, session inventory)
- The microphone-comparison bootstrap uncertainty analysis added during peer review (confidence intervals on the per-order energy rolloff)
- Pre-computed results (CSV tables, LaTeX macros, publication figures) so most of the repository reproduces without downloading any audio

For methodology, interpretation, and results discussion, please refer to the manuscript. The comparison session's core signal analysis (per-order RMS, LUFS, spectral, directional metrics) was first published for the companion AES Copenhagen paper; see [hoa-mic-comparison-aes2026](https://git.pg.edu.pl/p829296/hoa-mic-comparison-aes2026) for that repository. `revision_stats.py` here reimplements the same per-order metric definition rather than depending on that repo, so this repository is self-contained.

## Repository Structure

```
.
├── pyscripts/
│   ├── analysis_utils.py             # Shared config, spectral helpers, mic definitions
│   ├── generate_all_figures.py       # Audio-driven: computes every corpus figure CSV
│   ├── render_ieee_figures.py        # CSV-driven: renders Figs 3-10 at IEEE column width
│   ├── generate_latex_variables.py   # CSV -> \newcommand macros consumed by the manuscript
│   ├── parse_render_stats.py         # REAPER render-stats HTML -> LUFS table
│   ├── analyze_aula_acoustics.py     # Room-acoustic parameters (RT60, C80, ...)
│   ├── calculate_corpus_stats.py     # Corpus size/duration/order inventory
│   ├── generate_session_inventory.py # Session inventory LaTeX table
│   ├── plot_rt60.py                  # Fig. 3 standalone
│   ├── plot_lufs_distribution.py     # Fig. 6 standalone
│   └── plot_spectral_comparison.py   # Fig. 7 standalone (needs audio)
├── plots/                            # Pre-computed figure inputs (CSV)
├── data/                             # Render statistics, aggregated LaTeX macros, session inventory
├── revision_stats.py                 # Paired moving-block bootstrap (confidence intervals)
├── revision_figures.py               # Two-piece Fig. 9, Figs 10a/10b with CI whiskers
├── revision_results/                 # Bootstrap outputs - see revision_results/README.md
│   ├── spatial_energy_two_piece.csv  #   Per-order dBFS + 95% CIs, both pieces
│   ├── rolloff_bootstrap.csv         #   Rolloff + paired between-array difference
│   ├── directional_ci.csv            #   W level, X/Y/Z-over-W with CIs
│   ├── revision_stats_variables.tex  #   LaTeX macros for the manuscript
│   ├── frame_order_energies_*.csv    #   Frame-level per-order energies
│   ├── frame_difference_3OA_*.csv    #   Annotated ZM-1 vs Spcmic difference files
│   └── cache/frames_*.npz            #   Frame-energy caches (reproduce without audio)
├── requirements.txt
├── LICENSE
└── README.md
```

## Recordings

**Recording corpus**: Higher-Order Ambisonics Recording Corpus, deposited at *Bridge of Data* (Most Danych), Gdańsk University of Technology - [doi.org/10.34808/w8bx-2094](https://doi.org/10.34808/w8bx-2094) (CC BY-NC-SA 4.0)

The recordings are not included in this repository. Download them from the DOI above and point the analysis scripts to their location.

## Reproducing the Corpus Figures

Most figures regenerate **without downloading any audio**, straight from the CSVs in `plots/`:

```sh
pip install -r requirements.txt
python3 pyscripts/render_ieee_figures.py          # all figures
python3 pyscripts/render_ieee_figures.py 09 10    # selected figure numbers
```

Two exceptions need the audio: Fig. 7 (spectral comparison) and any re-run of `generate_all_figures.py`, which recomputes the CSVs from the WAV files:

```sh
export HOA_CORPUS_DIR="/path/to/hoa-corpus"
python3 pyscripts/generate_all_figures.py
```

`HOA_CORPUS_DIR` must contain the session folders as deposited (e.g. `2024.08.15 -- ZM1 Spcmic Saramonic/render/*.wav`).

## Numeric Claims in the Manuscript

Every number cited in the paper is a LaTeX macro, not a typed literal:

```
CSV results  ->  generate_latex_variables.py  ->  data/all_variables.tex  ->  \input{} in the manuscript
```

## Uncertainty Analysis (Bootstrap Confidence Intervals)

`revision_stats.py` attaches confidence intervals to the microphone-comparison results, added during peer review to address reviewer requests for statistical treatment. Each recording of the co-located comparison session (2024-08-15) is analysed in 1-second frames; because all arrays captured the same performance simultaneously, frames are **paired across arrays by wall-clock time**, so the between-array rolloff difference is resampled as a paired statistic and the programme-level variance shared by both arrays cancels. Resampling uses a moving-block bootstrap (30-second blocks, 2000 replicates, fixed seed) to respect the temporal correlation of musical material.

```sh
python3 revision_stats.py --base-dir /path/to/hoa-corpus   # frame caches + CIs
python3 revision_figures.py                                # figures with CI whiskers
```

The frame-energy caches in `revision_results/cache/` are committed (≈1.2 MB), so both commands reproduce every statistic and figure **without downloading the ~48 GB of session audio** - `revision_stats.py` only reads WAV files whose cache is missing. Full details, the resampling rationale, and the headline numbers are in [`revision_results/README.md`](revision_results/README.md).

## License

**Code in this repository**: licensed under [Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: https://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png

## Contact

Bartłomiej Mróz · bartlomiej.mroz@pg.edu.pl · Department of Multimedia Systems, Gdańsk University of Technology · [bmroz.eu](https://bmroz.eu)
