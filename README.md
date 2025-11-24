# CopyGAT
CopyGAT: a graph attention mechanism-based method for inferring copy number variations from scRNA-seq data

file, cc_genes, bin_size=25, max_cp=15, intermediate_dim=128, latent_dim=20, batch_size=128, epochs=200, number_of_clones=2 are the default parameters of the model. The best performance for different datasets occurs under different settings.
If you want to identify tumor subclones, you can control this with the number_of_clones parameter. The file parameter is the scRNA-seq input data.
cc_genes is the cell cycle gene file.
bin_size=25 is used to control the size of the gene window, with the default being 25.
The results will achieve the best performance in certain conditions.

"Next, we will introduce the workflow of the model."
Workflow of CopyGAT. (a) Data preprocessing, where a cell similarity matrix is constructed using the K-nearest neighbors (KNN) algorithm. (b) Discrimination of normal cells and cancer high-risk cells, followed by the inference of a pseudo-copy number matrix. The binned gene expression matrix x_bin and the cell similarity graph are input into the GAT encoder to extract features that differentiate cancer high-risk cells from normal cells. Subsequently, Gaussian Mixture Model (GMM) clustering is applied to partition the cells into two categories. The normal cell cluster and the cancer high-risk cell cluster are identified based on the autocorrelation coefficients of each cluster. The normal cell cluster is then used to construct a baseline, enabling the calculation of the pseudo-copy number matrix. (c) Copy number estimation across all cells. The pseudo-copy number matrix and the cell similarity graph are fed into the GAT encoder to learn low-dimensional representations of the copy number features. These low-dimensional features are then decoded using a negative binomial decoder to estimate the mean copy number, facilitating more precise copy number inference
