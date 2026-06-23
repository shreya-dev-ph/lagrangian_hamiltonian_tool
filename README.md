# lagrangian_hamiltonian_tool
calculates lagrangian and hamiltonian in generalized coordinates

##Lagrangian Hamiltonian Solver

A Python command-line tool for symbolic calculations in analytical mechanics.
This package can derive:

* the Lagrangian from kinetic and potential energy
* conjugate momentum
* the Hamiltonian
* Lagrange's equation of motion
* symbolic solutions using SymPy

The package is mainly intended for simple symbolic mechanics problems written in generalized coordinates.

## Installation

Clone the repository and install the package locally:

```bash
pip install -e .
```

## Usage

The command-line tool accepts generalized coordinates, constants, and either:

1. kinetic and potential energy expressions, or
2. a direct Lagrangian expression.

### Using kinetic and potential energy

```bash
lagrangian-solver "x" "m,k" energies "0.5*m*x_dot**2" "0.5*k*x**2"
```

Here:

* `"x"` is the generalized coordinate
* `"m,k"` are constants
* `"0.5*m*x_dot**2"` is the kinetic energy
* `"0.5*k*x**2"` is the potential energy

The tool prints the Lagrangian, Hamiltonian, and Lagrange equation.

### Using a direct Lagrangian

```bash
lagrangian_hamiltonian_solver "x" "m,k" lagrangian "0.5*m*x_dot**2 - 0.5*k*x**2"
```

The tool prints the Hamiltonian and Lagrange equation.

## Notation

Coordinates are entered as ordinary names such as:

```text
x
theta
r
```

The package internally treats them as time-dependent generalized coordinates:

```text
x(t)
theta(t)
r(t)
```

Time derivatives are written using `_dot`, `_ddot`, etc.

Examples:

```text
x_dot      → dx/dt
x_ddot     → d²x/dt²
theta_dot  → dθ/dt
```

## Example

For a one-dimensional harmonic oscillator:

```bash
lagrangian_hamiltonian_solver "x" "m,k" energies "0.5*m*x_dot**2" "0.5*k*x**2"
```

The Lagrangian is:

```text
0.5*m*x_dot**2 - 0.5*k*x**2
```

The corresponding equation of motion is equivalent to:

```text
m*x_ddot + k*x = 0
```

## Dependencies

This package uses:

* SymPy
* NumPy

Install dependencies with:

```bash
pip install sympy numpy
```

If the package is installed using `pip install -e .`, dependencies listed in `pyproject.toml` should be installed automatically.

## Project Structure

```text
lagrangian_hamiltonian_tool/
├── pyproject.toml
├── README.md
├── LICENSE
└── src/
    └── lagrangian_hamiltonian_solver/
        ├── __init__.py
        ├── core.py
        └── cli.py
```

## License

This project is licensed under the MIT License.

