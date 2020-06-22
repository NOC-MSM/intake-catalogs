# intake-catalogs

Catalogs based on [intake](https://intake.readthedocs.io/en/latest/) and the pugin [intake-xarray](https://intake-xarray.readthedocs.io/en/latest/).

## Quick start:
Install `intake-xarray`:
```
conda install -c conda-forge intake-xarray
```

Import the main catalog:
```python
import intake
cat = intake.open_catalog('./catalog.yaml')
```

Find all available catalogs:
```python
list(cat)
```

Find the entries in a catalog (e.g., JASMIN):
```python
list(cat.JASMIN)
```

Select an entry (e.g., ORCA0083_N006):
```python
# same as cat.JASMIN["ORCA0083_N006"]
cat.JASMIN.ORCA0083_N006
```

Get the description of an entry:
```python
cat.JASMIN.ORCA0083_N006.description
```

Get a dictionary with detailed info and metadata of an entry:
```python
# For example, user_parameters tells the additional parameters that can be set,
# such as year, grid, ...
cat.JASMIN.ORCA0083_N006.describe()
```

Open a catalog entry:
```python
# ds is a xarray.Dataset
ds = cat.JASMIN.ORCA0083_N006.to_dask()
```

Open a catalog entry using different parameters:
```python
ds = cat.JASMIN.ORCA0083_N006(grid='U', year=1990).to_dask()
```

## Cookbook
See the [cookbook](./cookbook) folder for a collection of recipes to open datasets.