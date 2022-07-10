[![Documentation Status](https://readthedocs.org/projects/hyperon-tutorials/badge/?version=latest)](https://hyperon-tutorials.readthedocs.io/en/latest/?badge=latest)


# Tutorials and Documentation for OpenCog Hyperon & MeTTa 

[**OpenCog Hyperon**](https://github.com/trueagi-io/hyperon-experimental) is the next-generation cognitive architecture aiming to achieve true Artificial General Intelligence (AGI). This repository contains the tutorials and documentation for Hyperon and the MeTTa programming language.

> **Note:** This repository is a work in progress. It is not yet complete and is not ready for use.
> 
> Visit [here](https://hyperon-tutorials.readthedocs.io/en/latest/) for the latest build.


## Development for the Documentation

The documentation is built using [Sphinx](https://www.sphinx-doc.org/en/master/) and is published and hosted on [ReadTheDocs](https://readthedocs.org/).

Both reStructuredText and Markdown are supported. The Markdown support is enabled by the [MyST](https://myst-parser.readthedocs.io/en/latest/index.html) extension. By default, all the MyST syntax extensions are enabled. See [here](https://myst-parser.readthedocs.io/en/latest/syntax/optional.html) for more details regarding the allowed syntax. 

## Build the Documentation Locally

To build the documentation locally, install the required python packages first.

```bash
pip install -r requirements.txt
```

Then, go to the `docs/` directory and run the following command to build the documentation in HTML format.

```bash
cd docs
make html
```

The built documentation is located in `docs/build/html/index.html`. 
