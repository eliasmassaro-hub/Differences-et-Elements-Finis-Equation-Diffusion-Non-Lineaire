# Projet EDP — Infiltration de l'eau dans le sol

Résolution numérique des équations de **Darcy** et **Richards** pour modéliser l'infiltration de l'eau dans un sol non saturé, par différences finies (DF) et éléments finis P1 (EF).

**Auteurs :** Massaro · Secondi · Mantsouaka · Presutto

---

## Présentation du projet

Ce projet implémente quatre approches numériques pour simuler l'écoulement en milieu poreux :

| Modèle | Méthode | Dimension |
|---|---|---|
| Darcy non stationnaire (K constant) | Différences finies | 2D |
| Darcy non stationnaire (K constant) | Éléments finis P1 | 2D |
| Richards (K(ψ) et C(ψ) variables) | Différences finies | 1D et 2D |
| Richards (K(ψ) et C(ψ) variables) | Éléments finis P1 | 1D et 2D |

### Modèle de Van Genuchten–Mualem

Les fonctions constitutives du sol θ(ψ), K(ψ) et C(ψ) sont paramétrées selon le modèle de Van Genuchten–Mualem pour trois types de sol :

- **Sable** — drainage rapide, forte conductivité à saturation
- **Limon** — comportement intermédiaire
- **Argile** — rétention d'eau prolongée, faible conductivité

### Équation de Darcy non stationnaire

$$S_s \frac{\partial h}{\partial t} - \nabla \cdot (K \nabla h) = 0$$

avec conditions aux limites : flux de pluie (Neumann) en surface, nappe phréatique (Dirichlet) en bas, parois imperméables (Neumann homogène) sur les côtés.

### Équation de Richards (non linéaire)

$$C(\psi)\frac{\partial \psi}{\partial t} - \nabla \cdot \left[K(\psi)(\nabla \psi + \mathbf{e}_z)\right] = 0$$

Résolue par linéarisation de Picard à chaque pas de temps.

---

## Contenu du dépôt

```
.
├── Code_EDP_Infiltration-eau.ipynb   # Notebook Jupyter — implémentation complète
├── EDP_Rapport_Infiltration-Eau.pdf  # Rapport détaillé du projet
└── README.md
```

---

## Dépendances

```
numpy
scipy
matplotlib
```

Installation :

```bash
pip install numpy scipy matplotlib
```

---

## Lancer le notebook

```bash
jupyter notebook Code_EDP_Infiltration-eau.ipynb
```

Le notebook est auto-contenu : chaque section peut être exécutée indépendamment après avoir lancé les cellules préliminaires (imports et définition des fonctions constitutives).
