# Brain Extraction Evaluation for Tumor Segmentation with Deep Learning

[UNDER CONSTRUCTION]

Accompanying the paper "Towards fully automated deep-learning-based brain tumor segmentation: is brain extraction still necessary?".

Instructions:

1. [Install FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FslInstallation/Linux)
1. [Install CaPTk](https://cbica.github.io/CaPTk/Download.html)
1. [Install HD-BET](https://github.com/MIC-DKFZ/HD-BET)
1. Install nnU-Net and the brats submodules (already in the repo)
1. Unzip BraTS2020 training data into `data/raw/MICCAI_BraTS2020_TrainingData`
1. Put TCGA images in `data/raw/TCGA` (see below for more details on how TCGA data must be structured) and DICOM-Glioma-SEG in `data/raw/DICOM-Glioma-SEG` (and DICOM_Glioma_SEG_Metadata in `data/raw/DICOM_Glioma_SEG_Metadata`)
1. Download the non-skull-stripped T1-weighted image of the [SRI24 atlas](https://www.nitrc.org/projects/sri24/) into `data/raw/SRI24_T1.nii`


### TCGA data

The preprocessing expects the TCGA data to be organized in a slightly different way from what is provided directly in TCIA. First, the TCGA folder inside `data/raw` must have two subdirectories, `LGG` and `GBM`, containing the respective data for each study. Inside these, the structure is similar to what we get from TCIA, except all whitespaces are converted to underscores. Unfortunately, this is necessary for some of the CLIs of the preprocessores we use. **This whitespace-to-underscores conversion is also required for DICOM-Glioma-SEG data**. So, for example, the raw dicom files for the T1Gd modality of TCGA-02-0003 patient will be stored in `data/raw/TCGA/GBM/TCGA-02-0003/13.000000-AX_T1_POST-19694/*.dcm`.
