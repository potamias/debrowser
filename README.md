# debrowser: 
Differential Expression Analysis Toolbox

# Introduction

Differential gene expression analysis has become an increasingly popular tool
in determining and viewing up and/or down experssed genes between two sets of
samples.  The goal of Differential gene expression analysis is to find genes
or transcripts whose difference in expression, when accounting for the
variance within condition, is higher than expected by chance.  DESeq2
<https://bioconductor.org/packages/release/bioc/html/DESeq2.html> is an R
package available via Bioconductor and is designed to normalize count data
from high-throughput sequencing assays such as RNA-Seq and test for
differential expression (Love et al. 2014).  With multiple parameters such as
padjust values, log fold changes, plot styles, and so on, altering plots
created with your DE data can be a hassle as well as time consuming.  The
Differential Expression Browser uses DESeq2 coupled with shiny to produce
real-time changes within your plot queries and allows for interactive browsing
of your DESeq results. In addition to DESeq analyzation, DEBrowser also offers
a variety of other analyzation plots and tools to help visualize your data
even further.

# Quick start

Running these simple command will launch the DEBrowser within your local
machine.

Before you start;
First, you will have to install R and/or RStudio.
(On Fedora/Red Hat/CentOS, these packages have to be installed;
openssl-devel, libxml2-devel, libcurl-devel, libpng-devel)

```
# Installation instructions from source:
# 1. Install the dependencies by running the lines below in R or RStudio. 
### Packages for R.

install.packages(“ggvis”)

install.packages(“ggplot2”)

install.packages(“RColorBrewer”)

install.packages(“DT”)

install.packages(“gplots”)

install.packages(“devtools”)
### BioC Packages for R.

source(“http://www.bioconductor.org/biocLite.R”)

biocLite()

biocLite(“clusterProfiler”)

biocLite(“ReactomePA”)

biocLite(“shiny”)

biocLite(“DESeq2”)

biocLite(“annotate”)

biocLite(“AnnotationDbi”)

biocLite(“org.Hs.eg.db”)

biocLite(“DOSE”)

biocLite(“edgeR”)

# 2. install debrowser using the command below

R CMD INSTALL debrowser_0.99.0.tar.gz

# 3. Start R and load the library

library(debrowser)

#  4. start DE browser

startDEBrowser()
```

# Browsing your Data

Once you have the DEBrowser running, a page will load asking to choose a CSV
file.  In order to run DESeq2, we are going to need gene quantifications for
those genes contained in a CSV or TSV format.

IE:

```
gene  transcript  exper_rep1 exper_rep2 control_rep1 control_rep2
DQ714826  uc007tfl.1  0.00  0.00  0.00  0.00
DQ551521  uc008bml.1  0.00  0.00  0.00  0.00
AK028549  uc011wpi.1  2.00  1.29  0.00  0.00
```

You can also view/use the data.tsv located within the data directory as an
example. After obtaining and loading in the gene quantifications file, you
are then able to select which samples will be selected for your first
condition and second condition for differential expression based on the column
headers within your data file. Once you've selected your conditions, you are
then ready to run DESeq2 to calculate differential expression by clicking on
the Run DESeq! button.

After clicking on the Run DESeq! button, DESeq will run, analyzing your data
and shiny will output the information obtained from DESeq into an interactive
graph format. You will have options to adjudt the padjust value and fold
change cut off, as well as selecting a different dataset such as upregulated
genes only and changing the type of plot you will be viewing on the left hand
side of the screen.

On the right hand side of the screen will be your plots and graphs that shiny
has created for you. By hovering over specific plot points, bar graphs will be
generated for that specific plot point.  You also have the ability to
select/highlight specific portions of your graph to be able to zoom in. Making
a selection will populate the graph on the right as a graph of your selected
original graph.

Additional plots and tables are generated by selecting one of the many tabs at
the top of the screen. Additional plots allows you to create an all-to-all
plot, a specific type of heatmap, as well as a principal component analysis
plot.  The GO Term tab allows you access various Gene Ontology databases to
create a variety of GO Term plots.  The rest of the tabs contain specific
tabled information about your DESeq data that you can then search or export
for your own personal use. All detected describes all the genes detected
while the Up/Down tabs show the up or down regulated genes.  The final tab
Selected is populated based on your current selection of your graph.

With that, you've now successfully navigated the DEBrowser and are ready to
start inserting your own data files and browsing your own experiments.  Enjoy
the DESeq browser!
