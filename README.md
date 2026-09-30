# Quantum Orbital Explorer

An interactive, in-browser simulation of electron orbitals, built directly from the equations of quantum mechanics. Pick an atom or any orbital and see its probability cloud, its nodes, and its radial distribution.

**Live demo:** `https://YOUR-USERNAME.github.io/REPO-NAME/`

## What it shows

- **3D probability cloud.** Each dot is a possible electron position, sampled at random from |ψ|². Drag to rotate, scroll to zoom.
- **Orbitals s, p, d and f** (real forms) for n up to 10, with a different color for each orbital. Select several to overlay them.
- **Nodes.** These are places where ψ = 0 and the electron is never found. They appear as dashed, labeled shells and planes in 3D.
- **Cross-section view.** A slice through the nucleus shown as a heat map. White lines are nodes, and the dark gaps around them are empty space.
- **Radial distribution graph** for every selected orbital, with node markers. Switch between r²|R|², |R|² and R(r).
- **Atoms from H to Kr (Z = 1 to 36).** Click an element in the mini periodic table to see its orbitals, atomic number, period, group, block and electron configuration.
- **Phase view** (±ψ), adjustable dot count, and animation.

## How to run

It is a single file with no dependencies and no build step.

1. Download `index.html`.
2. Open it in any modern browser.

To host it on GitHub Pages: **Settings → Pages → Deploy from a branch → `main` / root**.

## The physics

Each orbital is a hydrogen-like wavefunction:

```
ψ(r,θ,φ) = R(r) · Y(θ,φ)
R(r) ∝ ρ^l · e^(−ρ/2) · L(ρ),   ρ = 2Zr / (n·a₀)
P(r) = r² |R(r)|²
```

- R(r) uses associated Laguerre polynomials, computed numerically and normalized.
- Y(θ,φ) is the real spherical harmonic for the chosen orbital.
- The radius is sampled from the radial distribution, and the direction from |Y|² by rejection sampling.
- Radial nodes = n − l − 1. Angular nodes = l.
- Energy: Eₙ = −13.6 eV · Z² / n².

## Limitations

- For multi-electron atoms, Z is replaced by an effective charge from Slater's rules. The shapes are therefore hydrogen-like approximations, not exact many-electron orbitals.
- The 3D view draws nodal planes only for p orbitals and for dxz, dyz, dxy and fxyz. The curved (conical) nodes of the other d and f orbitals are clearest in the cross-section view.
- The elements stop at Z = 36.

## License

MIT. Use it freely, and credit is appreciated.
