## TCGA_PanCancer_Immune_Genetics

Last update: 03/07/2022

## Immune Traits

139 immune traits were curated from (Thorsson et al., 2018) for analysis. Immune Trait categories were defined based on the methodological source of the data. Immune trait functional modules were defined based on Pearson correlation analysis.

## Citations
Please cite the following when using the data and code contained here in: 
* Sayaman, Saad, Heimann, et al., STAR Protocols (2022). Analytic pipelines to assess the relationship between immune response and germline genetics in human tumors. https://doi.org/10.1016/j.xpro.2022.101809
* Sayaman, Saad et al., Immunity (2021). Germline genetic contribution to the immune landscape of cancer. https://doi.org/10.1016/j.immuni.2021.01.011

Please cite the following when downloading the TCGA QC and HRC imputed genotyping data:
* Chambwe, Sayaman, et al., STAR Protocols (2022). Analysis of germline-driven ancestry-associated gene expression in cancers. https://doi.org/10.1016/j.xpro.2022.101586
* Sayaman, Saad et al., Immunity (2021). Germline genetic contribution to the immune landscape of cancer. https://doi.org/10.1016/j.immuni.2021.01.011
* Carrot-Zhang et al., Cancer Cell (2020). Comprehensive Analysis of Genetic Ancestry and Its Molecular Correlates in Cancer. https://doi.org/10.1016/j.ccell.2020.04.012

Please additionally cite the following when referencing the immune traits:
* Thorsson et al., Immunity (2018). The Immune Landscape of Cancer. https://doi.org/10.1016/j.immuni.2018.03.023
  
Please additionally cite the following when using code to calculate gene expression signatures from Wolf et al. and Amara et al.:
* Wolf, et al., PLoS ONE (2014). Gene co-expression modules as clinically relevant hallmarks of breast cancer diversity. https://doi.org/10.1371/journal.pone.0088309
* Amara, et al., Breast Cancer Res Treat (2017). Co-expression modules identified from published immune signatures reveal five distinct immune subtypes in breast cancer.  https://doi.org/10.1007/s10549-016-4041-3

Please additionally cite the following when using code to calculate gene expression signatures from Bindea et al. and Senbabaogulu et al.:
* Bindea et al., Immunity (2013). Spatiotemporal dynamics of intratumoral immune cells reveal the immune landscape in human cancer. https://doi.org/10.1016/j.immuni.2013.10.003
* Senbabaoglu et al., Genome Biology (2016). Tumor immune microenvironment characterization in clear cell renal cell carcinoma identifies prognostic and immunotherapeutically relevant messenger RNA signatures. https://doi.org/10.1186/s13059-016-1092-z

## Contributors
* Rosalyn W. Sayaman, Ph.D., University of California, San Francisco: rwsayaman@gmail.com
* Vesteinn Thorsson, Ph.D., Institute for Systems Biology
* Denise M. Wolf, Ph.D., University of California, San Francisco
* Acknowledgment: David L. Gibbs, Ph.D., Institute for Systems Biology


## Description
Code contained herein are meant as a guide and should be modified and adapted to match your server specifications and directories.

Authors will not be available to assist with troubleshooting. Please familiarize yourself with the associated scripting languages, and contact your server admin for instructions on the proper format for submitting jobs to your compute cluster and to ensure all necessary programs are installed.


## Required Software
* R (https://www.r-project.org/)


## Workflow

139 immune traits were curated from (Thorsson et al., 2018) for analysis. Immune Trait categories were defined based on the methodological source of the data. Immune trait functional modules were defined based on Pearson correlation analysis.

1.	Prepare curated set immune traits genes.

    a.	Curated set of 139 immune traits in TCGA can be downloaded from (Sayaman et al., 2021) Table S2. 
      
    b.	For calculation of immune traits in a new dataset, consult  (Thorsson et al., 2018) methods section describing methodologies and source papers for derivation of specific immune traits.	
            
    i. Code to generate gene expression signatures from (Wolf et al., 2014) (Amara et al., 2017) and single sample gene set enrichment signatures from (Bindea et al., 2013; Şenbabaoğlu et al., 2016) are provided as a resource.
    
    * Code for Wolf et al., 2014, Amara et al., 2017 gene expression immune signatures: https://github.com/rwsayaman/TCGA_PanCancer_Immune_Genetics/tree/main/Code/Immune_Traits/Wolf_Amara
    * Code for Bindea et al., 2013, Şenbabaoğlu et al., 2016 ssGSEA enrichment scores:
https://github.com/rwsayaman/TCGA_PanCancer_Immune_Genetics/tree/main/Code/Immune_Traits/ssGSEA_Bindea_Senbabaoglu
            
    ii. Necessary transformation of immune trait values in TCGA for use in genetic analysis described below are annotated in (Sayaman et al., 2021)  (Table S2).


2.	Calculate Pearson correlations of continuous values of the 139 immune traits. 
3.	Cluster correlation matrix using complete agglomerative clustering method using (1-correlation) as distance metric.
a.	Generate heatmap with clustering dendrogram using heatmap.2 function in gplots R package or similar algorithm.
4.	Identify highly correlated blocks (dendrogram clusters) of immune-traits to generate immune functional modules.

**Note:** 	See script used in this section "ImmunePheno139.Cibersort.continuous_cor.pearson.R" and associated figures generated in the "Figures" folder.


### Limitations
 
Immune signatures lack cancer-specific cell type resolution. The majority of immune traits were calculated based on specific gene sets from expression data (RNA-sequencing) from bulk tissue to generate estimates of immune cell activation or abundance using different enrichment or deconvolution techniques. Caution should be exercised when interpreting results in the context of specific tumors or cell types. However, many of these signatures were validated in specific tissues and cancers via FACS sorting or immunohistochemistry/immunofluorescence imaging of immune populations.

