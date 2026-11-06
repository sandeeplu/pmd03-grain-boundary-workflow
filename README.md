# Ex2: Solute-grain boundary segregation

## 1. Overview

This workflow investigates the segregation behaviour of different solute atoms at a Σ5 (120)[001] tilt grain boundary in aluminium (Al).

The objective is to understand how local atomic environments and excess Voronoi volumes influence solute segregation energies.

The workflow considers four solute elements: copper (Cu), silver (Ag), gold (Au), and nickel (Ni). Atomistic calculations are performed using the Effective Medium Theory (EMT) interatomic potential through ASE and pyiron-workflow.

## 2. Scientific Objective

Grain boundaries contain atomic sites with different local environments, including compressed and expanded sites. Solute atoms can preferentially occupy these sites depending on their energetic and structural compatibility with the surrounding host atoms.

This workflow calculates segregation energies and relates them to the excess Voronoi volumes of grain-boundary sites.

The segregation energy is calculated as:

E_seg = (E_GB+X + E_bulk) - (E_GB + E_bulk+X)

where X represents the solute atom. Negative segregation energies indicate energetically favourable segregation relative to the most favourable bulk solute site.

## 3. Workflow Description

The workflow consists of the following steps:

1. Generate bulk aluminium and Σ5 grain-boundary structures.
2. Relax the bulk and clean grain-boundary structures.
3. Identify symmetrically distinct atomic sites using Steinhardt bond-order parameters.
4. Substitute solute atoms at distinct bulk and grain-boundary sites.
5. Relax the solute-containing structures.
6. Calculate solute segregation energies.
7. Calculate atomic Voronoi volumes and grain-boundary excess volumes.
8. Plot segregation energies against excess Voronoi volumes.

## 4. Software and Dependencies

The workflow uses:

- Python
- Atomic Simulation Environment (ASE)
- pyiron-workflow
- pyiron-workflow-atomistics
- bagofholding
- NumPy
- Matplotlib
- pmd03

The exact package versions are specified in `pyproject.toml`.

## 5. Installation

Create the Conda environment:

```bash
conda env create -f environment.yml
```

Activate it:

```bash
conda activate pmd03-ex2
```

Install the local Python package if it has not already been installed through the environment file:

```bash
pip install -e .
```

Launch JupyterLab:

```bash
jupyter lab
```

## 6. Execution

Open `ex2-grain_boundary.ipynb` in JupyterLab.

The notebook provides two execution options:

**Option 1: Load existing results**

The notebook uses the existing HDF5 result file and results can be downloaded from https://github.com/pyiron-node-store/pmd03_demonstrators:

`results/gb_run.h5`

The default setting is:

```python
use_result = True
```

This loads the previously calculated workflow results.

**Option 2: Run the calculations again**

To execute the atomistic calculations instead of loading cached results, change:

```python
use_result = False
```

The full calculation considers Cu, Ag, Au and Ni. The notebook also provides a cheaper test configuration.

## 7. Expected Outputs

The workflow produces:

- Relaxed grain-boundary structure
- Symmetrically distinct grain-boundary sites
- Solute segregation energies
- Excess Voronoi volumes
- A plot comparing segregation energies with excess volumes

The analysis investigates the relationship between local atomic volume and solute segregation behaviour.

## 8. Notes and Limitations

The calculated segregation energies depend on the accuracy and applicability of the EMT interatomic potential. The results should therefore be interpreted within the limitations of this potential.

The finite size of the periodic simulation cells can also influence segregation energies through interactions between periodic images and constrained strain fields.

The notebook provides previously calculated results to facilitate inspection without requiring the full calculations to be repeated.

## 9. Acknowledgement and Attribution

This workflow is adapted from the original demonstrator developed by Liam Huber and available in the https://github.com/pyiron-node-store/pmd03_demonstrators repository. The original work is acknowledged, and modifications made in this version are documented where applicable.


