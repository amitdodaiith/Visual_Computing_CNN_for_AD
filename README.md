# Visual_Computing_CNN_for_AD

Follow this to download and process the data before it can be used for model training

1. Raise a request for login to ADNI anc lcik on image collection
https://ida.loni.usc.edu/home/projectPage.jsp?project=ADNI

![image](https://user-images.githubusercontent.com/132141855/235603102-3ff52611-3b24-4f2c-bf15-5ca29184466a.png)

2. Use the filters as shown below to download the data
![image](https://user-images.githubusercontent.com/132141855/235603378-e25b4071-a6b1-434a-8ccb-fb7928e1ff92.png)

3. Download using advance option
![image](https://user-images.githubusercontent.com/132141855/235603972-8c26e410-5fb2-4dd0-b44d-d35a5f291b01.png)

![image](https://user-images.githubusercontent.com/132141855/235604047-cacd8ff6-4189-4030-a9a8-e0e71dc2f568.png)


4. Also download clinical dataset.
5. Install python package clinica and dcm2niix
6. Run this command to convert the downloaded data to BIDS format data
7. Install licensend MATLAB version on your machine
8. Install SPM and add path in matlab
9. add matlab in env path
10. set SPM_HOME path
11. Run this command to convert BIDS format data to t1-volume
11, Your data is now ready for trainng.

Steps for Model training
1. Follow the notebook https://github.com/amitdodaiith/Visual_Computing_CNN_for_AD/blob/master/Model_Training.ipynb

Steps for Model results
1. follow the notebook https://github.com/amitdodaiith/Visual_Computing_CNN_for_AD/blob/master/Model_Results.ipynb
