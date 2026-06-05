# Physics-Consistent Heat Surrogate Benchmark

This repository contains the implementation and reproducibility artifacts for the paper:

**Physics-Consistent Benchmarking of Surrogate Models for Two-Dimensional Heat Conduction: Accuracy, Residual Reliability, and Efficiency Across Regular and Irregular Domains**

## Overview

This benchmark evaluates surrogate models for two-dimensional steady-state heat-conduction field prediction. The study compares three model families under a unified experimental protocol:

- Convolutional Neural Networks (CNNs)
- Graph Neural Networks (GNNs)
- Enhanced Quantum-Inspired Extreme Learning Machine (eQELM)

The benchmark focuses on the joint evaluation of predictive accuracy, physics consistency, statistical robustness, computational efficiency, and reproducibility.

## Main Contributions

- Reproducible multi-dataset benchmark for 2D heat-conduction surrogate modeling.
- Comparison of CNN, GNN, and eQELM models under the same data splits and evaluation protocol.
- Physics-consistency evaluation using residual error, boundary flux consistency, regional thermal error, and Fourier spectral error.
- Repeated-seed statistical analysis with mean, standard deviation, confidence intervals, and paired tests.
- Reviewer-oriented reproducibility package including raw results, figures, configuration files, environment records, and dataset manifests.

## Repository Structure

```text
physics-consistent-heat-surrogate-benchmark/
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
├── notebooks/
│   └── ieee-access-heat-benchmark.ipynb
├── results/
│   ├── results_ieee_access.csv
│   ├── summary_mean_std.csv
│   ├── results_lambda_ablation.csv
│   ├── ablation_lambda_summary.csv
│   ├── paired_tests_rmse.csv
│   ├── paired_tests_mae.csv
│   ├── paired_tests_physics_error.csv
│   ├── paired_tests_latency_ms.csv
│   ├── dataset_manifest.csv
│   └── scaling_audit.csv
├── figures/
│   ├── dataset_sample_D6.png
│   ├── dataset_sample_D8var.png
│   ├── dataset_sample_D8irregular.png
│   ├── rmse_mean_std.png
│   ├── physics_error_mean_std.png
│   ├── latency_ms_mean_std.png
│   ├── lambda_ablation_pareto.png
│   ├── pareto_precision_physics.png
│   ├── sample_prediction_D6_CNN.png
│   └── sample_prediction_D8var_CNN.png
├── reviewer_artifacts/
│   ├── run_config.json
│   ├── run_card.json
│   ├── environment.json
│   ├── pip_freeze.txt
│   ├── nvidia_smi.txt
│   └── README_REPRODUCIBILITY.md
└── manuscript/
    └── paper.pdf
```

## Datasets

The benchmark includes three thermal settings:

| Dataset | Description | Purpose |
|---|---|---|
| D6 | Regular-grid zero-boundary dataset | Reference heat-source-to-temperature mapping |
| D8-var | Regular-grid boundary-condition-variant dataset | Boundary-condition robustness |
| D8-irregular | Irregular-coordinate stress dataset | Coordinate-aware and mesh-related behavior |

All datasets are generated through a deterministic pipeline. Dataset manifests and SHA-256 checksums are included to support reproducibility.

## Evaluation Metrics

The benchmark reports four groups of metrics:

1. **Predictive accuracy**: RMSE, MAE, and R².
2. **Physics consistency**: residual error, boundary flux error, regional thermal error, and Fourier spectral error.
3. **Computational efficiency**: inference latency, model size, and deployment-oriented cost indicators.
4. **Statistical reliability**: repeated random seeds, confidence intervals, and paired Wilcoxon signed-rank tests.

## Main Findings

The final benchmark results show that:

- CNN achieves the lowest predictive error across the evaluated datasets.
- eQELM provides the fastest inference and the lowest residual-based physics error on regular-grid datasets.
- The evaluated GNN does not outperform CNN or eQELM in the current configuration, suggesting that more specialized mesh-aware graph design is required.
- The lowest RMSE and the lowest physics residual occur at different physics-regularization strengths, confirming the need for accuracy--physics Pareto analysis.

## Running the Notebook

The main notebook is located in:

```text
notebooks/ieee-access-heat-benchmark.ipynb
```

It is designed to run in a Kaggle GPU environment, preferably with an NVIDIA T4 GPU.

To install the main Python dependencies locally:

```bash
pip install -r requirements.txt
```

Then open the notebook with Jupyter:

```bash
jupyter notebook notebooks/ieee-access-heat-benchmark.ipynb
```

For exact reproducibility, see:

```text
reviewer_artifacts/README_REPRODUCIBILITY.md
reviewer_artifacts/run_config.json
reviewer_artifacts/environment.json
reviewer_artifacts/pip_freeze.txt
```

## Reproducibility

The benchmark pipeline stores dataset generation parameters, train/validation/test split information, train-only normalization statistics, random seed records, raw per-seed results, aggregated result tables, statistical-test outputs, generated figures, and environment records.

These artifacts are intended to make the benchmark auditable, reproducible, and extensible.

## Citation

If you use this benchmark, please cite the associated paper once published.

```bibtex
@article{nkishi2026physicsconsistentheatbenchmark,
  title   = {Physics-Consistent Benchmarking of Surrogate Models for Two-Dimensional Heat Conduction: Accuracy, Residual Reliability, and Efficiency Across Regular and Irregular Domains},
  author  = {Nkishi Djenga, Gedeon and Kambale, Witesyavwirwa Vianney and Kambale, Exauce Maruba and Muhire, Jean-Pierre Mugisha and Kyamakya, Kyandoghere},
  journal = {IEEE Access},
  year    = {2026},
  note    = {Submitted}
}
```

## License

This repository is released under the MIT License. See [LICENSE](LICENSE) for details.

## Contact

**Gédéon Nkishi Djenga**  
University of Kinshasa (UNIKIN)  
Email: gedeon.nkishi@unikin.ac.cd
