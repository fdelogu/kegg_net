---
output:
  pdf_document: default
  html_document: default
  word_document: default
---
# KEGG Orthology and Metabolites Network

General script to download and parse information from KEGG to generate a metabolic network spanning all the KEGG Orthology (KO) entries. A set of KOs can be plugged in to generate a custom network, e.g. a microbial community.

The generation of the network follows the one described in Roume et al. 2015, Biofilms and Microbiomes suppl. material, section: "Community-wide metabolic network reconstructions"
.

In this representation each node of the network is a Collapsed KEGG Orthology term (CKO) summarising all the KOs which reactions have the same metabolites. A map between CKOs and KOs is given to relate back the simplified nodes with the orginal entries.

Network colore according to the second level of the [KEGG Pathway and Brite Hierarchy](https://www.genome.jp/kegg-bin/get_htext?ko00001.keg) and node size proportional to the degree:

![alt text](/results/net_plot.png)

The network can be used for further analysis, for instance this is the relationship between number of nodes and average gedree for each metabolic pathway listed in KEGG:

![alt text](/results/kegg_NDeg.png)

## Folder structure and files

### RMarkdown notebooks:
- **net_maker.Rmd** *It evaluates the needed files, download them and build the network*
- **ko_hierarchy_parser.Rmd** *It downloads the KEGG Orthology and Brite hierarchy and parses it*
- **net_analyzer.Rmd** *It does some basic analysis of the previously built network.*

### Compiled notebooks:
- results/net_maker.html 
- results/ko_hierarchy_parser.html 
- results/net_analyzer.html

### Results:
- **results/ko2cko.txt** *Map between KOs and the nodes (CKOs)*
- **results/ko.txt** *KEGG Pathway and Brite Hierarchy*
- **results/CKO_Adj.txt** *Adjacency matrix of the network*

### Figures:
- results/kegg_NDeg.png
- results/net_plot.png 

### Other:
- README.md   Readme file.
- data/ *Will contain some intermediate tables and maps between different types of KEGG entries (e.g. reaction-reaction classes, etc.)*
- data/reactions/ *Will be populated by the entries of the reactions (RN) dataset of KEGG*

## To do:

The script is still under modification. There are some things that will addressed as soon as possible:
- Exploit the adjacency matrix sparsity to save space
