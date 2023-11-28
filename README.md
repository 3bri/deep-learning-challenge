# deep-learning-challenge

Brian Guenther

Title:  Deep Learning Model to aid charity funding decisions

Overview:
The nonprofit Alphabet Soup provided a database regarding charity funding outcomes for 34,000 different grants.  The purpose of this project was to develop a neural network that was trained on this data to predict if applicants will be successful when provided funding.  The goal of the model was an accuracy of greater than 75% correct on the test set.  In seeking to obtain this metric, three different approaches to the neural network we tried:  an initial neural network, using autotune to obtain an optimized network, and removal of data to reduce bias or extraneous information from the training set.

Results: 
•	Data Preprocessing for the final model
The target binary variable for the model is the ‘IS_SUCCESSFUL’ column from the database.  Representing whether an applicant was successful.
The features within the model were the following columns:  APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT, and ASK_AMT.
The following variables were removed from the input data because they are neither targets nor features:  'EIN', 'NAME', 'STATUS', and 'SPECIAL_CONSIDERATIONS'.  

The accuracy of the final model was 0.7261, assessed versus the test data.  So, the goal of obtaining an accuracy of 75% was not obtained at this time.

•	Compiling, Training, and Evaluating the Model
In the final model “relu” activation function was selected for both layers.  The relu function was chosen due to the expected non-linear nature of this problem.  Two layers were chosen with eight neurons in the first layer and five neurons in the second layer.  

The first deep learning model (Chal21_att1.ipynb) utilized the same activation function and layers as the final model and obtained a slightly lower accuracy of 0.7248.  Removal of extraneous information resulted in a small improvement in the accuracy.  The second attempt to improve the model (Chal21_att2autotune.ipynb) using autotuning allowed the tuner to choose between three activation functions ('relu','tanh','sigmoid') and between one and five layers with each layer containing between one and 10 neurons.  I was surprised by the result of no significant improvement of accuracy from top 3 models produced by the autotuning approach.  This indicated to me that issues with the data set were limiting the resolution of the model.  Therefore, I sought to remove superfluous information for the third attempt (Chal21_att3trim.ipynb).  This model was that was chosen as final model (AlphabetSoupCharity_Optimization.ipynb ) before running for a final time.

Summary: 
Overall, my attempts to improve on the accuracy of the initial model added less than 1% to the final accuracy.  This was independent of the activation function, number of layers, and number of neurons from the much larger range of possibilities sampled during autotuning.  This indicates to me that addressing improvements relate not with the neural network but require either more changes to the data set or a different deep learning approach.  I recommend going over the columns in the data set with the nonprofit Alphabet Soup as several of these columns may be redundant and biasing the model.  For example, AFFILIATION indicating sector of industry, CLASSIFICATION indicating Government organization classification (with a non-descript code value), and ORGANIZATION, may all be representing the same/similar information.  A greater understanding of these categories would aid in determining if they can be removed for the data.  Additionally, it might be beneficial to add information such as: region of country or urban vs. rural…   Another possibility to consider is the design of a more targeted deep learning model.  For example, the model should be limited to predictions for a more concise problem by such as an individual “USE_CASE” like healthcare or a bin of funding amount requested instead of the full range of granted requests.  These possibilities to improve the model remain to be explored.


Acknowledgements:  Aid provided by Kourt Bailey(tutor) regarding filtering/binning of ‘APPLICATION_TYPE’ and ‘CLASSIFICATION’.  Additionally, directions for saving the model as an HDF5 file were obtained from the following link: 
https://www.tensorflow.org/tutorials/keras/save_and_load . 
Otherwise, this project was accomplished based on information from class activities.
