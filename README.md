# Crime Knowledge Graph Experiments

This project studies relational inductive bias of message passing - whether relational message passing improves prediction on an event-centric crime knowledge graph and how sensitive the performance is to the choice of graph relations. The main task is to predict the victim-offender relationship categories from an event-centric KG.

## Files

- `crime_kg_experiments.ipynb`: main notebook with KG parsing, diagnostics, baselines, R-GCN experiments, and relation ablations.
- `crime_kg_ultra.ipynb`: ULTRA link prediction experiment using TSV splits exported from the main notebook.
- `kg_raw.ttl`: input knowledge graph.
- `crime_kg_outputs/`: exported splits and result CSV files.

## Running Order

1. Run `crime_kg_experiments.ipynb`.
2. Run `crime_kg_ultra.ipynb`.

The first notebook exports the TSV files required by the ULTRA notebook.

## Data Path

Do not change the location of the knowledge graph. It should be at:

```python
KG_PATH = Path("kg_raw.ttl")