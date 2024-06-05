# EnzymeML


### EnzymeMLDocument

- <details>
  <summary>name</summary>

  - Type: string
  - Term: schema:name
  - description: Title of the EnzymeML Document.

  </details>
- <details>
  <summary>references</summary>

  - Type: string
  - description: Contains references to publications, databases and arbitrary links to the web.

  </details>
- <details>
  <summary>created</summary>

  - Type: string
  - description: string the EnzymeML document was created.

  </details>
- <details>
  <summary>modified</summary>

  - Type: string
  - description: string the EnzymeML document was modified.

  </details>
- <details>
  <summary>creators</summary>

  - Type: Creator
  - description: Contains all authors that are part of the experiment.

  </details>
- <details>
  <summary>vessels</summary>

  - Type: Vessel
  - description: Contains all vessels that are part of the experiment.

  </details>
- <details>
  <summary>proteins</summary>

  - Type: Protein
  - description: Contains all proteins that are part of the experiment.

  </details>
- <details>
  <summary>complexes</summary>

  - Type: Complex
  - description: Contains all complexes that are part of the experiment.

  </details>
- <details>
  <summary>reactants</summary>

  - Type: Reactant
  - description: Contains all reactants that are part of the experiment.

  </details>
- <details>
  <summary>reactions</summary>

  - Type: Reaction
  - description: Dictionary mapping from reaction IDs to reaction describing objects.

  </details>
- <details>
  <summary>conditions</summary>

  - Type: ReactionConditions
  - description: Conditions under which the reaction was carried out.

  </details>
- <details>
  <summary>measurements</summary>

  - Type: Measurement
  - description: Contains measurements that describe outcomes of an experiment.

  </details>
- <details>
  <summary>kinetic_model</summary>

  - Type: KineticModel
  - description: Contains the kinetic model of the experiment.

  </details>

### Creator

- <details>
  <summary>given_name</summary>

  - Type: string
  - Term: schema:givenName
  - description: Given name of the author or contributor.

  </details>
- <details>
  <summary>family_name</summary>

  - Type: string
  - Term: schema:familyName
  - description: Family name of the author or contributor.

  </details>
- <details>
  <summary>mail</summary>

  - Type: string
  - Term: schema:email
  - description: Email address of the author or contributor.

  </details>

### Vessel

- <details>
  <summary>name</summary>

  - Type: string
  - Term: schema:name
  - description: Name of the used vessel.

  </details>
- <details>
  <summary>volume</summary>

  - Type: float
  - Term: OBO:OBI_0002139
  - description: Volumetric value of the vessel.
  - template_alias: Volume value

  </details>
- <details>
  <summary>string</summary>

  - Type: string
  - description: Volumetric string of the vessel.

  </details>
- <details>
  <summary>constant</summary>

  - Type: boolean
  - description: Whether the volume of the vessel is constant or not.

  </details>
- <details>
  <summary>creator_id</summary>

  - Type: string
  - Term: schema:string
  - description: Unique string of the author.

  </details>

### Protein

- <details>
  <summary>name</summary>

  - Type: string
  - Term: schema:name

  </details>
- <details>
  <summary>constant</summary>

  - Type: boolean
  - default: False

  </details>
- <details>
  <summary>sequence</summary>

  - Type: string
  - Term: OBO:GSSO_007262
  - description: Amino acid sequence of the protein

  </details>
- <details>
  <summary>vessel_id</summary>

  - Type: string
  - Term: schema:string

  </details>
- <details>
  <summary>ecnumber</summary>

  - Type: string
  - description: EC number of the protein.

  </details>
- <details>
  <summary>organism</summary>

  - Type: string
  - Term: OBO:OBI_0100026
  - description: Organism the protein was expressed in.

  </details>
- <details>
  <summary>organism_tax_id</summary>

  - Type: string
  - description: Taxonomy string of the expression host.

  </details>
- <details>
  <summary>references</summary>

  - Type: string
  - description: Array of references to publications, database entries etc. that describe the protein.

  </details>

### Complex

- <details>
  <summary>participants</summary>

  - Type: string
  - description: Array of IDs the complex contains

  </details>

### Reactant

- <details>
  <summary>name</summary>

  - Type: string
  - Term: schema:name

  </details>
- <details>
  <summary>constant</summary>

  - Type: boolean
  - default: False

  </details>
- <details>
  <summary>vessel_id</summary>

  - Type: string
  - Term: schema:string

  </details>
- <details>
  <summary>canonical_smiles</summary>

  - Type: string
  - description: Canonical Simplified Molecular-Input Line-Entry System (SMILES) encoding of the reactant.

  </details>
- <details>
  <summary>inchikey</summary>

  - Type: string
  - description: Hashed International Chemical string (InChIKey) encoding of the reactant.

  </details>
- <details>
  <summary>references</summary>

  - Type: string
  - description: Array of references to publications, database entries etc. that describe the reactant.

  </details>

### Reaction

- <details>
  <summary>name</summary>

  - Type: string
  - description: Name of the reaction.

  </details>
- <details>
  <summary>reversible</summary>

  - Type: boolean
  - description: Whether the reaction is reversible or irreversible
  - default: False

  </details>
- <details>
  <summary>species</summary>

  - Type: ReactionSpecies
  - description: List of reaction elements that are part of the reaction.

  </details>
- <details>
  <summary>modifiers</summary>

  - Type: string
  - description: List of reaction elements that are not part of the reaction but influence it.

  </details>

### ReactionSpecies

- <details>
  <summary>species_id</summary>

  - Type: string
  - description: Internal string to either a protein or reactant defined in the EnzymeMLDocument.

  </details>
- <details>
  <summary>stoichiometry</summary>

  - Type: float
  - description: Float number representing the associated stoichiometry.

  </details>

### ReactionConditions

- <details>
  <summary>temperature</summary>

  - Type: float
  - description: Numeric value of the temperature of the reaction.

  </details>
- <details>
  <summary>temperature_string</summary>

  - Type: string
  - description: string of the temperature of the reaction.

  </details>
- <details>
  <summary>ph</summary>

  - Type: float
  - description: PH value of the reaction.

  </details>

### KineticModel

- <details>
  <summary>name</summary>

  - Type: string
  - description: Name of the kinetic law.

  </details>
- <details>
  <summary>strings</summary>

  - Type: RateLaw
  - description: string for the kinetic law.

  </details>
- <details>
  <summary>parameters</summary>

  - Type: KineticParameter
  - description: List of estimated parameters.

  </details>

### RateLaw

- <details>
  <summary>species_id</summary>

  - Type: string
  - description: Internal string to a species defined in the EnzymeMLDocument.

  </details>
- <details>
  <summary>string</summary>

  - Type: string
  - description: string of the rate law.

  </details>

### KineticParameter

- <details>
  <summary>name</summary>

  - Type: string
  - description: Name of the estimated parameter.

  </details>
- <details>
  <summary>value</summary>

  - Type: float
  - description: Numerical value of the estimated parameter.

  </details>
- <details>
  <summary>string</summary>

  - Type: string
  - description: string of the estimated parameter.

  </details>
- <details>
  <summary>constant</summary>

  - Type: boolean
  - description: Specifies if this parameter is constant

  </details>
- <details>
  <summary>initial_value</summary>

  - Type: float
  - description: Initial value that was used for the parameter estimation.

  </details>
- <details>
  <summary>upper</summary>

  - Type: float
  - description: Upper bound of the estimated parameter.

  </details>
- <details>
  <summary>lower</summary>

  - Type: float
  - description: Lower bound of the estimated parameter.

  </details>
- <details>
  <summary>stderr</summary>

  - Type: float
  - description: Standard error of the estimated parameter.

  </details>

### Measurement

- <details>
  <summary>name</summary>

  - Type: string
  - description: Name of the measurement

  </details>
- <details>
  <summary>species</summary>

  - Type: MeasurementData
  - description: Species of the measurement.

  </details>
- <details>
  <summary>group_id</summary>

  - Type: string
  - description: User-defined group ID to signalize relationships between measurements.

  </details>

### MeasurementData

- <details>
  <summary>species_id</summary>

  - Type: string
  - description: The string for the described reactant.

  </details>
- <details>
  <summary>init_conc</summary>

  - Type: float
  - description: Initial concentration of the measurement data.

  </details>
- <details>
  <summary>data_type</summary>

  - Type: DataTypes
  - description: Type of data that was measured (e.g. concentration)

  </details>
- <details>
  <summary>data_string</summary>

  - Type: string
  - description: SI string of the data that was measured.

  </details>
- <details>
  <summary>time_string</summary>

  - Type: string
  - description: Time string of the replicate.

  </details>
- <details>
  <summary>time</summary>

  - Type: float
  - description: Time steps of the replicate.

  </details>
- <details>
  <summary>data</summary>

  - Type: float
  - description: Data that was measured.

  </details>
- <details>
  <summary>is_calculated</summary>

  - Type: boolean
  - description: Whether or not the data has been generated by simulation.
  - default: False

  </details>

## Enumerations

### DataTypes

```
ABSORPTION = abs
BIOMASS = biomass
CONCENTRATION = conc
CONVERSION = conversion
FEED = feed
PEAK_AREA = peak-area
```