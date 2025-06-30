# By: Jesse-Don-Steelman
# MASTERKEY9 Unification Simulation

[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/matr9-masterkey9-sim)](https://pypi.org/project/matr9-masterkey9-sim/)
[![PyPI](https://img.shields.io/pypi/v/matr9-masterkey9-sim)](https://pypi.org/project/matr9-masterkey9-sim/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Stars](https://img.shields.io/github/stars/WizardOfNine/matr9-masterkey9-sim?style=social)](https://github.com/WizardOfNine/matr9-masterkey9-sim)

## Overview

The `matr9-masterkey9-sim` project is an open-source Python package that computationally models the **MATR9/MASTERKEY9 Unified Trinitarian Principle**. It explores how fundamental Golden Ratio ($\phi$) dynamics, when guided by an active unifying force (MASTERKEY9), lead to phase-locked resonance and inherent coherence within a dynamic system.

This simulation provides a tangible framework for understanding how seemingly disparate components can achieve synchronized, harmonious function, embodying universal principles of order and creation.

## The Core Principles: A Symbolic and Philosophical Layer

The system is built upon a trinitarian conceptual framework, where three distinct aspects interact and are unified:

* **MATR9($1/\phi$)**: Represents the **"Primordial Template"** or **"Father"**. This aspect embodies the reciprocal origin, defining the fundamental blueprint or source of form.
* **MATR9($\phi$)**: Represents the **"Living Pattern"** or **"Son"**. This aspect embodies generative balance, the active and dynamic unfolding of the template into a living, evolving form.
* **MATR9($\phi^2$)**: Represents the **"Evolving Field"** or **"Spirit"**. This aspect embodies expansive unfolding, representing the outward growth, accumulation, and interaction of the pattern within a broader field.

**MASTERKEY9**: This meta-framework serves as the **"Unified Logos"** or **"The Word made Flesh"**. Its role is to actively enforce **perfect resonance** and **phase lock coherence** across all three MATR9 aspects. MASTERKEY9 ensures that despite individual scaling and progression, the system maintains synchronized, maximized vibrational resonance, leading to a unified field of operation. It is the active principle of unification.

## Mathematical Definition & Logic/Rules

The system's behavior is precisely defined by the following mathematical framework, which has been rigorously verified by multiple AI models.

**1. Fundamental Constants and Ratios:**

* **Golden Ratio ($\phi$)**:
    $\phi \approx 1.61803398875$
* **Inverse Golden Ratio ($\phi_{inv}$)**:
    $\phi_{inv} = \frac{1}{\phi} = \phi - 1 \approx 0.61803398875$
* **Golden Ratio Squared ($\phi_{sq}$)**:
    $\phi_{sq} = \phi^2 \approx 2.61803398875$
* **Angular Resolution Parameters**: These define the resolution for the angular mapping within the system's conceptual grid.
    * $N_i = 9$
    * $N_j = 24$

**2. Toroidal Coordinate Mapping ($\theta$ function):**

This function maps a pair of integer indices $(i, j)$ to a point $\mathbf{p} = (x, y)$ in a 2D Cartesian plane, simulating a conceptual projection from a toroidal-like structure.
For given integer indices $i$ and $j$:
$x = \cos\left(\frac{2\pi i}{N_i}\right)$
$y = \sin\left(\frac{2\pi j}{N_j}\right)$
Result: $\theta(i, j) = (x, y)$

**3. Seed Coordinates:**

These are foundational 2D points, derived from the $\theta$ function, that serve as starting references for the system's progression.

* **J-Expected ($j_{\text{expected}}$)**: A fractional value indicating a specific point along the $j$-axis before discretization for $\theta$.
    $j_{\text{expected}} = \phi_{inv} \times N_j$
* **J-Alternate ($j_{\text{alt}}$)**: A fractional value derived from $N_j$ and $j_{\text{expected}}$.
    $j_{\text{alt}} = N_j - j_{\text{expected}}$
* **Expected Seed ($\mathbf{SEED}_{\text{EXPECTED}}$)**:
    $\mathbf{SEED}_{\text{EXPECTED}} = \theta(1, \lfloor j_{\text{expected}} \rfloor \pmod{N_j})$
* **Alternate Seed ($\mathbf{SEED}_{\text{ALT}}$)**:
    $\mathbf{SEED}_{\text{ALT}} = \theta(1, \lfloor j_{\text{alt}} \rfloor \pmod{N_j})$

**4. MATR9 Progression (Recursive Step for each Version):**

The simulation models three distinct MATR9 versions, indexed by $V \in \{1, 2, 3\}$, each operating with a unique scaling factor $S_V$.
The scaling factors are: $S_1 = \phi_{inv}$, $S_2 = \phi$, $S_3 = \phi_{sq}$.

Let $\mathbf{C}_V^{(L-1)} = (C^{(L-1)}_{V,x}, C^{(L-1)}_{V,y})$ denote the **adjusted centroid** of MATR9 version $V$ at the end of layer $L-1$. For the initial layer ($L=1$), the starting centroid for all versions is $\mathbf{C}_V^{(0)} = \mathbf{SEED}_{\text{ALT}}$.

For each layer $L \in \{1, ..., 9\}$ and each MATR9 version $V$:

* **Distance `d` Calculation ($d^{(L)}_V$):** The Euclidean distance from the current centroid $\mathbf{C}_V^{(L-1)}$ to $\mathbf{SEED}_{\text{ALT}}$.
    $d^{(L)}_V = \|\mathbf{C}_V^{(L-1)} - \mathbf{SEED}_{\text{ALT}}\| = \sqrt{\left(C^{(L-1)}_{V,x} - \text{SEED}_{\text{ALT},x}\right)^2 + \left(C^{(L-1)}_{V,y} - \text{SEED}_{\text{ALT},y}\right)^2}$

* **L-Vector Calculation ($\mathbf{L}^{(L,V)}$):** A 3-component vector derived by scaling the current centroid coordinates and the distance $d^{(L)}_V$ by the version's specific scaling factor $S_V$.
    $\mathbf{L}^{(L,V)} = \left[ C^{(L-1)}_{V,x} \times S_V, \quad C^{(L-1)}_{V,y} \times S_V, \quad d^{(L)}_V \times S_V \right]$

* **$\Theta$ Coordinates Derivation ($\mathbf{\Theta}_{\text{coords}}^{(L,V)}$):** Each component of the $\mathbf{L}^{(L,V)}$ vector is used to derive an integer $j$-index for a $\theta$ coordinate. The corresponding $i$-index is set by the component's position (0, 1, or 2). This step involves **discretization** via flooring and modulo operations to ensure integer indices for $\theta$.
    For each component $k \in \{0, 1, 2\}$ of $\mathbf{L}^{(L,V)}$:
    $val_k = \mathbf{L}^{(L,V)}[k]$
    $j_k = \lfloor val_k \rfloor \pmod{N_j}$
    The $k^{th}$ $\Theta$ coordinate is $\theta(k, j_k)$.
    Result: $\mathbf{\Theta}_{\text{coords}}^{(L,V)} = \left\{ \theta(0, j_0), \theta(1, j_1), \theta(2, j_2) \right\}$

* **Preliminary Centroid Calculation ($\mathbf{P}_C^{(L,V)}$):** The geometric centroid (average position) of the three $\Theta$ coordinates for the current version $V$ and layer $L$.
    $\mathbf{P}_C^{(L,V)} = \left( \frac{1}{3}\sum_{k=0}^{2} (\theta(k, j_k)_x), \quad \frac{1}{3}\sum_{k=0}^{2} (\theta(k, j_k)_y) \right)$

**5. MASTERKEY9 Active Phase-Locking (Inter-Version Coherence):**

This critical step enforces coherence by adjusting the preliminary centroids of all three MATR9 versions based on their collective average for the current layer $L$. A `coherence_strength` parameter, denoted as $\alpha \in [0, 1]$, defines the intensity of this unifying force.

* **MASTERKEY9 Target Centroid ($\mathbf{MK9}_{T_C}^{(L)}$):** The average of the preliminary centroids of all three MATR9 versions for the current layer $L$. This represents the ideal point of collective coherence that MASTERKEY9 pulls the system towards.
    $\mathbf{MK9}_{T_C}^{(L)} = \frac{1}{3}\sum_{V=1}^{3} \mathbf{P}_C^{(L,V)}$

* **Adjusted Centroid Calculation ($\mathbf{A}_{C}^{(L,V)}$):** For each MATR9 version $V$, its preliminary centroid $\mathbf{P}_C^{(L,V)}$ is adjusted by being pulled towards the $\mathbf{MK9}_{T_C}^{(L)}$. This **adjusted centroid** then becomes the starting centroid for the next layer's calculation, i.e., $\mathbf{C}_V^{(L)} = \mathbf{A}_{C}^{(L,V)}$.
    $\mathbf{A}_{C}^{(L,V)} = \mathbf{P}_C^{(L,V)} + \alpha \cdot \left(\mathbf{MK9}_{T_C}^{(L)} - \mathbf{P}_C^{(L,V)}\right)$

**6. MASTERKEY9 Phase Lock Coherence Metric:**

This metric quantifies the collective coherence of the three MATR9 versions at each layer, using their **adjusted centroids** ($\mathbf{A}_{C}^{(L,V)}$).

For each layer $L$:
* **Pairwise Distances:** The Euclidean distances between the adjusted centroids of each pair of MATR9 versions.
    $d_{12}^{(L)} = \|\mathbf{A}_{C}^{(L,1)} - \mathbf{A}_{C}^{(L,2)}\|$
    $d_{23}^{(L)} = \|\mathbf{A}_{C}^{(L,2)} - \mathbf{A}_{C}^{(L,3)}\|$
    $d_{31}^{(L)} = \|\mathbf{A}_{C}^{(L,3)} - \mathbf{A}_{C}^{(L,1)}\|$

* **Average Phase Distance ($APD^{(L)}$):** The average of these three pairwise distances. This value serves as the primary indicator of the system's overall coherence at a given layer; a decreasing $APD^{(L)}$ signifies increasing phase lock.
    $APD^{(L)} = \frac{d_{12}^{(L)} + d_{23}^{(L)} + d_{31}^{(L)}}{3}$

## Installation

You can install the `matr9-masterkey9-sim` package using pip:

```bash
pip install matr9-masterkey9-sim
