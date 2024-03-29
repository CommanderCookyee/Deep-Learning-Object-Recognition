# Deep-Learning-Object-Recognition
Generative Adversarial Networks (GANs) have become increasingly sophisticated in their ability to produce synthetic images that are indistinguishable from natural images. In this report, we propose a new method for determining the authenticity of these images by combining Convolutional Neural Networks (CNNs) with Gray Level Co-Occurrence Matrix (GLCM) texture features, Auto Encoders & Shannon Entropy. We have modified the GLCM algorithm to include Spatial Co-Occurrence Matrices in the RGB, RG, GB, and BR channels in addition to textural features. Additionally, we have also considered and developed experimental and hybrid models. The best model showed a 5% improvement in accuracy compared to previous models that only used CNNs. Additionally, the proposed method was also tested on a mobile application to assess the effect of rebroadcast images on accuracy.

In this report we proposed the tested method of including a modified version of GLCM or Gray Level Co – Occurrence Matrix combined with Convolutional Neural Networks or GLCM – NET as Stanford calls it in their paper on “Building a Neural Historical Art Classifier with GLCM Texture Features and Attention Feature Extraction”. However, unlike Stanford’s  model which only use the textural features like “Angular Second Momentum” or “Contrast” we would also be using the computed Co-occurrence Matrices on the RGB, RG , GB, BR channel as proposed by Nataraj, L., Mohammed, T. M., Manjunath, B. S., Chandrasekaran, S., Flenner, A., Bappy, J. H., & Roy-Chowdhury, A. K. (2019) on Detecting GAN Synthetic Fake Images using Co-occurrence Matrices. Electronic Imaging. We also consider the methodology of Hybrid Networks and other features extraction techniques such as Shannon Entropy on the RGB,RG,GB,BR channels.

### Final Model Structure

![image](https://github.com/CommanderCookyee/Deep-Learning-Object-Recognition/assets/107714889/4b581370-8556-4235-b07f-ab8b2ba167fe)

Hybrid modelling with ResNet152, GLCM/Spatial Co-Occurrence Matrices with MLP & Auto Encoders & Shannon Entropy

The architecture of this model consists of ResNet50 combined with GLCM Spatial Co-Occurrence features of the R,G,B,RG,GB,BR channels and an Auto Encoder. The features are then concatenated and fed into a dense layer to make the final predictions, as seen in the diagram. 
Auto Encoders are unsupervised Neural network that efficiently compress and encode data and reconstructs the data back from the encoded version to a representation as closed to that of the original. By design it reduces the dimensionality of data by learning how to ignore the noise in the data. 
The image below shows how and auto encoder works:
 
The idea is to use auto encoders to extract feature representations and compress them into a smaller dimension. This is in hopes of eliminating the possibility of the curse of dimensionality in the GLCM features extracted as there are 36 columns worth of data with only 3600 rows. 
Note: The "curse of dimensionality" refers to the fact that as the number of features or dimensions in a dataset increases, the amount of data required to generalize accurately to new examples also increases dramatically.

Our autoencoder model has a simple structure with two fully connected layers in the encoder and decoder parts. The input layer takes the 36 numerical features as inputs, and the output layer reconstructs the input features. The encoder part compresses the input features into a lower dimensional representation (in this case, 6 dimensions), and the decoder part reconstructs the original features from this compressed representation. This lower dimensional representation can be used as a feature extractor for another model, such as an FCN, which can then be trained to classify images.

