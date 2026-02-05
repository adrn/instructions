---
applyTo: "**/*.{py,ipynb}"
description: This file describes my Python preferences.
---

# Python Package Management and Project Execution with uv

Use uv for Python package management in this project. Also use uv to run Python code and manage scripts, run tests, etc.

## Package Management Commands

- All Python dependencies should be installed, synchronized, and locked using uv

Use these commands:

- Install dependencies: `uv add <package>`
- Remove dependencies: `uv remove <package>`
- Sync dependencies: `uv sync`

Put all dependencies in `pyproject.toml` under the `[tool.uv.dependencies]` section, and additional dependencies should be added under dependency groups as needed.
For example, dependencies needed for testing (pytest, etc.) should go in a "test" group, documentation dependencies in a "docs" group, development dependencies in a "dev" group (such as pre-commit, ruff, etc.).

## Running Python Code

- Run a Python script with `uv run <script-name>.py`
- Run Python tools like Pytest with `uv run pytest` or `uv run ruff`
- Launch a Python repl with `uv run python`

## Jupyter Notebooks

These Python coding guidelines also apply when working with Jupyter notebooks (`.ipynb` files).

### Running Notebooks

- Use the integrated notebook execution tools in VS Code rather than terminal commands
- Execute cells directly in the notebook editor
- Notebooks automatically use the configured Python environment

### Package Management in Notebooks

- Install packages in notebooks using `uv add <package>` in the terminal, not `!pip install` in cells
- After adding packages with `uv add`, use `uv sync` to ensure environment consistency
- The notebook kernel will have access to packages installed via `uv`
- Make sure ipykernel is installed in the environment for Jupyter support: `uv add ipykernel`

### Code Style in Notebooks

All code style guidelines apply to notebook cells:

- **Type hints**: Include type hints in function definitions within reason. Most notebooks are written for exploration, so prioritize clarity.
- **Immutability**: Don't mutate input parameters
- **jaxtyping**: Use for arrays and PyTrees in data science workflows

### Notebook Organization

- **Markdown cells**: Use for explanations, context, and section headers
- **Code cells**: Keep focused and modular - prefer small, testable functions
- **Outputs**: Clear outputs before committing if they contain sensitive data or are large
- If you add cells for testing or experiments, keep track of them so that we can clean up later.

### Example Notebook Cell:

```python
from jaxtyping import Array, Float
import jax.numpy as jnp

def normalize_data(
    data: Float[Array, "batch features"],
    epsilon: float = 1e-8
) -> Float[Array, "batch features"]:
    """Normalize data to zero mean and unit variance.

    Args:
        data: Input data array
        epsilon: Small value for numerical stability

    Returns:
        Normalized data array
    """
    mean = jnp.mean(data, axis=0)
    std = jnp.std(data, axis=0)
    return (data - mean) / (std + epsilon)
```

## Core Development Principles

### Truthfulness Framework

#### What You MUST Do:

- Use file system tools to verify file existence before claiming they exist
- Copy exact code snippets from files, never paraphrase or recreate from memory
- Run commands to check actual state (`uv sync`, `git status`, etc.)
- Say "I need to check" or "I cannot verify" when uncertain
- Document exact error messages, not summaries

#### What You MUST NOT Do:

- Write "the file probably contains" or "it should have"
- Create example code that "would work" without testing
- Assume file locations or function names exist
- Hide, avoid, or bypass failures or errors
- Continue when core requirements are unclear (instead, use escalation examples below)

### Escalation Examples:

- "I found 3 different implementations and need guidance on which to modify"
- "The tests are failing with this specific error: [exact error]"
- "I cannot find the file mentioned in the requirements"
- "Two approaches are possible, and I need a decision on direction"

## Python Environment Management

Always use `uv` for environment management and commands.

### UV Commands

```sh
# Install dependencies
uv sync

# Add new dependencies
uv add package_name
uv add --dev package_name  # for development dependencies

# Run Python commands
uv run python script.py
uv run pytest  # for tests

# Quality checks
uv run pre-commit  # linting, formatting, typing
uv run ty check    # type checking with ty
```

### Never Use Bare Python

- **Always use `uv run python`** instead of just `python`
- **Always use `uv add`** instead of `pip install`
- **At the start, use `uv sync`** to ensure environment consistency

### Project Configuration Files

Each project should use these configuration files (refer to them for current settings):

- **`pyproject.toml`**: Main project configuration, dependencies, tool settings
- **`.pre-commit-config.yaml`**: Pre-commit hooks configuration
- **`.python-version`**: Python version specification
  If these files are absent, escalate.

## Type Checking with `ty` and `jaxtyping`

### Array and PyTree Typing with jaxtyping

Use `jaxtyping` for type annotation of JAX (and PyTorch, NumPy, MLX, and TensorFlow) arrays and PyTrees.

```python
from jaxtyping import Array, Float, PyTree

# Accepts floating-point 2D arrays with matching axes
# You can replace `Array` with `torch.Tensor` etc.
def matrix_multiply(x: Float[Array, "dim1 dim2"],
                    y: Float[Array, "dim2 dim3"]
                  ) -> Float[Array, "dim1 dim3"]:
    ...

def accepts_pytree_of_ints(x: PyTree[int]):
    ...

def accepts_pytree_of_arrays(x: PyTree[Float[Array, "batch c1 c2"]]):
    ...
```

## Code Style Guidelines

### Function Naming Conventions

- **Boolean functions**: Use prefixes `is_`, `can_`, `has_`, `should_`
  ```python
  def is_enabled(feature: dict) -> bool:
  def can_show_feature(user: User) -> bool:
  def has_permission(user: User, resource: str) -> bool:
  ```
- **Avoid**: Verb prefixes for booleans (e.g., `calculate_show_feature` when returning boolean)

### Function Parameters

- **Type hints required**: Always include type hints for parameters and return values
- **Use jaxtyping for arrays**: For JAX arrays, PyTrees, and numerical data
- **Example**:

  ```python
  from typing import TypedDict
  from jaxtyping import Array, Float, PyTree
  import jax.numpy as jnp

  # Good - jaxtyping for numerical arrays
  def process_matrix(
      data: Float[Array, "batch height width channels"],
      weights: Float[Array, "in_features out_features"]
  ) -> Float[Array, "batch out_features"]:
      pass

  # Good - PyTree typing for complex nested structures
  def update_model_params(
      params: PyTree[Float[Array, "..."]],
      gradients: PyTree[Float[Array, "..."]]
  ) -> PyTree[Float[Array, "..."]]:
      pass
  ```

### Function Immutability

- **Never mutate input parameters** - Functions should not modify their input arguments
- **Return new objects** - Create new dictionaries, lists, or objects
- **Pure functions preferred** - Functions should return new data without side effects
- **Example**:

  ```python
  # Bad - mutates input parameter
  def update_config(config: dict) -> None:
      config["enabled"] = True  # Direct mutation

  # Good - returns new dict
  def update_config(config: dict) -> dict:
      return {
          **config,
          "enabled": True
      }

  # Even better - with type hints
  def update_config(config: Config) -> Config:
      return Config(**{**config.__dict__, "enabled": True})
  ```

## Code Organization Patterns

### Project Structure

```
src/
├── my_package/
│   ├── __init__.py
│   ├── core/
│   │   ├── __init__.py
│   │   ├── layers.py
│   │   └── optimizers.py
│   └── utils/
│       └── __init__.py
├── experiments/
│   ├── __init__.py
│   └── ...
├── LICENSE
├── pyproject.toml
└── README.md

tests/
├── __init__.py
├── conftest.py
├── unit/
│   ├── __init__.py
│   └── core/
│       ├── __init__.py
│       ├── test_layers.py
│       └── test_optimizers.py
├── integration/
│   ├── __init__.py
│   └── test_training_loop.py
└── regression/
    ├── __init__.py
    ├── test_pytorch_reference.py
    ├── test_sklearn_reference.py
    ├── test_numerical_stability.py
    └── fixtures/
        ├── __init__.py
        ├── reference_outputs.pkl
        └── test_data.npy
```

### Utility Function Placement

- **Bottom-up approach**: Place utilities as close to usage as possible
- **Module utilities**: If only used by one module → `src/my_package/module_name/utils.py`
- **Shared utilities**: If used across multiple modules → `src/my_package/utils/`
  - Organize by domain: `src/my_package/utils/validation.py`, `src/my_package/utils/formatting.py`

### Comments Policy

#### Core Principles

- **Self-documenting code first** - Use clear naming and structure
- **Comments must add value** - Explain WHY, not WHAT; omit otherwise
- **Docstrings for public functions** - Follow Google style

#### Example:

```python
# Bad - states the obvious
# Check if feature is enabled
if feature.enabled:
    pass

# Good - explains algorithm or non-obvious logic
def calculate_hash(data: bytes) -> str:
    """Calculate SHA-256 hash with salt for security.

    Uses double hashing to prevent rainbow table attacks.
    """
    salt = os.urandom(16)
    # First hash with salt to prevent rainbow tables
    first_hash = hashlib.sha256(salt + data).digest()
    return hashlib.sha256(first_hash).hexdigest()
```

## Testing Guidelines

### Test Structure

- **All tests in `tests/` directory**
- **Use pytest fixtures** for common setup within a test module
- **Use hypothesis** to parameterize tests
- **Write common test utilities** if setup is shared across test modules

### Test Commands

```sh
# Run all tests
uv run pytest

# Run specific test file
uv run pytest tests/unit/test_auth.py

# Run with coverage
uv run pytest --cov=src

# Run tests matching pattern
uv run pytest -k "test_login"
```

### Quality Checks

Always run after making code changes:

```sh
# All checks (formatting, linting, type checking)
uv run pre-commit

# Individual checks may be more efficient (if needed)
# Check .pre-commit-config.yaml for what is configured
uv run ty check         # example: type checking with ty
```

## Session Handover Template

When switching contexts or reaching limits:

1. **Current state**: What was accomplished
2. **Files modified**: Exact paths with brief description
3. **Commands run**: `uv sync`, `uv run pytest`, etc.
4. **Blockers**: Any decisions needed or errors encountered
5. **Next steps**: What should happen next
   Omit any of the above if not applicable.

Example:

```
## Session Summary
- Modified: `src/my_package/auth.py` (added login validation)
- Added: `tests/unit/test_auth.py` (login validation tests)
- Commands run: `uv sync`, `uv run pytest`, `uv run pre-commit`
- Status: All tests passing, pre-commit checks passed
- Next: Need decision on password complexity requirements
```