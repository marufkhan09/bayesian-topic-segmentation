# Bayesian Topic Segmentation (BayesSeg)

A copy of the BayesSeg reference implementation by Jacob Eisenstein and Regina Barzilay (MIT, 2008), kept in `experiments/bayesseg/`. The code, data and baselines are the authors' release and are not original work. They are used under the GNU General Public License, version 2 or later.

> Jacob Eisenstein and Regina Barzilay. *Bayesian Unsupervised Topic Segmentation.* Proceedings of EMNLP 2008.

## What it does

BayesSeg splits a text into topically coherent segments without any labelled training data, using a Bayesian model of lexical cohesion. Segmenters are scored with Pk and WindowDiff.

The configuration files in `experiments/bayesseg/config/` run:

| Config | Segmenter |
|---|---|
| `dp.config` | Bayesian lexical cohesion, solved with dynamic programming |
| `cue.config` | Cue-phrase MCMC version, initialised from the dynamic programming result |
| `mcsopt.ai.config` | MinCutSeg (Malioutov and Barzilay, 2006) |
| `ui.config` | TextSeg 1.211 (Utiyama and Isahara) |
| `lcseg.config` | LCSeg (not included; it must be obtained from Columbia University) |
| `perfect.config` | A "perfect" segmenter that reproduces the ground truth, for debugging |

## Contents

- `experiments/bayesseg/source/`: Java source
- `experiments/bayesseg/classes/`: compiled classes
- `experiments/bayesseg/data/`: the medical textbook dataset (`books/clinical`) and ICSI meeting data (`icsi`)
- `experiments/bayesseg/baselines/`: TextSeg 1.211, included under its own licence (see `COPYING` in that folder)
- `experiments/bayesseg/README`: the authors' original documentation

## Run it

Requires Java 6 or later. Run these from `experiments/bayesseg/`:

```bash
# Evaluate a segmenter on textbook files 001, 101 and 201
./eval config/dp.config

# Segment one document read from stdin
cat data/books/clinical/050.ref | ./segment config/dp.config

# Rebuild from source with Apache Ant
ant build
```

## Licence and credit

Copyright 2008 Massachusetts Institute of Technology, released under GPL v2 or later. Credit for the method and code belongs to the original authors. See the original README for the full notice.
