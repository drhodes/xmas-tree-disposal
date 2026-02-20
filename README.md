# JupyterLite Exercise: The Christmas Tree Disposal Problem

This exercise explores a simulation of a social contagion effect on a real number line.

## Problem Description

Imagine a neighborhood where houses are located at every integer point on the real number line. Every household celebrates Christmas and has a Christmas tree.

### 1. The Initial Disposal Schedule
Each household decides when to dispose of their Christmas tree based on a random variable $T_i$, where $i$ is the house's position (the integer). 

- The disposal day is relative to Christmas Day ($t=0$).
- Most people follow a distribution that peaks several days after Christmas.
- Notably, very few people dispose of their trees on December 26 ($t=1$), though a small fraction still does.
- Let $T_i^0$ be the "natural" disposal day for household $i$, drawn from a distribution $P(T)$.

### 2. The Social Contagion Effect
A complicating factor is the influence of neighbors. If a household sees a neighbor's tree on the curb, it hastens their own decision to dispose of their tree.

- Let $T_i$ be the actual disposal day for household $i$.
- If a neighbor at $i-1$ or $i+1$ disposes of their tree at time $T_{i \pm 1} < T_i^0$, it may cause household $i$ to move their disposal day earlier.
- The rule for updated disposal time $T_i$ could be:
  $T_i = \min(T_i^0, \text{neighbor\_influence}(T_{i-1}, T_{i+1}))$

## The Challenge
Your task is to implement this simulation in a JupyterLite notebook.

1. **Define the Natural Distribution**: Create a probability distribution for $T_i^0$ that reflects the "post-Christmas" behavior described (low at $t=1$, peaking later).
2. **Model the Interaction**: Define how a neighbor's action influences the household. Does it hasten it by a fixed number of days? Or does it set a new maximum wait time?
3. **Simulate the Neighborhood**: Run the simulation for a range of houses (e.g., $i \in [-100, 100]$) and observe how the "tree disposal wave" propagates through the neighborhood.
4. **Analyze the Results**: 
   - How does the social contagion affect the average disposal day?
   - Are there "clusters" of disposal?
   - How does the initial small group of "early disposers" ($t=1$) influence the rest of the line?

## Getting Started

This project is set up to deploy as a [JupyterLite](https://jupyterlite.readthedocs.io/) static site via GitHub Pages. Once deployed, anyone can open and run the notebook directly in their browser — no installation required.

### Try it online

> **`https://<your-username>.github.io/jupyterlite-exercise/`**

Opening that URL will directly open the notebook and kick off the JupyterLite instance.

### Enable GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Set the source to **GitHub Actions**.
4. The included workflow (`.github/workflows/deploy.yml`) will automatically build and deploy on every push to `main`.

### Local development

```bash
pip install -r requirements.txt
jupyter lite build --contents content --output-dir dist
cp index.html dist/index.html
# Serve dist/ with any static file server, e.g.:
python -m http.server -d dist
```
