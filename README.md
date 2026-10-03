# python-template

Plantilla [Copier](https://copier.readthedocs.io) para proyectos Python con
**uv**, **ruff**, **pytest**, **Makefile** y logging listo para usar.

## Qué genera

```
mi_proyecto/
├── pyproject.toml          # uv + hatchling, pytest, ruff (incluye orden de imports)
├── Makefile                # make setup | test | lint | format | check | diagrams | clean
├── .pre-commit-config.yaml
├── .gitignore  .env.example  .python-version
├── src/<paquete>/          # __init__, __main__ y logging_setup.py
├── tests/{unit,integration}/
├── logs/  docs/diagrams/
└── README.md
```

## Instalación (una sola vez)

```bash
uv tool install copier
```

## Crear un proyecto nuevo

```bash
copier copy gh:EricLuceroGonzalez/python-template mi_proyecto
cd mi_proyecto
make setup
```

Copier pregunta nombre, descripción, versión de Python y autor.
Para probar la plantilla en local, sin GitHub, desde la carpeta que la contiene:

```bash
copier copy --trust ./python-template mi_proyecto
```

## Actualizar proyectos ya creados

Cuando mejores la plantilla, haz commit y push (no hacen falta tags):

```bash
cd python-template
git add . && git commit -m "Mejora del Makefile" && git push
```

Y en cada proyecto generado con ella:

```bash
cd mi_proyecto
git status                 # debe estar limpio: confirma tus cambios antes
copier update --trust
git diff                   # revisa lo que cambió, luego commit
```

> Sin tags, Copier toma el **último commit** de la plantilla (`HEAD`) y lo
> anota como `_commit` en `.copier-answers.yml`. Ese archivo es el que permite
> actualizar: no lo borres ni lo edites a mano.

## Notas

- El `Makefile` usa **tabuladores** (lo exige `make`); el editor no debe convertirlos en espacios.
- `make diagrams` necesita graphviz: `brew install graphviz`.

