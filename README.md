# example_package_MLSD

Ce projet est un exemple de package Python minimal, créé en suivant le guide officiel [Packaging Python Projects](https://packaging.python.org/en/latest/tutorials/packaging-projects/).  
Il a pour but d’illustrer les étapes nécessaires à la création, la construction et la publication d’un package sur PyPI (ou TestPyPI).

---

## 📦 Objectif

Ce package contient une fonction simple `add_one()` qui incrémente un entier.  
Il peut servir de base pour créer des packages plus complexes.

---

## 🛠 Structure du projet

```
example_package_MLSD/
├── LICENSE
├── pyproject.toml
├── README.md
├── src/
│   └── example_package_MLSD/
│       ├── __init__.py
│       └── example.py
└── tests/
```

---

## 🧩 Fichiers importants

- `pyproject.toml` : définit les métadonnées du projet et le backend de build (`hatchling` dans ce cas).
- `example.py` : contient la fonction principale `add_one()`.
- `README.md` : ce fichier, affiché sur PyPI.
- `LICENSE` : licence du projet (MIT ici).
- `tests/` : répertoire prévu pour les tests unitaires (vide ).

---

## 🔨 Étapes de création du package

1. Organisation du code dans `src/example_package_MLSD/` avec un fichier `__init__.py`.

2. Configuration du projet dans `pyproject.toml` (nom, version, auteur, description, etc.).

3. Ajout d’un `README.md` pour la description sur PyPI.

4. Ajout d’une licence (ex: MIT).

5. Installation des outils de build :

```bash
python -m pip install --upgrade build
```

6. Création des archives du package :

```bash
python -m build
```

Cela génère deux fichiers dans le dossier `dist/` :
- `.whl` (wheel)
- `.tar.gz` (source archive)

7. Téléversement sur TestPyPI :

```bash
python -m pip install --upgrade twine
python -m twine upload --repository testpypi dist/*
```

👉 *(Utiliser un token API depuis [TestPyPI](https://test.pypi.org/account/register/))*

8. Installation depuis TestPyPI :

```bash
python -m pip install --index-url https://test.pypi.org/simple/ --no-deps example-package-MLSD
```

---

## ✅ Test rapide

```python
from example_package_MLSD import example

print(example.add_one(2))  # Affiche 3
```

---

## 🚀 Prochaines étapes

- Ajouter des tests dans le dossier `tests/`
- Ajouter des dépendances éventuelles dans `pyproject.toml`
- Publier sur le vrai PyPI avec :

```bash
python -m twine upload dist/*
```
