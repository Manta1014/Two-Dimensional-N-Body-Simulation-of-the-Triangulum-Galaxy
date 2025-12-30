# 🌀 Two-Dimensional N-Body Simulation of the Triangulum Galaxy (M33)

This project implements a **two-dimensional N-body simulation** of the **Triangulum Galaxy (M33)** to demonstrate why an **extended dark-matter halo** is required to explain the observed flat galactic rotation curve.

The simulation compares:
- a **visible-matter-only disk model**
- a **visible + dark-matter halo model**

and shows that only the latter reproduces a **flat outer rotation curve**, consistent with astronomical observations.

👉 **[Research Paper (PDF)](https://github.com/Manta1014/Two-Dimensional-N-Body-Simulation-of-the-Triangulum-Galaxy/blob/main/Two-Dimensional%20N-Body%20Simulation%20of%20the%20Triangulum%20Galaxy.pdf)**

---

## 📌 Motivation

Observed rotation curves of spiral galaxies, including M33, remain nearly flat at large radii, contradicting the Keplerian decline expected from visible matter alone.

This project recreates this classic dark-matter argument using a **simplified but physically motivated N-body model**, highlighting how mass distribution affects galactic dynamics.

---

## 🧠 Physical Model

### Gravitational Interaction
- Newtonian gravity with a **softening length** to avoid singular forces:
  
![Gravitational force equation](https://latex.codecogs.com/svg.image?\mathbf{F}_{ij}=G\frac{m_im_j}{(r_{ij}^2+\epsilon^2)^{3/2}}(\mathbf{r}_j-\mathbf{r}_i))

- All quantities are expressed in **dimensionless code units** with \( G = 1 \)

### Components

| Component | Description |
|---------|-------------|
| Stellar Disk | 100 equal-mass particles in a thin 2D disk |
| Dark Matter Halo | 200 heavier particles distributed over a larger radius |
| Integration | Leapfrog (velocity-Verlet), symplectic and energy-stable |

---

## ⚙️ Simulation Setup

| Parameter | Value |
|--------|------|
| Time step | Δt = 0.001 |
| Total steps | 4000 |
| Softening length | ε = 0.01 |
| Snapshot interval | every 200 steps |
| Disk radius | R = 1.0 (code units) |

- Stellar velocities initialized using a **Kepler-like profile** ![Kepler velocity scaling](https://latex.codecogs.com/svg.image?v(r)\propto r^{-1/2}) 
- Dark matter initialized with small random velocities to approximate a halo in near equilibrium

---

## 📊 Outputs & Results

### Disk Evolution
- Visible-only model develops shear and weakly bound outer stars
- Dark-matter model preserves a coherent rotating disk

### Rotation Curves
- **Visible-only model** → declining (Keplerian-like) rotation curve  
- **Visible + dark matter model** → flat outer rotation curve  

This reproduces the qualitative behavior seen in real observations of M33.

### Sensitivity Tests
- Increasing dark-matter mass produces flatter rotation curves
- Varying the softening length affects noise but not the main conclusion

---

## 📂 Project Structure
```
├── triangulum.py          # Main N-body simulation script
├── figures/
│   ├── visible_only_facets.png
│   ├── visible_plus_dm_facets.png
│   └── rotation_curves.png
├── README.md
```

---

## ▶️ How to Run

python triangulum.py

This will:
	1.	Run the visible-only simulation
	2.	Run the visible + dark-matter simulation
	3.	Generate disk evolution plots and rotation curves

---

📚 Key Takeaway

A disk composed of visible matter alone cannot sustain a flat galactic rotation curve.
An extended, massive dark-matter halo is dynamically required.

Despite its simplicity and small particle count, this model clearly illustrates the core physical argument for dark matter in spiral galaxies.

---

🔧 Possible Extensions
	•	3D simulation
	•	Realistic halo profiles (NFW, isothermal)
	•	Energy and angular momentum diagnostics
	•	Larger particle counts with tree-based gravity (Barnes–Hut)
