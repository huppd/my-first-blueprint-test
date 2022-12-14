# Contributing

Contributions are welcome, and they are greatly appreciated! Every little bit helps, and credit will always be given.

## Types of Contributions

You can contribute in many ways.

### Report Bugs

Report bugs as [GitHub issues](https://github.com/MeteoSwiss-APN/my-first-blueprint-test/issues).

If you are reporting a bug, please include

- your operating system name and version,
- any details about your local setup that might be helpful in troubleshooting, and
- detailed steps to reproduce the bug.

### Fix Bugs

Look through the [GitHub issues](https://github.com/MeteoSwiss-APN/my-first-blueprint-test/issues) for bugs. Anything tagged with "bug" and "help wanted" is open to whoever wants to implement it.

### Implement Features

Look through the  [GitHub issues](https://github.com/MeteoSwiss-APN/my-first-blueprint-test/issues) for features. Anything tagged with "enhancement" and "help wanted" is open to whoever wants to implement it.

### Write Documentation

my first blueprint test could always use more documentation, whether as part of the official my first blueprint test docs, in docstrings --- or even on the web in blog posts, articles, and such.

### Submit Feedback

The best way to send feedback is to file a [GitHub issue]( https://github.com/MeteoSwiss-APN/my-first-blueprint-test/issues).

If you are proposing a feature,

- explain in detail how it would work;
- keep the scope as narrow as possible, to make it easier to implement; and
- remember that this is a volunteer-driven project, and that contributions are welcome! :)

## Get Started!

Ready to contribute? Here's how to set up `my-first-blueprint-test` for local development.

1. Fork the [`my-first-blueprint-test` repo](https://github.com/ on GitHub.
2. Clone your fork locally:

    ```bash
    git clone git@github.com:your_name_here/my-first-blueprint-test.git
    ```

3. Create a virtual environment and install the development dependencies:

    ```bash
    cd my-first-blueprint-test/
    ./setup_env -di
    ```

    This will create a conda environment named `my-first-blueprint-test-dev` (change with `-n`) and install the following:

    - Pinned runtime dependencies in `requirements/environment.yml`
    - Pinned Development dependencies in `requirements/dev-environment.yml`
    - The `my-first-blueprint-test` package itself in editable mode.

    Activate the environment:

    ```bash
    conda activate my-first-blueprint-test-dev
    ```
    Use `-u` to get the newest package versions (unpinned dependencies in `requirements/requirements.yml` and `requirements/dev-requirements.yml`), and additionally `-e` to update the environment files.

4. Create a branch for local development:

    ```bash
    git switch -c name-of-your-bugfix-or-feature
    ```

    Now you can make your changes locally.

5. When you're done with a change, format and check the code using various installed tools like `black`, `isort`, `mypy`, `flake8` or `pylint`. Those that are set up as pre-commit hooks can be run together with:

    ```bash
    pre-commit run -a
    ```

    Next, ensure that the code does what it is supposed to do by running the tests with pytest:

    ```bash
    pytest
    ```

6. Commit your changes and push your branch to GitHub:

    ```bash
    git add .
    git commit -m "fixed this and did that"
    git push origin name-of-your-bugfix-or-feature
    ```

7. Submit a pull request through the GitHub website.

## Pull Request Guidelines

Before you submit a pull request, check that it meets these guidelines:

1. The pull request should include tests.
2. If the pull request adds functionality, the docs should be updated. Put your new functionality into a function with a docstring, and add the feature to the list in `README.md`.
3. The pull request should work for Python 3.6 and 3.7, and for PyPy. Make sure that the tests pass for all supported Python versions.

## Tips

For a subset of tests or a specific test, run:

```bash
pytest tests.test_my_first_blueprint_test
pytest tests.test_my_first_blueprint_test/test_feature::test_edge_case
```

## Versioning

In order to release a new version of your project, follow these steps:

- Make sure everything is committed, cleaned up and validating (duh!). Don't forget to keep track of the changes in `HISTORY.md`.
- Increase the version number that is hardcoded in `pyproject.toml` (and only there) and commit.
- Either create a (preferentially annotated) tag with `git tag`, or directly create a release on GitHub.

## Project Structure

Following is a description of the most important files and folders in the project in alphabetic order.

- `.github/workflows/`: [GitHub Actions](https://docs.github.com/en/actions) workflows, e.g., checks that are run when certain branches are pushed.
- `docs/`: Documentation.
- `jenkins/`: Jenkins setup.
- `requirements/`: Various kinds of dependencies with different degrees of version restrictions.
    - `dev-environment.yml`: Complete tree of runtime and development dependencies with fully pinned version numbers; created with `conda env export`; (approximately) a superset of those in `environment.yml`.
    - `dev-requirements.yml`: Top-level development dependencies with only necessary version restrictions (typically a minimum version or a version range); kept manually.
    - `environment.yml`: Complete tree of runtime dependencies with fully pinned version numbers; created with `conda env export`; (approximately) a subset of those `dev-environment.yml`.
    - `requirements.yml`: Top-level runtime dependencies with only necessary version restrictions (typically a minimum version or a version range); kept manually.
- `src/my_first_blueprint_test/`: Source code of the project package.
- `tests/test_my_first_blueprint_test/`: Unit tests of the project package; run with `pytest`.
- `.gitignore`: Files and folders ignored by `git`.
- `.pre-commit-config.yaml`: Configuration of pre-commit hooks, which are formatters and checkers run before a successful commit.
- `AUTHORS.md`: Project authors.
- `CONTRIBUTING.md`: Instructions on how to contribute to the project.
- `HISTORY.md`: List of changes for each version of the project.
- `LICENSE`: License of the project.
- `MANIFEST.in`: Files installed alongside the source code.
- `pyproject.toml`: Main package specification file, including build dependencies, metadata and the configurations of development tools like `black`, `pytest`, `mypy` etc.
- `README.md`: Description of the project.
- `run-mypy.sh`: Run script for the static type checker `mypy`.
- `setup_env.sh`: Script to create new conda environments; see `setup_env.sh -h` for all available options.
- `setup_miniconda.sh`: Script to install miniconda.
- `test_all.sh`: Script to run all tests and checkers, including the pre-commit hooks and unit tests.
- `USAGE.md`: Information on how to use the package.

## Managing dependencies

my first blueprint test uses [Conda](https://docs.conda.io/en/latest/) to manage dependencies. (Also check out [Mamba](https://mamba.readthedocs.io/en/latest/) if you like your package installations fast.) Dependencies are specified in YAML files, of which there are four:

- `requirements/requirements.yml`: Top-level runtime dependencies with minimal version restrictions (typically a minimum version or a version range). It is kept manually.
- `requirements/dev-requirements.yml`: Additional top-level development dependencies with minimal version restrictions; also kept manually.
- `requirements/environment.yml`: Full tree of runtime dependencies with fully specified ('pinned') version numbers. It is created with `conda env export`.
- `requirements/dev-environment.yml`: Full tree of runtime and development dependencies with fully specified version numbers; also created with `conda env export`. The dependencies are an (approximate) superset of those in `environment.yml`.

Typically, the pinned `*environment.yml` files should be used to create reproducible environments for development or deployment. This ensures reproducible results across machines and users. The unpinned `*requirements.yml` files have two main purposes: (i) keeping track of the top-level dependencies, and (ii) periodically updating the pinned `*environment.yml` files to the latest package versions.

Updating the environment files involves the following steps:

```bash
conda env create --name my_env --file requirements/requirements.yml
conda env export --name my_env --no-builds > requirements/environment.yml
conda env update --name my_env --file requirements/dev-requirements.yml
conda env export --name my_env --no-builds > requirements/dev-environment.yml
```

Alternatively, use the provided script

```bash
setup_env.sh -u -d -e
```

to create a runtime and a development (`-d`) environment from unpinned (`-u`) dependencies and export (`-e`) them (consider throwing in `-m` for good measure to speed things up with `mamba`).

## How to provide executable scripts

By default, a single executable script called my-first-blueprint-test is provided. It is created when the package is installed. When you call it, the main function (`cli`) in `src/my_first_blueprint_test/cli.py` is called.

When the package is installed, a executable script named `my-first-blueprint-test` is created in the bin folder of the active conda environment. Upon calling this script in the shell, the `main` function in `src/my_first_blueprint_test/cli.py` is executed.

The scripts, their names and entry points are specified in `pyproject.toml` in the `[project.scripts]` section. Just add additional entries to provide more scripts to the users of your package.
