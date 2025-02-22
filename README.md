# PHY671: Multiscale Materials Modelling, from Atomistic to Macroscopic Methods

## Graphene Poisson Ratio Simulation

This repository contains the course project for **PHY671: Multiscale Materials Modelling, from Atomistic to Macroscopic Methods** at the École Polytechnique (Institut Polytechnique de Paris). In this project, a graphene sheet is simulated under uniaxial tension using LAMMPS. The goal is to analyze the variation of its Poisson ratio with applied strain. The methodology follows the approach described in the paper:

> **Pacheco-Sanjuán, A., & Batra, R. C. (2023).** Insights into the auxetic behavior of graphene: A study on the temperature dependence of Poisson's ratio and in-plane moduli. *Carbon, 215*, 118416. [https://doi.org/10.1016/j.carbon.2023.118416](https://doi.org/10.1016/j.carbon.2023.118416)

Post-processing is performed in **Python**, utilizing Jupyter Notebooks to visualize results and calculate the Poisson Ratio.

## Project Overview

- **Graphene Microstructure**: Two sizes provided (M and L) in `.lmp` format
- **Simulation Software**: [LAMMPS](https://www.lammps.org/)
- **Post-Processing**: Python (Jupyter Notebooks)

## Repository Contents

### 1. Microstructure Generation and Graphene Structure Files

The graphene structure was generated using **Atomsk** with the following commands:

```sh
atomsk --create graphite 2.46 C -cut above 0.1 Z graphene.xsf
atomsk graphene.xsf -orthogonal-cell -duplicate 52 30 1 graphene_L.xsf
atomsk graphene_L.xsf lmp
```

Two graphene structure files of different sizes are provided in this repository:
- `graphene_M.lmp` – Smaller graphene microstructure (17×10 hexagons, 680 carbon atoms)
- `graphene_L.lmp` – Larger graphene microstructure (52×30 hexagons, 6240 carbon atoms)

### 2. LAMMPS Simulation

- `in.graphene` – LAMMPS input script for running the graphene simulation

### 3. Post-Processing & Analysis

- `poisson.ipynb` – Jupyter Notebook for animating the simulation, computing the Poisson ratio, plotting results, and analyzing the data.
- `gamma_graphene.ipynb` – Bonus Jupyter Notebook for generating a $\gamma$-graphene-like unit cell, as presented in [Paupitz et al., 2022](https://doi.org/10.1016/j.cplett.2021.139220).

## Running the Simulation

1. Install **LAMMPS** and required Python dependencies (`numpy`, `pandas`, `scipy`, `matplotlib`, `ipython`)
2. Run LAMMPS simulation:
   ```sh
   lmp -in in.graphene
   ```
3. Execute Jupyter Notebooks for post-processing and visualization.

## Results

The **Poisson ratio** is calculated using two methods: one based on **local strains** and the other on **global strains**, both derived from the **xyz coordinates** of atomic positions. The approach for computing local strains is detailed in the referenced paper. The results are presented through various plots.

## License

This project is shared for educational purposes. Modify and use it as needed.

