# Cardiac Device Identification

## Summary
This software repository is published as a supplementary material to the article "Open Access Data and Deep Learning for Cardiac Device Identification on Standard DICOM and Smartphone-based
Chest Radiographs" published in the journal "Radiology: Artificial Intelligence", Volume 6, Issue 4.

The software repository contains experimental Jupyter notebooks (`notebooks` folder) that demonstrate the process of pacemaker/biomonitor segmentation and classification on computed tomography data captured using smartphone cameras. These notebooks provide examples of how to implement algorithms to identify and segment pacemaker devices in medical images, as well as classify the type of pacemaker.

Moreover, the notebooks also showcase the potential for developing smartphone applications that could expedite the process of device model identification during emergency patient arrival. This feature could be particularly beneficial for hospitals and medical facilities looking to improve their patient care services.

The notebooks in the repository can serve as a valuable starting point for developing applications based on the published dataset.

The repository also contains a simple demonstration app (`demo_app` folder) that allows to use the models in the paper, packaged in docker container form.

## Contents

As discussed in the article, the goal of the algorithms is to classify manufacturer and model of the cardiac device based on the image in common (.jpg, .png) format. There are 2 key stages.
In the first stage, the input image is segmented to localize the device. In the second stage, the localized image of the device is classified in terms of device manufacturer and model. 

* The notebook `01_segmentation.ipynb` demonstrates the training process of the segmentation network as well as it's usage for generating image crops used for classification.
* The notebooks `02_fastai_classification_manufacturer.ipynb` and `03_fastai_classification_model.ipynb` demonstrate the training process of the manufacturer and device classification networks, respectively, sample results on the validation sets using fastai and the procedure to generate confidence results. Final results are demonstrated in the paper.
* The notebook `04_additional_data_experiments.ipynb` demonstrates the evaluation of the trained models using the dataset published alongside `Cardiac Rhythm Device Identification Using Neural Networks` by Howard et al. 

The data used in the notebooks is submitted and to be published on PhysioNet (as of 2024.07.18). Depending on the format the data is made accessible with, metadata files used in the notebooks may not be usable and therefore are not published here. The metadata files are designed according to the fastai Dataloader input format with columns specifying image path in the host system, validation split and class to train and infer. 

The sample demonstration app uses the trained models and allows to predict the manufacturer and device present on the input image. It utilizes docker container infrastructure and can be run using the `docker build` and `docker compose` commands on a machine with at least 8 GB of RAM. The trained model parameters are downloaded from Zenodo (https://zenodo.org/record/10955502) on container building stage. When the containers are running, the frontend app with simple image submission interface is hosted on port 8050 of the local machine. 

