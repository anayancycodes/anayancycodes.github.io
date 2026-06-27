+++
title = "My R starter kit for bioinformatics"
date = 2026-06-26
draft = false
tags = ["R", "bioinformatics", "tools", "tutorial"]
summary = "The handful of R packages I reach for first on almost every analysis — and a minimal setup you can copy."
+++

When I started, the hardest part wasn't any single function — it was knowing *which* of the thousands of R packages to even open. Here's the short list I actually use, plus a minimal setup you can paste into a fresh script.

> This is a living post. I'll update it as my setup changes.

## The core four

For everyday data work, before anything bioinformatics-specific:

- **`tidyverse`** — `dplyr`, `ggplot2`, `readr`, `tidyr`. The grammar I think in.
- **`here`** — sane file paths that don't break when you move a script.
- **`janitor`** — `clean_names()` alone has saved me hours.
- **`fs`** — file-system operations that behave the same on every OS.

```r
install.packages(c("tidyverse", "here", "janitor", "fs"))
```

## Bioconductor: the other half of the world

A lot of bioinformatics packages don't live on CRAN — they live on **Bioconductor**. You install those through its own manager:

```r
install.packages("BiocManager")
BiocManager::install(c(
  "Biostrings",      # sequence handling
  "SummarizedExperiment",  # the standard container for omics data
  "DESeq2"           # bulk RNA-seq differential expression
))
```

If you're heading toward single-cell, `Seurat` (CRAN) is the common entry point and worth a post of its own.

## A minimal project setup

I start almost every analysis the same way. Create the script, load tools, set a path anchor:

```r
# packages
library(tidyverse)
library(here)
library(janitor)

# read data from a /data folder at the project root
counts <- read_csv(here("data", "counts.csv")) |>
  clean_names()

glimpse(counts)
```

Two small habits that pay off later:

1. **Use `here()` instead of `setwd()`.** Your code keeps working when someone else (or future you) opens the project somewhere else.
2. **`clean_names()` immediately.** Column names like `Gene Symbol (raw)` become `gene_symbol_raw`, and everything downstream gets easier.

## What I'd skip at first

You don't need a perfect environment to start. `renv` for reproducibility, Docker, a full project template — all great, all *later*. Getting one real analysis working end-to-end taught me more than any amount of setup.

---

*What's in your starter kit? I'm always looking to trim or add — [email me](mailto:imusicjunki3@gmail.com).*
