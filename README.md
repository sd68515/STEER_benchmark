# STEER benchmark source fork

This fork supports [VelocityBenchmarking](https://github.com/vikkihuangkexin/VelocityBenchmarking) and is based on [lzygenomics/STEER](https://github.com/lzygenomics/STEER) commit `b2480ee810982dbd16bb1dd68ceb29e9fca4b10f`. Please cite the original STEER work when using the method.

## Compatibility changes

| File and location | Change | Reason |
| --- | --- | --- |
| `steer/utils/utils.py`, `GeneExpressionDataset_adata_velo` | Converts original spliced and unspliced layers with `.toarray()` only when sparse; accepts dense arrays through `np.asarray()`. | Upstream called `.toarray()` unconditionally, which fails for dense input. |

The conversion preserves input values. STEER's architecture, losses, training stages, and velocity equations are unchanged.

## Environment

Reference versions: Python 3.10.12 and PyTorch 2.4.0+cu124. The retained upstream `requirements.txt` is dependency metadata, not a complete environment lock.

## Installation

Install the retained `steer/` package in an environment with compatible PyTorch, PyG, and R dependencies:

```bash
python -m pip install --no-deps -e .
```

The separate benchmark runner supplies spatial preprocessing, parameters, device selection, and input data. Tutorials, checkpoints, and results are not included.

## License and provenance

The upstream snapshot has no standalone `LICENSE`; its `setup.py` declares MIT. This fork adds no new license text; consult the upstream authors for licensing terms.
