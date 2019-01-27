# Grapha QA

[![Build Status](https://travis-ci.org/yuzhiliu/graphqa.svg?branch=week2)](https://travis-ci.org/yuzhiliu/graphqa)

A question answering (QA) system built ove knowledge graphs (KG).

This is based on [english2cypher](https://github.com/Octavian-ai/english2cypher) [David Mack](https://medium.com/@DavidMack) built.

# Installation:

Run
```bash
make install
```

# Build the dataset to be used by training

Run
```bash
python -m graphqa.build_data
```
This will download the data from
[GoogleCloud](https://storage.googleapis.com/octavian-static/download/english2cypher/gqa.zip),
tokenlize the data, and partition them into three different files for training,
evaluation, and prediction. The files will be saved under data/ diretory as
"data/gqa.yaml" by default.

# Training the model

Run
```bash
python -m graphqa.train
```
This will take a while to complete.

Alternatively, one can try
```bash
python -m graphqa.train --quick
```
This will use smaller batch size, one layer, et al. and existing test input
files to train the model. The result will not be good at all though. It might
be helpful to use this to debug the code.

# Running the model to make predictions

You will need to have a graph database installed to make predictions. The
simplest way is to run a Docker image created by [Andrew
Jefferson](https://neo4j.com/staff/andrew-jefferson/) and then create a
database by 

```bash
bash start-neo4j-database.sh
```

One can then run the following script to make predictions
```bash
python -m graphqa.predict
```
