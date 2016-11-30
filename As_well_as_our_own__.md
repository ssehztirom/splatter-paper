As well as our own Splat simulation Splatter provides implementations of several previously published simulations. These simulations have previously been published with R code or functions in existing packages but by including them in Splatter we make them available in a single place in a more user accessible way. Where only a script has been published the simulation has been reimplemented in Splatter, if the simulation is in an existing package we have simply written wrappers that provide consistent input and output but use the package implementation. We have chosen to keep the simulations as close as possible to what was originally published while keeping a consistent interface. The additional simulation are:

* Simple - A basic negative-binomal counts with gamma distributed means. This simulation is included as a reference and is not meant to truly reproduce
  scRNA-seq data.
* Lun - Published in a paper describing a normalisation method this simulation is also based on a negative-binomial with gamma means but includes a scaling factor for each cell. This simulation can also model differential expression between multiple groups.
* Lun 2 - In a second publication discussing batch effects the same authors extend the negative-binomial model to include batch effects between groups of cells. The estimation step for this simulation is quite sophisticated and many of the parameters are sampled from a real dataset rather than statistical distributions. Differential expression between two groups is included and the user can optionally select to use a zero-inflated model.
* scDD - The scDD package aims to test for differential expression between two groups but also more complex changes such as differential distributions or differential proportions. This is reflected in their simulation which can contain genes of all these types and also samples information from a real dataset.

Here we show the output of the comparison function included in Splatter. For each simulation we have estimated parameters from a real dataset then used them to produce a synthetic dataset of the same size. The real data we have used is a subset of data published by Tung et al. and contains 221 cells with 13058 genes from a single HapMap stem cell line, captured on three Fluidigm C1 plates \cite{Tung_2016}. Bad quality cells and lowly expressed genes have already been removed by the original authors but we also remove the ERCC spike-ins as these do not represent real genes. As we expect this to be a homogeneous population we do not simulate any differential expression but batch effects are included in the Lun 2 simulation. Figure 1 shows the plots returned by the comparison function.