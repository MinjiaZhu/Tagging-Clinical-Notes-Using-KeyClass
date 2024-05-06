# Tagging-Clinical-Notes-Using-KeyClass
2024 Deep Learning in Healthcare final project for Team 62

The goal of this project is to reproduce the methodology outlined in the paper below:
* [KeyClass_Classifying_Unstructured_Clinical_Notes_with_Automatic_Weak_Supervision.pdf](https://arxiv.org/pdf/2206.12088.pdf)

## KeyClass Github
* https://github.com/autonlab/KeyClass

## FasTag Github
* https://github.com/rivas-lab/FasTag

## Steps to Run

### Data Preparation
- Obtain access and download the MIMIC3 dataset, for this project, we only need 2 from [MIMIC-III](https://physionet.org/content/mimiciii/1.4/) dataset: NOTEEVENTS.csv and DIAGNOSES_ICD.csv 
- We used GCP for secure storage and did not include the files with sensitive infomration in the repo.
- Run createAdmissionNoteTable.R, which is included in the original FasTag Github (code from 7 years ago so some modifications were made). This script will pre-process the MIMIC-III data (NOTEEVENTS.csv, ICD9.csv), join ICD-9 and Notesevents table, filter and split in to train and validation set.
- Place the output files (icd9NotesDataTable_train.csv, icd9NotesDataTable_valid.csv) in /data folder
- [Optional] Original paper trained on large GPU, for reproducing and testing purpose, we used split_file.py to generate random samples and only ran on 10% of the original dataset.
- helper.py under /keyclass was modified from the original KeyClass repo's utils.py, with new functions specifically for processing MIMIC-III dataset, these functions were heavily utilized in process training and validation dataset and generate labels. 
 
### Install Dependencies
* Trining using GPU (CUDA), code included in final project notebook
* Clone this github repo in colab directly, this repo contains important changes from the original key class repo which will be used to run mimic data:
  * helper.py: contains additional functions mainly for processing MIMIC dataset and handling labels
  * yaml files in config_files: tweaked original example config to use for training
  * label model to categorize data
* package dependencies in requirements.txt

### Model Training 
* follow: [DLH_Project_Final.ipynb](https://github.com/MinjiaZhu/Tagging-Clinical-Notes-Using-KeyClass/blob/main/project_code/DLH_Project_Final.ipynb) for step by step execusion on a subset of data.




