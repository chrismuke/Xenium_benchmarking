# Repository Guidelines

## Project Structure & Module Organization
- `xb/`: Core Python package (formatting, preprocessing, domain identification, plotting, simulation).
- `notebooks/`: Reproducible analysis notebooks grouped by task; main pipelines: `end-to-end_pipeline_optimized*.ipynb`.
- `data/` and `figures/`: Input datasets and generated outputs (large files kept out of Git).
- `Banksy_py/`: BANKSY submodule/environment for domain identification.
- `xenium_benchmarking.yml`: Conda environment for the main workflow.

## Build, Test, and Development Commands
- Create env: `conda env create --name xb --file=xenium_benchmarking.yml`
- Activate: `conda activate xb`
- Install package: `pip install -e .` (provides `xb` in editable mode)
- Quick import check: `python -c "import xb; from xb import formatting, preprocessing"`
- Run notebooks: `jupyter lab` (rerun relevant sections to validate changes)
- Baysor helper: `bash xb/run_baysor.sh` (requires Docker image configured externally)

## Coding Style & Naming Conventions
- Python 3.8; follow PEP 8, 4‑space indentation, 88–100 col width.
- Naming: modules `snake_case.py`, functions/variables `snake_case`, classes `PascalCase`.
- Docstrings: NumPy or Google style; include parameter types and expected AnnData schema where relevant.
- Imports: standard lib, third‑party, local (in that order). Avoid wildcard imports.

## Testing Guidelines
- No formal test suite yet. Prefer lightweight smoke tests (import modules; run a small `format_to_adata` on the example dataset) and rerun targeted notebook cells.
- If adding tests, use `pytest` under `tests/`, files named `test_*.py`; focus on deterministic utilities in `xb/`.

## Commit & Pull Request Guidelines
- Commits: short imperative subject (<=72 chars), include scope when helpful (e.g., `xb/formatting:`). Squash noisy WIP commits.
- PRs: clear description of changes, rationale, and impact; reference datasets/notebooks touched; add screenshots for figure changes; include minimal reproduction (commands/paths) and environment notes (`xb` or `banksy`).
- Do not commit large data or secrets. Keep paths under `data/` configurable and ignored by Git.

## Security & Configuration Tips
- Large `.h5ad` and raw outputs belong in `data/` (download from Zenodo links). Never commit credentials or private endpoints. Document Docker/BANKSY versions when relevant.
