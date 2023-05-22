# INSTANT
MTP




## Overview

In this work, we propose a novel framework, called **Instant**, which first probes the underlying relational schema-linking structures between a NL query and its database schema from a pre-trained language model, and then effectively injects it into the downstream text-to-SQL parsing models.


## Codebase

### Prepare Environment

The setup of the environment is exactly the same as that of [LGESQL](https://github.com/rhythmcao/text2sql-lgesql):

The environment-related commands are provided in `setup.sh`.

```bash
sh setup.sh
```

### Download dataset.

Download, unzip and rename the [spider.zip](https://drive.google.com/uc?export=download&id=1_AckYkinAnhqmRQtGsQgUKAnTHxxX5J0) into the directory `data`. Merge the `data/train_spider.json` and `data/train_others.json` into one single dataset `data/train.json`.

### Preprocess dataset.

Preprocess the train and dev dataset, including input normalization, schema linking, graph construction and output actions generation.

```bash
./run/run_preprocessing.sh
```

### Training

Training  Proton with:

```
./run/run_lgesql_plm.sh msde electra-large-discriminator
```

### Evaluation

For evaluation, see `run/run_evaluation.sh` and `run/run_submission.sh` (eval from scratch) for reference.


## Acknowledgements

This implementation is based on [RAT-SQL: Relation-Aware Schema Encoding and Linking for Text-to-SQL Parsers.](https://github.com/microsoft/rat-sql) and [LGESQL: Line Graph Enhanced Text-to-SQL Model with Mixed Local and Non-Local Relations](https://github.com/rhythmcao/text2sql-lgesql). Thanks to the author for releasing the code.
