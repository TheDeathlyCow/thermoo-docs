# Thermoo Docs

This repo contains the mkdocs source for the Thermoo Developer Wiki. Thermoo is a temperature and environment API for Minecraft: Java Edition, and its source can be found at https://github.com/TheDeathlyCow/thermoo/

## Live Website

The live website can be found at https://thermoo.thedeathlycow.com/

## Wiki Build Instructions

The Thermoo Developer wiki is built with [MkDocs](https://www.mkdocs.org/) using the [Material Theme](https://squidfunk.github.io/mkdocs-material/). To install mkdocs, Python 3 is required: https://www.python.org/.

The following commands will install the requirements for mkdocs:
```bash
pip install mkdocs
pip install mkdocs-material
```

You can then run a local version of the Wiki:
```bash
cd wiki/
mkdocs serve
```

The wiki should then be available on http://localhost:8000/.

In order to deploy the wiki using GitHub pages, run:
```bash
mkdocs gh-deploy --force
```

This will deploy the site to https://your-username.github.io/thermoo, where it will be available on the public internet.
