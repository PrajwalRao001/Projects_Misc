# COVID-19 Detection using chest x-ray images

## Inspiration and Intuition

* COVID-19 detection has been one of the most tedious tasks with chest x-rays and lab tests, especially the latter costing a lot and taking a long time for results to confirm .
* Many a times without the test results, patients' treatment may get delayed which may lead to worsening of condition if they do have the virus.
* Even if other lab tests can't be available on the go, the soft copy of a chest x-ray is readily available and the doctors can use it to detect primary sources of congestion in the lungs.
* The COVID-19 Detection aims to automate this process and help reduce the time and resources spent on tests and sometimes even help give a second opinion to the doctor's analysis.


## Log

* A CNN test model to detect whether a given patient's chest x-ray was congested or not was tried out using keras module on the Google collabs platform. (link: https://colab.research.google.com/drive/1zbgg_ee3cOcKe7c2I1XwEx_gkTcnboLp?usp=sharing)
	* The dataset was created as follows:
		* For positive case images, this github repository with chest x-ray images of congested lungs with many kinds of diseases along with some metadata was used : https://github.com/ieee8023/covid-chestxray-dataset
		* For negative case images, a kaggle dataset with normal chest x-ray images from a pneumonia challenge was downloaded from this link : https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia
		* From the positive case images, a set of only the front view or PA view images with the COVID-19 tag where extracted and labelled.
		* These images were mixed with a random labelled set of negative case images.
		* This mix was divided into training and test sets forming the dataset to test different models on.
	* The CNN was built with this YouTube video as reference (the dataset used there was also extracted from the same links mentioned above): https://www.youtube.com/watch?v=nHQDDAAzIsI
	* The CNN was built and its accuracy was sub-par : it wasn't doing well in detecting COVID-19 (a lot of False Negatives). The hyperparameters and the structure was tweaked and different combinations were worked on. But the lack of in-depth knowledge of how these parameters affect the network meant that the tweaks were ultimately useless.
	* The model managed to procure excellent results in detecting negative case images however (very few False Positives).
	* This approach has been put in the shelf until we have a tighter grasp over the concept.
	* Note/Observation: 
		* The ratio of positive to negative cases in the final dataset was 1:4. The large number of negative cases that too in that ratio may have been a reason for the better performance of the model in detecting the negative cases effectively. Next time, more postive cases should be taken and the ratio of the classes should be 1:1.
		* All of this is being done without expert consultation from someone in the medical industry, so any results however effective can be deemed void if not feasible according to experts.



* The CNN model barely gave any insights as to how the features were extracted from the dataset. Also to get better results, we had to train more complex models which seemed inefficient. We wanted to learn what features we needed to concentrate on so that we can use some filters that concentrated on said features. We also noticed a lot of noise in the dataset like images having random markers on them, items like earphones, phones, etc appearing on the chest x-rays and wanted to filter it out giving us a chance to probably do better with simpler models. So we shifted to extracting features from the dataset.
	* The weka tool provides some simple image filters that can differentiate needed features pretty well and in a faster and easier manner. Of all the experimentation that can be done, we felt that this platform was good to start our work with.
	* We shrunk the dataset created for the CNN model and further cleaned it and modified it. We wrote a python code that generated the data part of the arff file which is weka compatible and created respective arff files for test and train data.
	* We opened the files on weka and applied different image filters to it and tried different simple classification algorithms on it.
	* Observations:
		* The results came out better than expected but the problem of False Negatives still persisted. With more experimentation involving cost-sensitive classification and better classifier options however, we can clear this problem.
		* Weka is more of an experimentation tool that works best with smaller datasets. It can say how good a classification can be, but replication of results into the CNN model will be a challenge.
		* weka provides limited number of image filters and even details of these filters are limited. We should explore them separately in detail and learn more about them to actually make sense of it.
		* All of this is being done without expert consultation from someone in the medical industry, so any results however effective can be deemed void if not feasible according to experts.


* Currently we are learning about different filters and noise reduction using R-wavelet transforms among other techniques to see if any can be applicable to our case.
