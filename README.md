# ML_Pneumonia_Detection
phase 4 final project

# Introduction

**Disclaimer**

**This project was completed for educational purposes only. Do not consider any of this as medical advice**

My objective with this project was to be able to use X-rays from pediatric patients to be able to identify whether or not the patient has pneumonia. I accomplished this task using deep learning and transfer models

My business case was to be able to quickly scan through a large amount of X-Ray images and be able to flag cases that were extremely likely to have Pneumonia to be able to more rapidly get them treatment. Given the limited data and limited time to work on this it was extremely unlikely to get a model that would be able to consistently outperform a doctor on diagnosis. This is only intended to be used as an aid for doctors to try and increase speed of diagnosis.

Traditionally with medical cases you want to optimize for recall, as reporting a false negative (someone does not have pneumonia when they actually do) will likely be a worse outcome than a false positive (prescribing treatment to a healthy person). In my business case I chose to optimize precision to try and create a system that could be very confident in it's prediction and be able to quickly get the patient treatment.

As this was run on my personal work computer, some elements (such as number of epochs) have been reduced in some models to reduce time spent modeling. This can reduce model accuracy in some cases.


# Dataset

The data is not included in my github repository as it exceeds upload limits. To download the dataset you can visit [Kaggle](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia) 
Or for a larger version of the dataset visit [Mendeley](https://data.mendeley.com/datasets/rscbjbr9sj/3) 

If you want to run the notebook you will need to change the download paths to where your files are located (this is mentioned in the notebook where you need to change it)

The dataset contains 5,863 X-Ray images (JPEG) that are split into 2 categories (Pneumonia/Normal), the dataset is highly unbalanced with more normal cases being represented. For each category the images are split into 3 folders (train, test, val) with Pneumonia/Normal cases appearing in all folders
Chest X-ray images (anterior-posterior) were selected from retrospective cohorts of pediatric patients of one to five years old from Guangzhou Women and Children’s Medical Center, Guangzhou. All chest X-ray imaging was performed as part of patients’ routine clinical care.
For the analysis of chest x-ray images, all chest radiographs were initially screened for quality control by removing all low quality or unreadable scans. The diagnoses for the images were then graded by two expert physicians before being cleared for training the AI system. In order to account for any grading errors, the evaluation set was also checked by a third expert.

# Modeling
As there was limited data my main focus was on transfer models. I did some baseline models and experimented with a few things but quickly moved onto testing three transfer models (VGG16, VGG19, and Xception). All of these models were created for the Imagenet classification competition. For more information visit this [link](https://dl.acm.org/doi/10.1145/3065386) 

# Evaluation
<img src="https://github.com/DivisiBULL/ML_Pneumonia_Detection/blob/main/Imgs/classification%20report%20pneumonia%20detection.PNG">

The model was able to generalize decently well. Precision on the 1 label (pneumonia) is what I optimized the model for. The model was able to get a .64 precision score on the 1 label (pneumonia). Given the business case, this model was able to perform pretty well. 

Traditionally with medical cases you want to optimize for recall, as reporting a false negative (someone does not have pneumonia when they actually do) will likely be a worse outcome than a false positive (prescribing treatment to a healthy person). In my business case I chose to optimize precision to try and create a system that could be very confident in it's prediction and be able to quickly get the patient treatment.

The model was only ever intended to be used as an aid to qualified doctors, to be able to help quickly identify a large number of cases of pneumonia cases. Which will allow for faster starts to treatment and recovery. The doctors will still have to manually go through each case to ensure accuracy.


# Conclussion

We all know even the best doctors can make mistakes. Humans can’t be right 100% of the time. But it can be hard to compare percentages between the two. There is not widespread data on doctors accuracy in pneumonia diagnosis. There are a few peer reviewed cases but they are only on a few hundred cases. So I don’t know if the average doctor correctly identifies pneumonia better or worse than the model. 
This model is still only intended to be able to aid doctors in Pneumonia screening, not replace them. 

There is also limited data on the error rates of doctors making it difficult to have a evaluation metric to aim for. I will include two links [link](https://pubmed.ncbi.nlm.nih.gov/18299488/) and [link](https://pubmed.ncbi.nlm.nih.gov/15759443/) to publications on this matter. But neither of them are that large of a scale of analysis and do not provide a concrete average error rate.


# Repo Structure

| Imgs - A folder that stores imgs which are used in the README

| PowerPoint - An accompanying powerpoint presentation

| Notebook - The main bulk of the project. Contains all the code and explanations throughout
