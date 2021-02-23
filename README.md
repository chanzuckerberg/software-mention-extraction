# Software Mention Extraction and Linking from Scientific Articles :floppy_disk:

Most of the cutting-edge science is built on scientific software, which makes scientific software often as important as traditional scholarly literature. Biology focused software defines bioinformatics and its use is central to computational biology. Despite that, the software is not always treated as such, especially when it comes to funding, credit, and citations. 
Moreover, with the ever-growing number of open-source software tools, it is impossible for many researchers to track tools, databases, and methods in a specific field. 

## :star: Instructions

### Dependencies
    Python 3.7+ (tested on 3.7.4)
    Python packages: pandas, numpy, keras, torch, nltk, sklearn, transformers, os, seqeval, 

### Training
#### Data

  __Softcite:__ 
  
  * [Softcite data repository](https://github.com/howisonlab/softcite-dataset)
	
  * [Full corpus](https://github.com/howisonlab/softcite-dataset/blob/master/data/corpus/softcite_corpus-full.tei.xml) (downloaded on February 8, 2021)
        
  * Download the XML file above and place it in the ./data folder. 
   
  * XML file processing script: ` ./scripts/Parse softcite data.ipynb`
  	  
	  * *Input:* ./data/softcite_corpus-full.tei.xml
    	  
	  * *Output:* ./data/labeled_dfs_all.csv

#### Model

  * Model training script: `./scripts/Train software mentions model.ipynb` 
  
	  * *Input:* ./data/labeled_dfs_all.csv, ‘allenai/scibert_scivocab_cased’

	  * *Output:* ./models/scibert_software_sent 
  
  __Performance:__
 
  <img src="https://github.com/chanzuckerberg/cord19-software-mentions/blob/main/img/img1.png" width="600">
	
### Inference 

#### Software Mentions
    
  * Download pretrained model 'scibert_software_sent' from: s3://meta-prod-ds-storage/software_mentions_extraction/models and place it in the ./models/ folder. 
  
  * Example of how to run the model in inference mode: `./scripts/Software mentions inference mode.ipynb`
  
  * *Example:* 
  
  <img src="https://github.com/chanzuckerberg/cord19-software-mentions/blob/main/img/img2.png" height="200">

#### Wikipedia Linking 

  * This model is based on [BLINK model](https://github.com/facebookresearch/BLINK)
  
  * Follow instructions on the github repo to download relevant models/install. 

  * Example of how to run the model in inference mode: `./scripts/Link text to wikipedia.ipynb`
	
  * *Example:* 
        
  ![](https://github.com/chanzuckerberg/cord19-software-mentions/blob/main/img/img3.png?raw=true)

### Extract Mentions of Software from CORD-19 Dataset :microbe: :books:

  * __CORD-19 data__: More information and download instructions: [here](https://github.com/allenai/cord19)
  * Save to the ./data/ folder
  * Run notebook: `./scripts/Software mentions CORD19.ipynb`

## Related documents: 

* [Project Details](https://docs.google.com/document/d/1BwFHpvispYfniaQR-xx00VpP0EdYxXnkWp-cldWYDr4/edit)
* [LH presentation (12/18/2020)](https://drive.google.com/file/d/1Be85kFXwtCnXf2iajZAz_aN0ldN9HhdG/view)


