# notes-project-3

## Objectives

Find an ordered set of genes to recursively build a phylogenetic tree
that optimizes the phylogenetic signal related to a trait.

## Hypotheses
- The variability of a trait is correlated to the evolution of a set
  of genes

## Sub-problems

- How to evaluate the correlation between a tree and a trait

	- [Pagel's lambda](https://www.nature.com/articles/44766)
	- [Bloomberg's K](https://pubmed.ncbi.nlm.nih.gov/12778543/)

- How to construct a tree based on multiple genes?

	- Concatenate the genes
	- [Ghost-tree](https://link.springer.com/article/10.1186/s40168-016-0153-6)
	

## Databases

List of available databases:
https://questfororthologs.org/orthology_databases

Biggest ones:
- OrthoDB (>4k prokaryotes, 588 eukaryotes, >3k viruses)
- eggNOG (1793 prokaryotes, 238 eukaryotes, 352 viruses)
- metaPhOrs (2714 organisms)
- OMA (>2k organisms)
- OrtholugeDB (>2k organisms)

### OrthoDB 

Databases available here: https://www.orthodb.org/?page=filelist

OG = Orthologous Group 

#### Available tables (from project's README)

odb10v1_levels.tab.gz:                  NCBI taxonomy nodes where Ortho DB orthologous groups (OGs) are calculated
odb10v1_species.tab.gz:                 Ortho DB individual organism (aka species) ids based on NCBI taxonomy ids (mostly species level)
odb10v1_level2species.tab.gz:           Correspondence between level ids and species ids
odb10v1_genes.tab.gz:                   Ortho DB genes with some info
odb10v1_gene_xrefs.tab.gz:              UniProt, ENSEMBL, NCBI, GO and InterPro ids associated with Ortho DB gene
odb10v1_OGs.tab.gz:                     Ortho DB orthologous groups
odb10v1_OG2genes.tab.gz:                OGs to genes correspondence
odb10v1_OG_xrefs.tab.gz:                OG associations with GO, COG and InterPro ids
v9_v10_OGs_map.tab.gz                   mappings between the previous and current release orthologous group ids

odb10v1_all_fasta.tab.gz                AA sequence of the longest isoform for all genes, fasta formatted
odb10v1_all_og_fasta.tab.gz             AA sequence of the longest
isoform for all genes participating in OG, fasta formatted

### Trait database

From [J. Madin et
al.](https://www.nature.com/articles/s41597-020-0497-4#Sec7)

condensed_traits_NCBI.csv: taxID (subspecies) | taxID (species) | Lineage | Traits

## Example data

Table 1 from [Fierer et al.](https://www.frontiersin.org/articles/10.3389/fmicb.2014.00614/full)

## Figures
<img src="img/screenshot-meeting-w-mahdi.png" width="800"/>
