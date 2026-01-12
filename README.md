# DSC180B Quarter 2 Project

---

# Running the Project Using Docker

To ensure reproducibility, we provide a minimal Docker environment that supports the dependencies required for:

- `generating_simulated_data.ipynb`
- `PC_alg.ipynb`

---

## 1. Build the Docker Image

From the repository root:

```bash
docker build -t causal-copilot-notebooks .
```

---

## 2. Run a Container With the Project Mounted

```bash
docker run --rm -it \
  -v "$(pwd):/workspace" \
  -p 8888:8888 \
  causal-copilot-notebooks
```

Then inside the container:

```bash
jupyter lab --ip=0.0.0.0 --no-browser --NotebookApp.token=''
```

Open:

```
http://localhost:8888
```

---

## 3. Running the Notebooks

Open and execute:

```
* generating_simulated_data.ipynb
* PC_alg.ipynb
```

The simulation notebook will automatically create timestamped output folders under simulated_data/.

The PC algorithm notebook will:

- Load simulated data
- Run the PC algorithm
- Visualize the inferred CPDAG
- Compute Structural Hamming Distance (SHD)
- Compare inferred graphs against the true simulated structure

---

## 4. Exiting the Container

To exit the running container:

```bash
exit
```

---

# Additional Notes

- This repository currently includes only the dependencies required for Quarter 1 deliverables.
- Full LaTeX, GPU, and advanced Causal Copilot tooling will be added in future project phases.

---

## Dependencies & Versions Installed in the Docker Image

The environment is built on:

**Base image:**
- `python:3.12-slim`

**System packages:**
- `graphviz` (required for PC algorithm graph visualization)

**Python libraries (as pinned in requirements_notebooks.txt):**
- `numpy==1.26.4`
- `pandas==1.5.3`
- `matplotlib==3.9.2`
- `scipy==1.13.1`
- `scikit-learn==1.5.2`
- `networkx==3.2.1`
- `python-igraph==0.11.8`
- `texttable==1.7.0` (igraph dependency)
- `causal-learn==0.1.3.9`
- `pydot==3.0.2` (GraphViz wrapper)
- `typing-extensions==4.12.2`
- `tqdm==4.66.5`

These packages are the **only** dependencies required to run the Quarter 1 deliverables.  

---
