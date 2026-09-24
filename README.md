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
    - [K loci](#k-loci)
    - [Predicted K types](#predicted-k-types)   
  - [O locus database](#o-locus-database)
- [How to use the databases](#how-to-use-the-databases)
  - [Using command-line Kaptive](#using-command-line-kaptive)
  - [Using Kaptive Web](#using-kaptive-web)    
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
* _"Klebsiella mammaliorum"_ (formal description in progress)
* plus two unnamed taxa 

The KoSC Kaptive databases also include loci from the closely related _K. indica_ (see phylogeny below) since this organism would otherwise not be captured by any available K and O databases. 

![Unrooted phylogeneny showing the relationships between Klebsiella species and other selected Enterobacteriales, with KoSC and K.indica marked](/images/Enterobacteriales_tree_KoSC.png)

## Database formats and versions

The K and O locus databases each comprise two files that are required to run Kaptive:
1. A multi-genbank file containing each unique locus sequence and its gene annotations.
2. A metadata file in TOML format, which provides essential information about the database (e.g. version, target organism(s), curator details), plus any special [phenotype logic](https://klebgenomics.github.io/Kaptive/db/curation.html#phenotype-logic) that applies to the database.

Please see the [Kaptive docs](https://klebgenomics.github.io/Kaptive/db/curation.html) for more details on the database file formats.

> [!Note] 
> We use Github tags to mark the database versions. See [here](https://github.com/klebgenomics/KoSC-surface-antigen-loci/tags) for a full list of database versions in this repository.

### How are loci defined?

Loci are defined by the rules of the [Kaptive typing framework](https://klebgenomics.github.io/Kaptive/db/overview.html#what-is-a-locus), which states that **a unique locus should represent a unique set of genes**, with the assumption that this encodes a unique
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

#### K loci

As of v1.0 the [K locus database](https://github.com/klebgenomics/KoSC-surface-antigen-loci/blob/main/Klebsiella_oxytoca_Species_Complex_K_locus_database.gbk) comprises 88 distinct loci:

- KL1 corresponds to the K locus of strain K15g, for which the capsule locus and polysaccharide structure was previously [described](https://doi.org/10.1134/s0006297925601935). 
- K loci KL26, KL29, KL41, KL66, KL70 and KL74 correspond to the originally defined _Klebsiella_ serotype reference strains (sequences described [here](https://doi.org/10.1038/srep15573)). These strains have been broadly assumed as _K. pneumoniae_ but are now known to be members of the KoSC.
- All other loci were defined from DNA sequence data on the basis of gene content, and numbered arbitrarily as described in [Aschcroft/McGarry et al. bioRxiv 2026](https://doi.org/10.64898/2026.07.16.739023)).

> [!Note]
> Insertion sequences (IS) are excluded from this database since we assume that the ancestral sequence was likely IS-free and IS transposase genes are not specific to the K locus.
> Synthetic IS-free K locus sequences were generated for K loci for which no naturally occurring IS-free variants have been identified to date.

> [!Tip]
> You can see a full list of database versions in this repository [here](https://github.com/klebgenomics/KoSC-surface-antigen-loci/tags). The version displayed/downloaded by default is the most recent version (highest number).

#### Predicted K types

K phenotypes are annotated in the database for those loci where corresponding serological types and/or polysaccharide structures have been defined, and for two loci for which we predicted functional equivalence to those in _K. pneumoniae_ for which serotypes and/or polysaccharide structures have been defined. These phenotype predictions are reported in the Kaptive output as the `Best match type`.

| K locus | K type         | Structure reference                                                                               |
| ------- | -------------- | ------------------------------------------------------------------------------------------------- |
| KL1     | K1             | [Lukianova et al. Biochemistry Moscow 2026](https://doi.org/10.1134/S0006297925601935)            |
| KL26    | K26            | [Di Fabio et al. Carbohydrate Research 1985](https://doi.org/10.1016/S0008-6215(00)90673-6)       |
| KL29    | K29            | Not applicable, no structure defined to-date                                                              |
| KL41    | K41            | [Joseleau et al. Carbohydrate Research 1978](https://doi.org/10.1016/S0008-6215(00)83742-8)       |
| KL66    | K66            | [Jansson et al. Carbohydrate Research 1984](https://doi.org/10.1016/0008-6215(84)85226-X)         |
| KL70    | K70            | [Dutton et al. Carbohydrate Research 1978](https://doi.org/10.1016/S0008-6215(00)80879-4)         |
| KL74    | K74            | [Dutton et al. Carbohydrate Research 1980](https://doi.org/10.1016/S0008-6215(00)85196-4)         |
| KL6     | K6 (=Kp K43)   | [Elsässer-Beile et al. Carbohydrate Research 1978](https://doi.org/10.1016/S0008-6215(00)84316-5) |
| KL11    | K11 (=Kp K102) | [Ravenscroft et al. Carbohydrate Polymers 2025](https://doi.org/10.1016/j.carbpol.2025.124385)    |

Kp = _K. pneumoniae_

> [!TIP] 
> Kaptive will report `Best match type` as `Capsule null` when it identifies a truncation in an essential capsule synthesis / assembly gene e.g. _wza_, _wzb_, _wzc_, _wzx_ and/or _wzy_, or an initiating glycosyltransferase gene, _wcaJ_ or _wbaP_.

### O locus database

As of v1.0 the [O locus database](https://github.com/klebgenomics/KoSC-surface-antigen-loci/blob/main/Klebsiella_oxytoca_Species_Complex_O_locus_database.gbk) comprises 9 distinct loci:

- OL3, OL5 and OL9 are orthologous to _K. pneumoniae_ Species Complex OL3α/OL3β, OL5 and OL15, respectively, for which the corresponding polysaccharide structures of OL3α/OL3β and OL5 are [well understood](https://doi.org/10.1128/mmbr.00090-23). We have therefore annotated the corresponding predicted polysaccharide phenotypes within the KoSC O locus database.
- OL2 is a much more distant ortholog of _K. pneumoniae_ Species Complex OL2α.3, and matches the locus [recently described](https://doi.org/10.1016/j.carbpol.2026.125475) for _K. pasteurii_ strain 0.067 expressing a polysaccharide structure matching _K. pneumoniae_ O1αβ,2αβ.
- We also include orthologs of _K. pneumoniae_ Species Complex _wbbYZ_ as 'extra genes'. In the _K. pneumoniae_ Species Complex, these genes are found elsewhere in the genome and result in conversion of an O2 polysaccharide to an O1 polysaaccahride.
- All other loci showed only partial orthology to those from the _K. pneumoniae_ Species Complex and no matched phenotypes were known at the time of discovery.

> [!Tip]
> You can see a full list of database versions in this repository [here](https://github.com/klebgenomics/KoSC-surface-antigen-loci/tags). The version displayed/downloaded by default is the most recent version (highest number).


## How to use the databases

The databases are designed for typing whole genome assemblies using [Kaptive](https://github.com/klebgenomics/Kaptive/). You can install and run Kaptive via the command-line or upload your assemblies to [Kaptive Web](https://kaptive-web.erc.monash.edu/). Alternatively, you can upload your assemblies to the third-party platform, [Pathogenwatch](https://pathogen.watch/).

> [!Tip]
> Test data are available [here](https://github.com/klebgenomics/KoSC-surface-antigen-loci/tree/main/test_data). These include six whole genome assemblies downloaded from the [NCBI RefSeq](https://www.ncbi.nlm.nih.gov/refseq/) database (labelled `*.fasta`), plus the corresponding output tables generated via command-line Kaptive (labelled `kosc_k_results.txt` and `kosc_o_results.txt`).

### Using command-line Kaptive

Make sure you have [Kaptive installed](https://klebgenomics.github.io/Kaptive/#1-install-kaptive) and accessible in your path. 

#### 1. Install the relevant database(s)

```bash
kaptive db install kosc_k
kaptive db install kosc_o
```

#### 2. Run Kaptive on your genome assemblies

```bash
kaptive type kosc_k *.fasta > results.tsv
```

This will run Kaptive on each assembly with the file suffix `.fasta`, using the KoSC K locus database, and print the results to a single file called `results.tsv`. For full details of all command line options see the [Kaptive docs](https://klebgenomics.github.io/Kaptive/cli/serotyping.html).

#### 3. Understand your output

Kaptive produces a tab-separated values (TSV) report, which you can easily open up in Excel, Numbers, or any text editor to browse through. 

Here are the key columns in your `results.tsv` file:

* **Kaptive version**: The version of the Kaptive code used to generate these results.
* **Database name**: The name of the database used to generate these results.
* **Database version**: The version of the database used to generate these results.
* **Assembly**: The name of your input genome file.
* **Best match locus**: The best-matching locus found in the database (e.g., `KL1`).
* **Best match type**: The predicted phenotype based on the best-matching locus and any special phenotype logic (e.g. taking into account any other genes elsewhere in the genome that are known to impact the phenotype, and/or gene truncations that can inhibit polysaccharide production).
* **Confidence**: How confident Kaptive is in the call - this is either "Typeable" or "Untypeable"

> [!TIP]
> We strongly recommend treating "Untypeable" results as unknown loci unless you are able to perform your own follow-up investigations. "Untypeable" results can indicate a genuine novel locus OR a poor quality match that may be incorrect. It is not possible to distinguish these options without further interrogation of the Kaptive results and your genome assembly. You can learn more in our [Kaptive webinars](https://klebnet.org/training/). 

For a deeper dive into interpreting the results, see the [Kaptive docs](https://klebgenomics.github.io/Kaptive/serotyping/results.html).

### Using Kaptive Web

[Kaptive Web](https://kaptive-web.erc.monash.edu/) provides a point and click, graphical interface to run Kaptive. It is designed for those who are less confident with command-line applications.

#### 1. Log into Kaptive Web

For security reasons, Kaptive Web now requires a log in. You can use a [Github](https://github.com/signup) or an [ORCiD](https://orcid.org/register) account to log in. You can delete the record of your account in Kaptive Web at any time via the `Settings` menu at the top right of the page.

#### 2. Select your organism of interest

Use the dropdown menu to select your organism of interest and see the available databases e.g. _Klebsiella oxytcoa_ Species Complex.
The database versions and citations will be shown.

![Kaptive Web home page, with KoSC databases selected](/images/Kaptive_Web_KoSC_home.png)

> [!TIP]
> The current Kaptive Web and Kaptive versions are shown at the bottom of the page. 

#### 3. Upload your genome assemblies

Browse and select genome assembly files to upload from your computer, or drag and drop your files into the panel on the right.

Assemblies must be in FASTA format, one genome per file and no more than 1000 files at a time. 

Optionally, add a memorable name for your analysis run so you can easily find it later. 

Click `Serotype!` to start your analysis.

#### 4. View your results 
When ready, your results will appear in the `Serotyping Results` tab. Each genome will be shown in a single row with the following information:

* **Run**: The name of the analysis run, either your designated name or an auto-generated alphanumeric identifier. 
* **Genome**: The name of your input genome file.
* **Locus**: The best-matching locus found in the database (e.g., `KL1`). 
* **Phenotype**: The predicted phenotype based on the best-matching locus and any special phenotype logic (e.g. taking into account any other genes elsewhere in the genome that are known to impact the phenotype, and/or gene truncations that can inhibit polysaccharide production).
* **Confidence**: How confident Kaptive is in the call - this is either "Typeable" or "Untypeable"
* **View**: Selecting the `View` button will allow you to toggle between an interactive image of the locus found in your assembly, and the detailed Kaptive results text. 

`Locus`, `Phenotype`, `Confidence` and `View` are grouped by database e.g. for KoSC you will see one set of columns for the K locus database and another set of columns for the O locus database. 

![Kaptive Web results page, with KoSC results shown](/images/Kaptive_Web_KoSC_results.png)

> [!TIP]
> We strongly recommend treating "Untypeable" results as unknown loci unless you are able to perform your own follow-up investigations. "Untypeable" results can indicate a genuine novel locus OR a poor quality match that may be incorrect. It is not possible to distinguish these options without further interrogation of the Kaptive results and your genome assembly. You can learn more in our [Kaptive webinars](https://klebnet.org/training/).

For information on the detailed Kaptive results, see the [Kaptive docs](https://klebgenomics.github.io/Kaptive/serotyping/results.html).

## Citations

If you use the **K locus database** please cite:  
Ashcroft, M. / McGarry N. _et al._ Genomic characterisation of capsule polysaccharide loci in the _Klebsiella oxytoca_ Species Complex. DOI: https://doi.org/10.64898/2026.07.16.739023

If you use the **O locus database** please cite:  
McGarry N. _et al._ Genomic typing of O polysaccharides among the _Klebsiella oxytoca_ Species Complex reveals species-level conservation of _K. pneumoniae_ O antigen orthologs. _In prep._

If you use command-line **Kaptive** please cite:  
Stanton _et al._ 2025. Fast and accurate _in silico_ antigen typing with Kaptive 3. Microbial Genomics:11(6):001428 DOI: [https://doi.org/10.1099/mgen.0.001428](https://doi.org/10.1099/mgen.0.001428).

If you use **Kaptive Web** please cite:  
Wick _et al._ 2018. Kaptive Web: User-friendly capsule and lipopolysaccharide serotype prediction for _Klebsiella_ genomes. Journal of Clinical Microbiology:56(6) DOI: [https://doi.org/10.1128/jcm.00197-18](https://doi.org/10.1128/jcm.00197-18).

## Curators

These databases are developed and maintained by [Naoise McGarry](https://research.monash.edu/en/persons/naoise-mcgarry/) and [Kelly Wyres](https://wyreslab.com/research-journey-kelly-wyres/) (Monash University, Australia), with major contribution from Melinda Ashcroft.

## Contribute

If you think you've found a novel K or O locus please [get in touch](mailto:kaptive.typing@gmail.com) so we can add it to the database (with attribution)!

## License

The databases are distributed under [GNU Genral Public license v3.0](https://github.com/klebgenomics/KoSC-surface-antigen-loci/blob/main/LICENSE). 

