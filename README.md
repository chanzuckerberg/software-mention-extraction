# Software Knowledge Base Construction from Scientific Articles

## Why?

Most of the cutting-edge science is built on scientific software, which makes scientific software often as important as traditional scholarly literature. Biology focused software defines bioinformatics and their use is central to computational biology. Despite that, the software is not always treated as such, especially when it comes to funding, credit, and citations. 
Moreover, with the ever-growing number of open-source software tools, it is impossible for many researchers to track tools, databases, and methods in a specific field. 

## What? 

The goal of this project is to automate systematic cataloging and build a comprehensive and indexed/queryable knowledge base of scientific software mined from the biomedical literature (including preprints.) 

This knowledge base will enable:
- monitoring usage, 
- identification of essential tools and gaps, 
- analysis of trends over time,
- facilitate retrieval of popular tools and methods for specific analyses or within specific domains, and more. 

While there have been efforts to tackle different aspects of this goal (and specific to Python or R, for example), we are not aware of a comprehensive index of all scientific tools and software. 

## How? 

1. Develop a model for automated identification of software mentions in the scientific literature.

2. Develop a model for linking mentions of software to existing knowledge bases ([Wikipedia](https://en.wikipedia.org/wiki/Main_Page))


## Instructions

### Dependencies
    Python 3.7.4
    Python packages: pandas, numpy, keras, torch, nltk, sklearn, transformers, os, seqeval, 

### Training
#### Data

  Softcite: 
        Repo: https://github.com/howisonlab/softcite-dataset
        Data file: https://github.com/howisonlab/softcite-dataset/blob/master/data/corpus/softcite_corpus-full.tei.xml (downloaded on February 8, 2021)
        Instructions: Download the XML file above and place it in the data folder. 
        Process XML file: ./scripts/Parse softcite data.ipynb
        Input: ./data/softcite_corpus-full.tei.xml
        Output: ./data/labeled_dfs_all.csv

#### Model
  Training: ./scripts/Train software mentions model.ipynb 
  Input: ./data/labeled_dfs_all.csv, ‘allenai/scibert_scivocab_cased’
  Output: ./models/scibert_software_sent 
  Performance: 
  ![Alt text](https://github.com/chanzuckerberg/cord19-software-mentions/img/img1.PNG?raw=true)
	
### Inference 

#### Software Mentions
    
  Download pretrained model from: s3://meta-prod-ds-storage/software_mentions_extraction/models and place it in ./models/ folder. 
  Example of how to run the model in inference mode: ./scripts/Software mentions inference mode.ipynb
  Example: 
  ![Alt text](https://github.com/chanzuckerberg/cord19-software-mentions/img/img2.PNG?raw=true)

#### Wikipedia Linking 
  This model is based on BLINK model: https://github.com/facebookresearch/BLINK 
  Follow instructions on the github repo to download relevant models/install. 

  Example of how to run the model in inference mode: ./scripts/Link text to wikipedia.ipynb
	
  Example: 
        
  ![Alt text](https://github.com/chanzuckerberg/cord19-software-mentions/img/img3.PNG?raw=true)

## Related documents: 

- [Project Details](https://docs.google.com/document/d/1BwFHpvispYfniaQR-xx00VpP0EdYxXnkWp-cldWYDr4/edit)
- [LH presentation (12/18/2020)](https://drive.google.com/file/d/1Be85kFXwtCnXf2iajZAz_aN0ldN9HhdG/view)


