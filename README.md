# Visual_Computing_CNN_for_AD , CS22MDS15012

### 1. Follow this to download and process the data before it can be used for model training

1. Raise a request for login to ADNI anc lcik on image collection
https://ida.loni.usc.edu/home/projectPage.jsp?project=ADNI

![image](https://user-images.githubusercontent.com/132141855/235603102-3ff52611-3b24-4f2c-bf15-5ca29184466a.png)

2. Use the filters as shown below to download the data
![image](https://user-images.githubusercontent.com/132141855/235603378-e25b4071-a6b1-434a-8ccb-fb7928e1ff92.png)

3. Download using advance option
![image](https://user-images.githubusercontent.com/132141855/235603972-8c26e410-5fb2-4dd0-b44d-d35a5f291b01.png)

![image](https://user-images.githubusercontent.com/132141855/235604047-cacd8ff6-4189-4030-a9a8-e0e71dc2f568.png)


4. Also download clinical dataset.

To download the clinical data, click on Download and choose Study Data. Select all the csv files which are present in ALL by ticking Select ALL tabular data and click Download.

![image](https://user-images.githubusercontent.com/132141855/235604438-6081019c-49db-4888-baeb-0a702401587c.png)

Select ALL- Select ALL tabular data 

![image](https://user-images.githubusercontent.com/132141855/235604848-2124613f-64be-4398-848c-04a33cbabe88.png)


5. Install python package clinica and dcm2niix
6. Run this command to convert the downloaded data to BIDS format data

#### clinica -v convert adni-to-bids 'ADNI_DATA_DIRECTORY' 'CLINICAL_DATA_DIRECTORY' 'BIDS_DIRECTORY' -m T1 --subjects_list subjects.txt
 
 subjects.txt to include list of subject ids
 
 Make sure the image folder for these subjects exist in ADNI_DATA_DIRECTORY and clinical data exists in CLINICAL_DATA_DIRECTORY various csv files such as ADNIMERGE.csv etc

Refer : https://aramislab.paris.inria.fr/clinica/docs/public/latest/Converters/ADNI2BIDS/

7. Install licensend MATLAB version on your machine
8. Install SPM and add path in matlab
9. add matlab in env path
export PATH=${HOME/TO/MATLAB}:${PATH}
10. set SPM_HOME path
export SPM_HOME= HOME/TO/SPM
11. Run this command to convert BIDS format data to t1-volume

For Train data : 

#### clinica run t1-volume 'BIDS_DIRECTORY_TRAIN' 'BIDS_PROCESSED_TRAIN' 'TRAIN' -tsv './Train_ADNI.tsv' -wd './WD_train' -np 2


TRAIN : is the group name lable. this is basically telling that use this as TRAIN set so that one of the internal step of dartel template creation will create the template using this data and save it as  groups/group-TRAIN/t1/group-TRAIN_template.nii.gz

When you run this preprocesss step for validation and test data , keep the group label as TRAIN so that the method refers to already created template to normalize the images.

For Val data : 

#### clinica run t1-volume 'BIDS_DIRECTORY_VAL' 'BIDS_PROCESSED_VAL' 'TRAIN' -tsv './Val_ADNI.tsv' -wd './WD_val' -np 2

For Test data : 

#### clinica run t1-volume 'BIDS_DIRECTORY_TEST' 'BIDS_PROCESSED_TEST' 'TRAIN' -tsv './Test_ADNI.tsv' -wd './WD_test' -np 2

here : first argument is the path to BIDS format image data
     : second argument is the destination path where the program will write the processed files
     : TRAIN is lable used for training set. when the file is not present, it will create the template.if it is present it will use the template and proceed further.
     : -tsv option to provide the diagonsis file containing details of respective data subjects.
     : -wd is to provide the path for working directory for intermediate steps.

Refer : https://aramislab.paris.inria.fr/clinica/docs/public/latest/Pipelines/T1_Volume/

12. Your data is now ready for trainng.

### Steps for Model training
1. Follow the notebook https://github.com/amitdodaiith/Visual_Computing_CNN_for_AD/blob/master/Model_Training.ipynb

### Steps for Model results
1. follow the notebook https://github.com/amitdodaiith/Visual_Computing_CNN_for_AD/blob/master/Model_Results.ipynb
