# Crime Knowledge Graph Experiments

This project investigates relational inductive bias of message passing - whether relational message passing improves prediction on an event-centric crime knowledge graph and how sensitive the performance is to the choice of graph relations. The main task is to predict the coarse victim-offender relationship category, which shows if there is a connection between the offender and the victim (for example, parent, boyfriend/girlfriend, and others). The knowledge graph used is the one created in another project - [NIBRS Knowledge Graph Project](https://github.com/whid0t/nibrs-knowledge-graph).

The two main research questions explored are:

- **RQ1:** Does an R-GCN model improve over non-graph baselines for predicting victim-offender relationship categories?
- **RQ2:** Which relation types contribute useful signal, and can removing relations improve performance?

The implementation includes both non-graph baselines (majority, logistic regression baseline)
and graph-based models (R-GCN). Ablations are made where specific relationship types are
omitted.

Overall, the results support the first research question: relational message passing improves over
both the majority baseline and the tabular logistic regression baseline for our crime dataset.
However, the improvement is only moderate - the best R-GCN reaches 0.400 macro-F1, so the
task remains difficult, especially for minority classes such as ”victim was offender”.
The results also show that performance is sensitive to graph relation selection. In the results,
we have shown that the full KG is not the best graph for message passing. A smaller graph
focused on core victim, offender, incident, and victim-type structure performs better and is
more stable across seeds.

## Project report

This project was completed for the Graph Representation Learning course in the Master’s programme in Data Science at Technische Universität Wien, 2026. The complete project methodology, experiments, results, and discussion are available in the [project report](report.pdf).

## Files

- `crime_kg_experiments.ipynb`: main notebook with KG parsing, diagnostics, baselines, R-GCN experiments, and relation ablations.
- `crime_kg_ultra.ipynb`: ULTRA link prediction experiment using TSV splits exported from the main notebook.
- `kg_raw.ttl`: input knowledge graph.
- `crime_kg_outputs/`: exported splits and resulting CSV files with the metrics.

## Running Order

1. Run `crime_kg_experiments.ipynb`.
2. Run `crime_kg_ultra.ipynb`.

The first notebook exports the TSV files required by the ULTRA notebook.

## Data Path

Do not change the location of the knowledge graph. By default, the notebooks expect the knowledge graph at ```miniproject/kg_raw.ttl```.