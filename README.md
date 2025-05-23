# ggcmpy -- Python utilities for the OpenGGCM Global Magnetosphere Code

[![Actions Status][actions-badge]][actions-link]
[![Documentation Status][rtd-badge]][rtd-link]

[![PyPI version][pypi-version]][pypi-link]
[![PyPI platforms][pypi-platforms]][pypi-link]

<!-- [![Conda-Forge][conda-badge]][conda-link] -->

[![GitHub Discussion][github-discussions-badge]][github-discussions-link]

<!-- prettier-ignore-start -->
[actions-badge]:            https://github.com/unh-hpc/ggcmpy/workflows/CI/badge.svg
[actions-link]:             https://github.com/unh-hpc/ggcmpy/actions
[conda-badge]:              https://img.shields.io/conda/vn/conda-forge/ggcmpy
[conda-link]:               https://github.com/conda-forge/ggcmpy-feedstock
[github-discussions-badge]: https://img.shields.io/static/v1?label=Discussions&message=Ask&color=blue&logo=github
[github-discussions-link]:  https://github.com/unh-hpc/ggcmpy/discussions
[pypi-link]:                https://pypi.org/project/ggcmpy/
[pypi-platforms]:           https://img.shields.io/pypi/pyversions/ggcmpy
[pypi-version]:             https://img.shields.io/pypi/v/ggcmpy
[rtd-badge]:                https://readthedocs.org/projects/ggcmpy/badge/?version=latest
[rtd-link]:                 https://ggcmpy.readthedocs.io/en/latest/?badge=latest

<!-- prettier-ignore-end -->

[Documentation](https://ggcmpy.readthedocs.io/)

<!-- SPHINX-START -->

The `ggcmpy` package provides Python utilities designed to work with the
OpenGGCM (Open Geospace General Circulation Model) data, facilitating data
analysis and interaction.

## Features

- **Effortless Data Handling with Xarray:** Read OpenGGCM binary files (`.iof`, `.3df`, `.p[xyz]_N`) directly into [Xarray datasets](https://xarray.dev) using `xr.open_dataset(filename)`. Xarray enhances numpy arrays with labeled dimensions and coordinates, simplifying data analysis.
- **OpenGGCM-Specific Xarray Extensions:** Access specialized coordinates like `mlts` (magnetic local times) and `colats` (colatitudes) in addition to standard `longs` and `lats`.
- **Support for Modern Data Formats:**
    - Read OpenGGCM XDMF/HDF5 data using the [xarray-pschdf5](https://github.com/psc-code/xarray-pschdf5) package.
    - Read OpenGGCM ADIOS2 data using the [xarray-adios2](https://github.com/unh-hpc/xarray-adios2) package.

## Getting Started

### Installation

The recommended way to install `ggcmpy` is using pip:

```bash
pip install ggcmpy
```

### Basic Usage: Reading Data

Here's a quick example of how to open an OpenGGCM data file using `ggcmpy` and `xarray`:

```python
import xarray as xr
# Import ggcmpy to access sample data or specific utilities if needed.
# If you are using your own data files, ggcmpy might only be needed
# for its Xarray backend registration, which happens automatically on import.
import ggcmpy 

# Example using a placeholder for your data file path:
# actual_file_path = "path/to/your/openggcm_data.3df.001200"

# Or, to use sample data provided with ggcmpy (if available and you know the path):
# from ggcmpy import sample_dir
# actual_file_path = sample_dir / "sample_jrrle.py_0.001200"

# For this example, let's define a placeholder. 
# Replace this with the actual path to your data.
actual_file_path = "path/to/your_openggcm_file.3df" 

try:
    # Open the dataset using xarray
    ds = xr.open_dataset(actual_file_path)
    print("Successfully opened dataset:")
    print(ds)
except FileNotFoundError:
    print(f"Error: Data file not found at '{actual_file_path}'.")
    print("Please ensure the path is correct or use ggcmpy's sample data if available.")
except Exception as e:
    print(f"An error occurred: {e}")

```

### Documentation

For more detailed information, including advanced usage and troubleshooting, please see the full [Getting Started Guide](./docs/getting-started-guide/index.md).

## Contributing

Contributions are welcome! We appreciate any help to improve and expand `ggcmpy`. We value all sorts of contributions, from bug reports and documentation improvements to new features.

Please see our [Contributing Guide](./.github/CONTRIBUTING.md) for more details on how to get started, report issues, and make contributions.

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](./LICENSE) file for details.

## Future Enhancements

The following are planned enhancements for `ggcmpy`:

- Advanced OpenGGCM-specific plotting utilities (basic 2D and 3D data visualization is available via Xarray's built-in plotting capabilities).
- Tools to assist with setting up OpenGGCM runs, such as:
    - Generating/modifying `runme` configuration files.
    - Helper utilities for creating non-uniform grids.
    - Tools for preparing solar wind event data.
