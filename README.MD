# Introduction
These are the tutorials associated with downstream DARLIN data analysis, developed during our work in [L. Li,...,S.-W. Wang, F. Camargo, Cell (2023)](https://doi.org/10.1016/j.cell.2023.09.019) 

Single-cell lineage analysis includes
1) Data loading
2) Common allele filtering
3) Allele integration across different target loci
4) Lineage coupling or fate bias analysis

Bulk lineage analysis includes
1) Data loading
2) Common allele filtering
3) Lineage coupling or shared clone fraction analysis


For allele integration across different loci, we used a heuristic approach that remains to be further improved. 

In principle, the mutation patterns of the alleles can be further utilized for inferring lineage phylogeny. This is an advanced topic not covered by this tutorial.

We use data associated with Figure 4 in paper for the single-cell tutorial, and use the data in Figure 5 for the bulk tutorial.

# Data preparation

To download the jupyter notebooks, please run
```bash
git clone https://github.com/ShouWenWang-Lab/DARLIN_tutorial
```

These notebooks cannot be directly executed without data. Please download the entire project file (~13G) from [zendo](https://zenodo.org/records/8422061), which includes all these notebooks, as well as all the raw and processed data needed for this tutorial, arranged in the correct folder structure that is runnable.

To download all raw or processed data, please go to [GEO: GSE222486](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE222486)

# Conda environment

To run this, you need to setup a proper environment, which we may call `DARLIN_analysis`. Particulary, it requires our in-house package called `MosaicLineage` as well as `cospar`

```bash
code_directory='.' # change it to the directory where you want to put the packages
cd $code_directory
kernel_name='DARLIN_analysis'
conda create -n $kernel_name python=3.8 --yes
conda activate $kernel_name
pip install cospar
pip install --user ipykernel
pip install pytest black ipywidgets
pip install pytest-datadir pytest-cov umi_tools toolz jupyterlab pyyaml scikit-bio biopython  wand  seaborn==0.11.2  scikit-learn==1.1.1 pandas==1.5.3
python -m ipykernel install --user --name=$kernel_name
pip uninstall cospar # uninstall the old version, and install the latest
cd $code_directory
git clone https://github.com/ShouWenWang-Lab/cospar --depth=1
cd cospar
python setup.py develop
cd $code_directory
git clone https://github.com/ShouWenWang-Lab/MosaicLineage --depth=1
cd MosaicLineage
python setup.py develop
cd $code_directory
git clone https://github.com/ShouWenWang-Lab/snakemake_DARLIN --depth=1
cd snakemake_DARLIN
python setup.py develop
```

## External links

- `20231122_DARLIN_in_vivo_hematopoiesis.ipynb` is also available from [CoSpar package](https://github.com/ShouWenWang-Lab/cospar/blob/master/docs/source/20231122_DARLIN_in_vivo_hematopoiesis.ipynb).

- A 30min video about DARLIN project in [Youtube](https://www.youtube.com/watch?v=TywIb_4cPk8) or [Bilibili](https://www.bilibili.com/video/BV1sw411F7hd/?spm_id_from=333.999.0.0&vd_source=88ba2b3e0a84657ca67330d8cba9e18f).

- [MosaicLineage](https://github.com/ShouWenWang-Lab/MosaicLineage), A (mosaic) collection of python help functions related to lineage tracing data analysis, developed through the DARLIN project.

- [Shou-Wen Wang Lab website](https://www.shouwenwang-lab.com/)
