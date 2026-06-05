# _Klebsiella oxytoca_ Species Complex surface polysaccharide locus databases

[![Database CI/CD Pipeline](https://github.com/klebgenomics/KoSC-surface-antigen-loci/actions/workflows/release.yml/badge.svg)](https://github.com/klebgenomics/KoSC-surface-antigen-loci/actions/workflows/release.yml)

This repository houses databases for _in silico_ typing of _K. oxytoca_ Species Complex (KoSC) and _Klebsiella indica_ K and O surface polysaccharides using [Kaptive](https://github.com/klebgenomics/Kaptive). The capsule polysaccharide (K) and outer-lipopolysaccharide (O) are major surface antigens and phage binding receptors, making them key targets for novel vaccines, monoclonal antibody and phage therapies targeting KoSC.

> [!WARNING]
> These databases should not be used for species outside of the KoSC and _K. indica_! Using the databases to type other organisms, including other _Klebsiella_ species, may result in errors and low typing rates. 

> [!TIP] 
> K and O locus databases for the _Klebsiella pneumoniae_ Species Complex are available [here](https://github.com/klebgenomics/KpSC-surface-antigen-loci).

## Contents
- [What is the _K. oxytoca_ Species Complex?](#what-is-the-k-oxytoca-species-complex)
- [Database formats and versions](#database-formats-and-versions)
  - [How are loci defined?](#how-are-loci-defined)
  - [K locus database](#k-locus-database)
  - [O locus database](#o-locus-database)   
- [Citations](#citations)
- [Curators](#curators)
- [Contribute](#contribute)
- [License](#license)

## What is the _K. oxytoca_ Species Complex?

The _K. oxytoca_ Species Complex (KoSC) comprises _K. oxytoca_ and closely related organisms that cannot be accurately distinguished by standard biochemical or mass-spectometry-based identification protocols (shown in red in the phylogeny below): 
* _Klebsiella oxytoca_
* _Klebsiella michiganensis_
* _Klebsiella grimontii_
* _Klebsiella pasteurii_
* _Klebsiella huaxiensis_
* _Klebsiella spallanzanii_
* _"Klebsiella mammalorium"_ (formal description in progress)
* plus two unnamed taxa 

The KoSC Kaptive databases also include loci from the closely related _K. indica_ (see phylogeny below) since this organism would otherwise not be captured by any available K and O databases. 

![Unrooted phylogeneny showing the relationships between Klebsiella species and other selected Enterobacteriales, with KoSC and K.indica marked](/images/Enterobacteriales_tree_KoSC.png)

## Database formats and versions

The K and O locus databases each comprise two files that are required to run Kaptive:
1. A multi-genbank file containing each unique locus sequence and its gene annotations.
2. A metadata file in TOML format, which provides essential information about the database (e.g. version, target organism(s), curator details), plus any special [phenotype logic](https://klebgenomics.github.io/Kaptive/Databases.html#phenotype-logic) that applies to the database.

Please see the [Kaptive docs](https://klebgenomics.github.io/Kaptive/Databases.html#format) for more details on the database file formats.

### How are loci defined?

Loci are defined by the rules of the [Kaptive typing framework](https://klebgenomics.github.io/Kaptive/Databases.html#what-is-a-locus), which states that **a unique locus should represent a unique set of genes**, with the assumption that this encodes a unique
polysaccharide structure. In many cases, these unique structures will
result in unique immunological serotypes. 

The gene translations (protein sequences) from each locus are compared
by pairwise alignment, and must fall under a defined percent identity
threshold to be considered 'unique'. Some genes (such as the core
assembly machinery) will be highly similar, however the genes
responsible for the polysaccharide structural diversity are expected to
be more variable. **The gene identity threshold for the 
KoSC databases is 82.5%.**


### K locus database

The K locus database comprises 88 distinct loci:

- KL1 corresponds to the K locus of strain K15g, for which the capsule polysaccharide structure was previously [described](), herein labeled K type K1. 
- K loci KL26, KL29, KL41, KL66, KL70 and KL74 correspond to the originally defined _Klebsiella_ serotype reference strains, KL26, KL29, KL41, KL66, KL70 and KL74, respectively. These strains have been broadly assumed as _K. pneumoniae_ but are now known to be members of the KoSC. WE therefore annotated those loci with the corresponding matched phenotypes.
- All other loci were defined from DNA sequence data on the basis of
  gene content, numbered arbitrarily. KL6 and KL11 are close orthologs of _K. pneumoniae_ Species Complex KL43 and KL102, respectively for which the polysaccharide structures have been determined, and we therefore annotated these loci with the matched structres. At the time of discovery, no other matched phenotypes were known.

> [!Note]
> Insertion sequences (IS) are excluded from this database since we assume that the ancestral sequence was likely IS-free and IS transposase genes are not specific to the K locus.
> Synthetic IS-free K locus sequences were generated for K loci for which no naturally occurring IS-free variants have been identified to date.


### O locus database

The O locus database comprises 9 distinct loci:
- OL3, OL5 and OL9 are orthologous to _K. pneumoniae_ Species Complex OL3α/OL3β, OL5 and OL15, respectively, for which the corresponding polysaccharide structures of OL3α/OL3β and OL5 are [well understood](https://doi.org/10.1128/mmbr.00090-23). We have therefore annotated the corresponding polysaccharide phenotypes within the KoSC O locus database.
- OL2 is a much more distant ortholog of _K. pneumoniae_ Species Complex OL2α.3.
- We also include orthologs of _K. pneumoniae_ Species Complex _wbbYZ_ as 'extra genes'. In the _K. pneumoniae_ Species Complex, these genes are found elsewhere in the genome and result in conversion of an O2 polysaccharide to an O1 polysaaccahride. However, polysaccharide structures remain to be elucidated for KoSC, and given the very distant orthology of the OL2 loci, we have not annotated any associated O phenotypes or phenotype logic in the database.
- All other loci showed only partial orthology to those from the _K. pneumoniae_ Species Complex and no matched phenotypes were known at the time of discovery.

## Citations

If you use the K locus database in your work, please cite:
Ashcroft, M. / McGarry N. _et al._ Genomic characterisation of capsule polysaccharide loci in the _Klebsiella oxytoca_ Species Complex. _In prep._

If you use the O locus database in your work please cite:
McGarry N. _et al._ Genomic typing of O polysaccharides among the _Klebsiella oxytoca_ Species Complex reveals species-level conservation of _K. pneumoniae_ O antigen orthologs. _In prep._

## Curators

These databases are developed and maintained by [Naoise McGarry](https://research.monash.edu/en/persons/naoise-mcgarry/) and [Kelly Wyres](https://wyreslab.com/research-journey-kelly-wyres/) (Monash University, Australia), with major contribution from Melinda Ashcroft.

## Contribute

If you think you've found a novel K or O locus please [get in touch](mailto:kaptive.typing@gmail.com) so we can add it to the database (with attribution)!

## License

The databases are distributed under [GNU Genral Public license v3.0](https://github.com/klebgenomics/KoSC_surface_antigen_loci/blob/main/LICENSE). 

