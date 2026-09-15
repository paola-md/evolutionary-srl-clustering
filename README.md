# Evolutionary clustering of apprentices' self-regulated learning behaviour

Code for tracking how apprentices' behaviour in online learning journals moves between profiles over a semester: SQL feature pipeline, temporal smoothing, spectral clustering per feature group, and k-modes over the labels.

**Evolutionary Clustering of Apprentices' Self-Regulated Learning Behavior in Learning Journals**  
Paola Mejia-Domenzain, Mirko Marras, Christian Giang, Alberto Cattáneo, Tanja Käser. *IEEE Transactions on Learning Technologies*, 2022.  
[DOI](https://doi.org/10.1109/tlt.2022.3195881) · [Abstract and BibTeX](https://paola-md.github.io/papers/evolutionary-clustering-of-apprentices-self-regulated-learning-behavior-.html)

This is a fork of [epfl-ml4ed/evolutionary-srl-clustering](https://github.com/epfl-ml4ed/evolutionary-srl-clustering), kept under my account with a standardised README and a clean-up pass (unused imports, stray OS files, personal paths). The code is otherwise as published; open issues upstream.

## What is here

```
sql/
  01-semantic/ 02-features/ 03-cohort/ 04-results/   the feature pipeline, run in order
  functions.sql  reset_schemas.sql
src/
  project_settings.py   feature groups (incl. the Geneva cohort) and ids
  etl/                  Postgres helpers and time-series generation
  features/             regularity, effort and related measures
  models/               evolutionary (temporally smoothed) spectral clustering, profiles
docs/
  paper.pdf             the paper
  formal_notation.pdf   the feature formulas
docker/                 Dockerfile and requirements for the analysis environment
data/                   empty
```

## How to run

The pipeline reads from a Postgres database described by `src/project_settings.py` and the SQL in `sql/`. Build the environment from `docker/` (or install `docker/requirements.txt`), load the journal data, run the SQL folders in numeric order, then the scripts under `src/models/`.

Database credentials are read from a config file, never from the code.

## Data

The learning-journal data (183 apprentices, over 121,000 entries) belongs to the vocational schools and is not included.

## Cite

```bibtex
@article{mejiadomenzain2022evolutiona,
  title      = {{Evolutionary Clustering of Apprentices' Self-Regulated Learning Behavior in Learning Journals}},
  author     = {Paola Mejia-Domenzain and Mirko Marras and Christian Giang and Alberto Cattáneo and Tanja Käser},
  year       = {2022},
  journal    = {IEEE Transactions on Learning Technologies},
  publisher  = {Institute of Electrical and Electronics Engineers},
  doi        = {10.1109/tlt.2022.3195881},
  url        = {https://paola-md.github.io/papers/evolutionary-clustering-of-apprentices-self-regulated-learning-behavior-.html}
}
```


## Licence and status

GNU GPL v3, as stated in the original README (the repository carries no LICENSE file).

Not maintained: kept as the record of the paper.
