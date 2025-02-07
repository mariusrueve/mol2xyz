# mol2xyz

**mol2xyz** is a Python library and command‐line tool that converts molecular data from SDF files or SMILES strings into the XYZ file format. It uses [RDKit](https://www.rdkit.org/) to generate and optimize 3D molecular structures, ensuring that a valid 3D conformation is produced when needed.

## Installation

### Installing Dependencies

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Usage

### Command-Line Interface (CLI)

Ensure the main script is executable. You might need to set the execute permission:

```bash
chmod +x mol2xyz.py
```

Run the tool directly from the command line:

- Converting an SDF file with 3D coordinates to XYZ:

```bash
./mol2xyz.py molecule.sdf output.xyz
```

- Converting a SMILES string to an XYZ file (with automatic 3D structure generation):

```bash
./mol2xyz.py "CCO" output.xyz --smiles
```

### Using as a Python Library

Import the functionality into your own Python scripts:

```bash
from mol2xyz import molecule_from_smiles, molecule_from_sdf, ensure_3d, write_xyz

# Converting a SMILES string:
mol = molecule_from_smiles("CCO")
write_xyz(mol, "output.xyz")

# Converting an SDF file:
mol = molecule_from_sdf("molecule.sdf")
mol = ensure_3d(mol)  # Generate a 3D conformer if not present
write_xyz(mol, "output.xyz")
```
