# Using `gorder` as a Python package

`gorder` can also be used as a Python package, allowing you to call it directly from your Python code.

## Installing using `uv`

The recommended way to install `gorder` as a Python package is to use the [uv](https://github.com/astral-sh/uv) package manager. To add `gorder` to your `uv` project, run:

```bash
$ uv add git+https://github.com/Ladme/gorder.git#subdirectory=pygorder
```

## Installing using `conda`

`gorder` is also available on [`conda-forge`](https://anaconda.org/conda-forge/pygorder) (credit to [@RubenChM](https://github.com/RubenChM)):

```bash
$ conda create -n gorder
$ conda activate gorder
$ conda install conda-forge::pygorder
```

## Installing using `pip`

If you use neither `uv` or `conda`, you can also install `gorder` simply using `pip`:

```bash
$ pip install git+https://github.com/Ladme/gorder.git#subdirectory=pygorder
```

## Using `gorder`

Once you install the package, import it into your Python code:

```python
import gorder
```

Once imported, you can access all the options and functionality described in this manual.

For instance, the following configuration YAML file:

```yaml
structure: system.tpr
trajectory: md.xtc
analysis_type: !CGOrder
  beads: "@membrane"
output: order.yaml
```

can also by written as the following Python code:

```python
analysis = gorder.Analysis(
    structure = "system.tpr",
    trajectory = "md.xtc",
    analysis_type = gorder.analysis_types.CGOrder("@membrane"),
    output_yaml = "order.yaml",
)
```

You can then run the analysis like this:
```python
results = analysis.run()
```

and either write the results into the output file(s):

```python
results.write()
```

or access them programmatically.

See the Python API documentation on [ladme.github.io/pygorder-docs](https://ladme.github.io/pygorder-docs/) for more information about using `gorder` as a Python package.