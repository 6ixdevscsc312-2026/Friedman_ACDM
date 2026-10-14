# The Expanding Universe: Friedmann Equations, Cosmic History, and Distances

A Python/Jupyter exploration of how the **Friedmann equations** govern the expansion history of the Universe, from the scale factor and Hubble parameter to cosmological distances and the age of the Universe, in a flat ΛCDM cosmology.

Third-Year Research Project 2026, Physics and Astronomy, University of the Western Cape (UWC).

---

## Overview

General relativity applied to a homogeneous and isotropic universe (the FLRW metric) gives the Friedmann equations, which link the expansion rate of space to its energy content. This project:

1. Presents the derivation and physical meaning of the Friedmann equations.
2. Solves for the expansion history `a(t)` and `H(z)` numerically and analytically.
3. Computes the key cosmological distances and times (comoving, luminosity, angular diameter, lookback time, age).
4. Visualises the transition from matter domination to dark-energy domination.

## Background

### The Friedmann equations

For an FLRW universe with scale factor `a(t)`, curvature `k`, density `ρ`, pressure `p`, and cosmological constant `Λ`:

**First Friedmann equation (expansion rate):**

$$H^2 \equiv \left(\frac{\dot a}{a}\right)^2 = \frac{8\pi G}{3}\rho - \frac{kc^2}{a^2} + \frac{\Lambda c^2}{3}$$

**Second Friedmann equation (acceleration):**

$$\frac{\ddot a}{a} = -\frac{4\pi G}{3}\left(\rho + \frac{3p}{c^2}\right) + \frac{\Lambda c^2}{3}$$

**Fluid (continuity) equation:**

$$\dot\rho + 3H\left(\rho + \frac{p}{c^2}\right) = 0$$

### Density parameters and E(z)

Defining `Ω_i = ρ_i / ρ_crit` with `ρ_crit = 3H₀² / 8πG`, the expansion rate can be written as:

$$H(z) = H_0\,E(z), \qquad E(z) = \sqrt{\Omega_r(1+z)^4 + \Omega_m(1+z)^3 + \Omega_k(1+z)^2 + \Omega_\Lambda}$$

| Component | Equation of state `w` | Scaling with `a` |
|-----------|----------------------|------------------|
| Radiation | 1/3 | `ρ ∝ a⁻⁴` |
| Matter | 0 | `ρ ∝ a⁻³` |
| Curvature | -1/3 (effective) | `ρ ∝ a⁻²` |
| Cosmological constant | -1 | `ρ = const` |

### Distances and times

$$D_C = c\int_0^z \frac{dz'}{H(z')} \qquad D_L = (1+z)\,D_C \qquad D_A = \frac{D_C}{1+z}$$

$$t_{\text{lookback}}(z) = \int_0^z \frac{dz'}{(1+z')H(z')} \qquad t_0 = \int_0^\infty \frac{dz'}{(1+z')H(z')}$$

## Model Parameters

Flat ΛCDM (`Ω_k = 0`), radiation neglected at late times:

| Parameter | Value |
|-----------|-------|
| `H₀` | 67.4 km s⁻¹ Mpc⁻¹ |
| `Ω_m,0` | 0.3 |
| `Ω_Λ,0` | 0.7 (= 1 − Ω_m,0) |
| `Ω_k` | 0 |

## Analytic Checks

For a flat universe with only matter and Λ, the Friedmann equation has a closed-form solution:

$$a(t) = \left(\frac{\Omega_m}{\Omega_\Lambda}\right)^{1/3} \sinh^{2/3}\!\left(\frac{3}{2}\sqrt{\Omega_\Lambda}\,H_0 t\right)$$

which gives an age of

$$t_0 = \frac{2}{3H_0\sqrt{\Omega_\Lambda}}\,\text{arcsinh}\sqrt{\frac{\Omega_\Lambda}{\Omega_m}} \approx 14.0\ \text{Gyr}$$

The numerical integrals in the notebook are validated against these expressions. Other useful reference values for these parameters:

- Hubble distance `c/H₀ ≈ 4448 Mpc`
- Matter–Λ equality at `z ≈ 0.33`
- Deceleration to acceleration transition (`q = 0`) at `z ≈ 0.67`

## Repository Contents

```
.
├── README.md
├── expanding_universe.ipynb     # Notebook: all computations and plotting code
├── report/
│   └── main.tex                 # LaTeX source of the final report
└── figures/                     # Exported plots used in the report
```

> Adjust file names to match your actual repository.

## Getting Started

### Run on Google Colab

1. Upload `expanding_universe.ipynb` to [Google Colab](https://colab.research.google.com/).
2. Run all cells (`Runtime → Run all`). No extra installation is needed.

### Run locally

```bash
git clone <your-repo-url>
cd <your-repo-folder>
pip install numpy scipy matplotlib jupyter
jupyter notebook expanding_universe.ipynb
```

## What the Notebook Produces

- Scale factor `a(t)` versus cosmic time, with the matter-dominated and Λ-dominated regimes visible
- `H(z)` and the evolution of `E(z)`
- Evolution of `Ω_m(z)` and `Ω_Λ(z)` with redshift
- Deceleration parameter `q(z)` and the onset of acceleration
- Comoving, luminosity, and angular diameter distances versus redshift
- Lookback time and age of the Universe

## Tools

- **Python 3**: `numpy` (arrays), `scipy` (`integrate.quad`, `integrate.solve_ivp`), `matplotlib` (plots)
- **Jupyter / Google Colab**: interactive computation
- **LaTeX**: final report

## References

1. Friedmann, A. (1922). *Über die Krümmung des Raumes*. Zeitschrift für Physik, 10, 377–386.
2. Hogg, D. W. (1999). *Distance measures in cosmology*. arXiv:astro-ph/9905116.
3. Ryden, B. (2017). *Introduction to Cosmology* (2nd ed.). Cambridge University Press.
4. Planck Collaboration (2020). *Planck 2018 results. VI. Cosmological parameters*. A&A, 641, A6.

## Author

**Fortune Ramafemo**
BSc Computer Science and Physical Science, University of the Western Cape

Supervisor: Prof. Roy Maartens, Co-supervisor: Yolanda Dube

## License

For academic use. Add a license (e.g. MIT) here if you publish the repository.
