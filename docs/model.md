---
hide:
    - navigation
---

# Model Reference

This page provides comprehensive information about the structure and components of the data model, including detailed descriptions of the types and their properties, information on enumerations, and an overview of the ontologies used and their associated prefixes. Below, you will find a graph that visually represents the overall structure of the data model.

??? quote "Graph"
    ``` mermaid
    flowchart TB
        enzymemldocument(EnzymeMLDocument) --> creator(Creator)
        enzymemldocument(EnzymeMLDocument) --> vessel(Vessel)
        enzymemldocument(EnzymeMLDocument) --> protein(Protein)
        enzymemldocument(EnzymeMLDocument) --> complex(Complex)
        enzymemldocument(EnzymeMLDocument) --> reactant(Reactant)
        enzymemldocument(EnzymeMLDocument) --> reaction(Reaction)
        enzymemldocument(EnzymeMLDocument) --> reactionconditions(ReactionConditions)
        enzymemldocument(EnzymeMLDocument) --> measurement(Measurement)
        enzymemldocument(EnzymeMLDocument) --> kineticmodel(KineticModel)
        reaction(Reaction) --> reactionspecies(ReactionSpecies)
        kineticmodel(KineticModel) --> ratelaw(RateLaw)
        kineticmodel(KineticModel) --> kineticparameter(KineticParameter)
        measurement(Measurement) --> measurementdata(MeasurementData)
        measurementdata(MeasurementData) --> datatypes(DataTypes)
    
        click enzymemldocument "#enzymemldocument" "Go to EnzymeMLDocument"
        click creator "#creator" "Go to Creator"
        click vessel "#vessel" "Go to Vessel"
        click protein "#protein" "Go to Protein"
        click complex "#complex" "Go to Complex"
        click reactant "#reactant" "Go to Reactant"
        click reaction "#reaction" "Go to Reaction"
        click reactionspecies "#reactionspecies" "Go to ReactionSpecies"
        click reactionconditions "#reactionconditions" "Go to ReactionConditions"
        click kineticmodel "#kineticmodel" "Go to KineticModel"
        click ratelaw "#ratelaw" "Go to RateLaw"
        click kineticparameter "#kineticparameter" "Go to KineticParameter"
        click measurement "#measurement" "Go to Measurement"
        click measurementdata "#measurementdata" "Go to MeasurementData"
        click datatypes "#datatypes" "Go to DataTypes"
    ```


## Ontologies
- [schema](https://schema.org/)
- [OBO](http://purl.obolibrary.org/obo/)


## Types


### EnzymeMLDocument
This is the root object that composes all objects found in an EnzymeML document. It also includes general metadata such as the name of the document, when it was created/modified and references to publications, databases and arbitrary links to the web.

__name__* `string`

- Title of the EnzymeML Document.

__references__ `list[string]`

- Contains references to publications, databases and arbitrary links to the web.

__created__ `string`

- string the EnzymeML document was created.

__modified__ `string`

- string the EnzymeML document was modified.

__creators__ [`list[Creator]`](#creator)

- Contains all authors that are part of the experiment.

__vessels__ [`list[Vessel]`](#vessel)

- Contains all vessels that are part of the experiment.

__proteins__ [`list[Protein]`](#protein)

- Contains all proteins that are part of the experiment.

__complexes__ [`list[Complex]`](#complex)

- Contains all complexes that are part of the experiment.

__reactants__ [`list[Reactant]`](#reactant)

- Contains all reactants that are part of the experiment.

__reactions__ [`list[Reaction]`](#reaction)

- Dictionary mapping from reaction IDs to reaction describing objects.

__conditions__ [`ReactionConditions`](#reactionconditions)

- Conditions under which the reaction was carried out.

__measurements__ [`list[Measurement]`](#measurement)

- Contains measurements that describe outcomes of an experiment.

__kinetic_model__ [`KineticModel`](#kineticmodel)

- Contains the kinetic model of the experiment.

------

### Creator
The creator object contains all information about authors that contributed to the resulting document.

__given_name__* `string`

- Given name of the author or contributor.

__family_name__* `string`

- Family name of the author or contributor.

__mail__* `string`

- Email address of the author or contributor.

------

### Vessel
This object describes vessels in which the experiment has been carried out. These can include any type of vessel used in biocatalytic experiments.

__name__* `string`

- Name of the used vessel.

__volume__* `float`

- Volumetric value of the vessel.
- `Template_alias`: Volume value

__string__* `string`

- Volumetric string of the vessel.

__constant__* `boolean`

- Whether the volume of the vessel is constant or not.

__creator_id__ `string`

- Unique string of the author.

------

### Protein
This objects describes the proteins that were used or formed over the course of the experiment.

__name__* `string`


__constant__* `boolean`

- `Default`: False

__sequence__* `string`

- Amino acid sequence of the protein

__vessel_id__ `string`


__ecnumber__ `string`

- EC number of the protein.

__organism__ `string`

- Organism the protein was expressed in.

__organism_tax_id__ `string`

- Taxonomy string of the expression host.

__references__ `list[string]`

- Array of references to publications, database entries etc. that describe the protein.

------

### Complex
This object describes complexes made of reactants and/or proteins that were used or produced in the course of the experiment.

__participants__ `list[string]`

- Array of IDs the complex contains 

------

### Reactant
This objects describes the reactants that were used or produced in the course of the experiment.

__name__* `string`


__constant__* `boolean`

- `Default`: False

__vessel_id__ `string`


__canonical_smiles__ `string`

- Canonical Simplified Molecular-Input Line-Entry System (SMILES) encoding of the reactant.

__inchikey__ `string`

- Hashed International Chemical string (InChIKey) encoding of the reactant.

__references__ `list[string]`

- Array of references to publications, database entries etc. that describe the reactant.

------

### Reaction
This object describes a chemical or enzymatic reaction that was investigated in the course of the experiment. All species used within this object need to be part of the data model.

__name__* `string`

- Name of the reaction.

__reversible__* `boolean`

- Whether the reaction is reversible or irreversible
- `Default`: False

__species__ [`list[ReactionSpecies]`](#reactionspecies)

- List of reaction elements that are part of the reaction.

__modifiers__ `list[string]`

- List of reaction elements that are not part of the reaction but influence it.

------

### ReactionSpecies
This object is part of the Reaction object and describes either an educt, product or modifier. The latter includes buffers, counter-ions as well as proteins/enzymes.

__species_id__* `string`

- Internal string to either a protein or reactant defined in the EnzymeMLDocument.

__stoichiometry__ `float`

- Float number representing the associated stoichiometry.

------

### ReactionConditions


__temperature__ `float`

- Numeric value of the temperature of the reaction.

__temperature_string__ `string`

- string of the temperature of the reaction.

__ph__ `float`

- PH value of the reaction.

------

### KineticModel
This object describes a kinetic model that was derived from the experiment.

__name__* `string`

- Name of the kinetic law.

__strings__* [`list[RateLaw]`](#ratelaw)

- string for the kinetic law.

__parameters__ [`list[KineticParameter]`](#kineticparameter)

- List of estimated parameters.

------

### RateLaw
This object describes an ordinary differential string that is part of the kinetic model.

__species_id__* `string`

- Internal string to a species defined in the EnzymeMLDocument.

__string__* `string`

- string of the rate law.

------

### KineticParameter
This object describes the parameters of the kinetic model and can include all estimated values.

__name__* `string`

- Name of the estimated parameter.

__value__* `float`

- Numerical value of the estimated parameter.

__string__* `string`

- string of the estimated parameter.

__constant__* `boolean`

- Specifies if this parameter is constant

__initial_value__ `float`

- Initial value that was used for the parameter estimation.

__upper__ `float`

- Upper bound of the estimated parameter.

__lower__ `float`

- Lower bound of the estimated parameter.

__stderr__ `float`

- Standard error of the estimated parameter.

------

### Measurement
This object describes the result of a measurement, which includes time course data of any type defined in DataTypes. It includes initial concentrations of all species used in a single measurement.

__name__* `string`

- Name of the measurement

__species__ [`list[MeasurementData]`](#measurementdata)

- Species of the measurement.

__group_id__ `string`

- User-defined group ID to signalize relationships between measurements.

------

### MeasurementData
This object describes a single entity of a measurement, which corresponds to one species. It also holds replicates which contain time course data.

__species_id__* `string`

- The string for the described reactant.

__init_conc__* `float`

- Initial concentration of the measurement data.

__data_type__* [`DataTypes`](#datatypes)

- Type of data that was measured (e.g. concentration)

__data_string__* `string`

- SI string of the data that was measured.

__time_string__* `string`

- Time string of the replicate.

__time__* `list[float]`

- Time steps of the replicate.

__data__* `list[float]`

- Data that was measured.

__is_calculated__* `boolean`

- Whether or not the data has been generated by simulation.
- `Default`: False



## Enumerations

### DataTypes

| Alias | Value |
|-------|-------|
| `ABSORPTION` | abs |
| `BIOMASS` | biomass |
| `CONCENTRATION` | conc |
| `CONVERSION` | conversion |
| `FEED` | feed |
| `PEAK_AREA` | peak-area |
