# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]
### Added
- New `transform` parameter that accepts a dictionnary of field-function items where each
  function transforms the input value that will be displayed. Fixes: Issue #10

## [0.0.4] - 2021/04/01
### Changed
- The demo notebook can now be run on Google Colab
### Fixed
- DataFrames with `NaN` values would previously lead to an **empty grid** as `NaN` were
  converted to `nan` (not recognized by JS) instead of `NaN`.
- Selection of molecules in Google Colab now works as expected.
- Saved documents are now displayed properly

## [0.0.3] - 2021/03/31
### Added
- **SMARTS search**: the "🔎" button now lets users choose between a text search or a SMARTS
  search. This relies on RDKit's "MinimalLib" JS wrapper which is still in beta, and will
  likely break at some point. Use at your own risk!
- **Sorting**: added a "Sort by" button that lets users choose in which order the molecules
  should be listed. Default: by index. Fixes: Issue #7
- `MolDrawOptions` **drawing** parameter: this will allow further customization of the drawing
  options.
- **Selection**: added checkboxes to each cell. Clicking on a checkbox will add the molecule's
  corresponding index and SMILES to the `mols2grid.selection` dictionnary.
- New **input** formats: dict and record (list of dicts) are automatically converted to a
  pandas DataFrame when used as input to the MolGrid class. The `mols2grid.display`
  function only accepts the dict option (since the list format is already used for lists
  of RDKit molecules).
- New **input** options: `mol_col` parameter. Adds the ability to directly use an RDKit mol
  instead of relying on a SMILES intermediate. This makes using the 2D coordinates of the
  input mol a possibility, instead of systematically generating new ones. It also allows
  for adding annotations and highlights on drawings. Introduces 2 new parameters:
  - `mol_col=None`: Column of the dataframe containing RDKit molecules
  - `use_coords=True`: directly use the coordinates from each molecule, or generate new
    ones
### Changed
- The "mols2grid-id" now keeps track of molecules that could not be read by RDKit. This
  makes relying on the index of the corresponding entry more reliable.
### Fixed
- The "mols2grid-id" field is now correctly set in the internal `DataFrame` and the
  JavaScript `List`.
- Using the search bar will now only search inside the fields listed in `subset` and
  `tooltip` and exclude the `img` field.
- When using the `display` function, the `height` of the iframe is now automatically set
  based on the different parameters, instead of a fixed 600px height. Fixes: Issue #6

## [0.0.2] - 2021/03/23
- First release