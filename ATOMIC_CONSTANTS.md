# Atomic constants for the U–Cl DFTB3 parameter set

All values in atomic units (Hartree). These are the constants needed to run
the U–Cl Slater–Koster files in this repository with DFTB+. They are the same
values as in Table 4 of the paper.

## Values stored in the Slater–Koster files (line 2 of the homonuclear SKF)

The onsite energies (ε), Hubbard parameters (U) and occupations (n) are read
by DFTB+ directly from `U-U.skf` and `Cl-Cl.skf`. They are listed here for
reference only and do not need to be set in the input.

| Element | Shell | ε (Ha)  | U (Ha) | n |
|---------|-------|---------|--------|---|
| U       | 7s    | -0.1547 | 0.1734 | 2 |
| U       | 6p    | -0.8533 | 0.2987 | 6 |
| U       | 6d    | -0.0861 | 0.2062 | 1 |
| U       | 5f    | -0.1266 | 0.3398 | 3 |
| Cl      | 3s    | -0.7544 | 0.4115 | 2 |
| Cl      | 3p    | -0.3164 | 0.3669 | 5 |
| Cl      | 3d    |  0.0220 | 0.3669 | 0 |

The U SKF uses the extended format for f electrons.

## Values that must be set in the DFTB+ input

### Hubbard derivatives (DFTB3, `ThirdOrderFull = Yes`)

The Hubbard parameters are shell-resolved (`ShellResolvedSCC = Yes`). The
Hubbard derivative is one value per element.

| Element | U^d (Ha)  | Source |
|---------|-----------|--------|
| U       | -0.04790  | computed for the 5f shell in this work, used for all U shells |
| Cl      | -0.06970  | 3OB parameter set |

### Spin–orbit coupling constants (optional)

These were **not** used for any result in the paper. Tests on UCl6 showed a
negligible effect on the geometry. They are given for users who want to
include SOC.

| Element | ξ_p (Ha) | ξ_d (Ha) | ξ_f (Ha) |
|---------|----------|----------|----------|
| U       | 0.0      | 0.0077   | 0.07313  |
| Cl      | 0.00430  | —        | —        |

Cite this article in case the SOC parameters are used:

Gautam Jha, Thomas Heine; DFTB Parameters for the Periodic Table: Part III, Spin-Orbit Coupling. J. Chem. Theory Comput. 12 July 2022; 18 (7): 4472–4481. https://doi.org/10.1021/acs.jctc.2c00376

### Spin constants

Spin polarization was not used in this work, and no spin constants are provided.

## Example DFTB+ input

See `dftb_in.hsd`.
