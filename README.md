# BetaCompositionalModel

MATLAB implementation of the Beta Compositional Model algorithm for Hyperspectral unmixing. See related paper, doi: 10.1109/JSTARS.2014.2330347
***************************************************************

***If this code is used, cite it: Xiaoxiao Du, & Alina Zare. (2019, April 12). GatorSense/BetaCompositionalModel: Initial Release (Version v1.0). Zenodo. http://doi.org/10.5281/zenodo.2638288
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.2638288.svg)](https://doi.org/10.5281/zenodo.2638288)

***NOTE: If the BCM Unmixing Algorithm is used in any publication or presentation, the following reference must be cited:

X. Du, A. Zare, P. Gader, D. Dranishnikov, ìSpatial and Spectral Unmixing Using the Beta Compositional Model,î  IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing, vol. 7, no. 6, pp. 1994-2003, June 2014.

***************************************************************

The BCM Unmixing Algorithm runs using the following function:

[Parameters] = BCMParameters(endmembers);  
[P] = BCM(Xim, Parameters, MethodFlag)

The endmembers input is a 1xM cell of endmember samples (known) where M is the number of endmembers.  

DxNumESamples double matrix within each cell, where D is the number of spectral bands and NumESamples is the number of endmember samples.  

The Xim input is a N1xN2xD matrix of N1xN2 image data points of dimensionality D.  

The parameters input is a struct with the following fields:  
 Parameters - struct - The struct contains the following fields:  
               % These parameters are user defined (can be modified)  
                   1. NumberIterations: Number of iterations  
                   2. K: Number of nearest neighbors  
                   3. c: Number of clusters for spatial K-means  
                   4. SigV: Weighting on SigmaV  
                   5. SigM: Weighting on SigmaMean  
                   6. s: Scaling parameter for location information  
                   7. ECovariance: diagonal covariance on endmembers, currently same for all endmembers  
               % These parameters are computed from input data and known endmembers (does not need modification)  
                   8. MaxNumEMs, M: Number of endmembers  
                   9. bandnum, D: Number of spectral bands/dimensions  
                  10. N: Number of pixels(input data points)  
                  11. Emean: Mean of endmember samples  
                  12. BetaParameters: parameters for fitting a Beta distribution to each band of each endmember  
               *Parameters can be modified in [Parameters] = BCMParameters(endmembers) function.  

The MethodFlag input is an 1x1 integer, choose from 1, 2, 3, 4, where each number indicates one BCM approach:  
           1. BCM-Spectral-QP (Quadratic Programming Approach)  
           2. BCM-Spectral-MH (Metropolis-Hastings Sampling Approach)  
           3. BCM-Spatial-QP  
           4. BCM-Spatial-MH  


********************************************************************* 
Description of files:

    demo_allMethods.m - This is the main file. The demo performs BCM unmixing and compares with FCLS and NCM unmixing methods.
    BCM.m - BCM (Beta Compositional Model) Spatial and Spectral Unmixing Algorithms.
    BCMParameters.m - Sets the parameters to be used during the BCM unmixing algorithm. Please change accordingly.
    BCM_Spectral.m- Performs BCM-Spectral unmixing, including BCM-Spectral-QP and BCM-Spectral-MH approaches.
    BCM_Spatial.m - Performs BCM-Spatial unmixing, including BCM-Spatial-QP and BCM-Spatial-MH approaches.
    hyperFcls.m - Performs fully constrained least squares on pixels of M. Written by I. Gerg (2012): Matlab Hyperspectral Toolbox [Online]. Available at https://github.com/isaacgerg/matlabHyperspectralToolbox.git.
    unmix_qpas_correct.m - Performs quadratic unmixing given endmember mean values.
    unmix2.m - Performs NCM-QP unmixing.
    unmixGaussian.m - Performs NCM-MH unmixing.
    PError.m - Computes the proportion errors per pixel per endmember given true and estimated proportion values.
    demo.mat - Hyperspectral image and endmember samples (provided for demo purposes)
    Ptrue.mat - Manual ground truth for the demo hyperspectral image (provided for demo purposes)
***********************************************************************


 Authors: Xiaoxiao Du, Alina Zare  
 University of Missouri, Department of Electrical and Computer Engineering  
 Email Address: xdy74@mail.missouri.edu; zarea@missouri.edu  
 Latest Revision: November 3, 2014  

This code uses MATLAB Statistics Toolbox and Matlab Optimization Toolbox. 


