# Impression-Generation-From-X-Ray-Images
#### Generating Medical Reports of Chest X-Rays Using Encoder-Decoder Model and Attention Mechanism.
## Business Problem
Clinical imaging captures enormous amounts of information but most radio-logic data are reported in qualitative and subjective terms. X-Rays are a form of Electromagnetic Radiation that is used for medical imaging. Analysis of X-ray reports is a very important task of radiologists and pathologists to recommend the correct diagnosis to the patients. In this project, we are tackling the image captioning problem for a data set containing Chest X-ray images with the help of the state of the art deep learning architecture and optimizing parameters of the architecture.

The problem statement here is to find the impression from the given chest X-Ray images. These images are of two types: Frontal and Lateral view of the chest. With these two types of images as input we need to find the impression for given X-Ray. To resolve this problem statement, we will be building a predictive model which involves both image and text processing to build a deep learning model.
## File Structure
1. [EDA](https://github.com/Kundan-jha/Impression-Generation-From-X-Ray-Images/blob/main/CS2_EDA%26Preprocessing.ipynb)
2. [Basic Model](https://github.com/Kundan-jha/Impression-Generation-From-X-Ray-Images/blob/main/CS2_Basic_model.ipynb)
3. [Attention Model](https://github.com/Kundan-jha/Impression-Generation-From-X-Ray-Images/blob/main/CS2_Attention.ipynb)
4. [Inference (Final)](https://github.com/Kundan-jha/Impression-Generation-From-X-Ray-Images/blob/main/CS2_Final.ipynb)
5. [Deploy Model](https://github.com/Kundan-jha/Impression-Generation-From-X-Ray-Images/blob/main/CS2_Deploy.ipynb)
## My Approach – Solution
Initially I will be doing the EDA and Preproccesing of the data with image as input and text as output. I could find the data imbalance, Images availability per patient, Type of images associated for each patient. After this step I will be implementing deep learning model with two different approach to find the improvement on one another.

1. The basic model: A simple encoder and decoder architecture. In encoder part it will have the CNN single fully connected layer to get the feature vector of images from pretrained CheXNET model. CheXNET Model is a Denset121 layered model which is trained on 112,120 number of chest x-ray images for the classification of 14 diseases. Decoder part will be having LSTM layer where it takes two inputs one is image feature vector and the sequence of text to word in each time step.

2. Main Model: I will be using encoder-decoder architecture to generate the impression from the chest X-ray. The encoder will output the image feature vectors. The feature vectors are then passed to decoder with attention mechanism this will generate the next word for the content of the image.

As initial step, I will use CheXNET model weight in Encoder feature extraction. Encoder: The encoder is a single fully connected linear model. The input image is given to CheXNET model to extract the features. this extracted feature of two images are added and input to the FC layer to get the output vector. This last hidden state of the Encoder is connected to the Decoder. Decoder: For the decoder, I have created a one_step_decoder layer which takes in decoder_input, the encoder_output and state value. The decoder_input will be any character token number. This will be passed through the embedding layer and then embedding output and the encoder_output will be passed through the attention layer which will produce the context vector. The context vector will then be passed through the RNN (here GRU will be used) with the initial state being that of the previous decoder. I have used dropout layers for tuning and regularization of model. The decoder calls the one-step attention layer for each of the decoder time-steps and computes the scores and attention-weights. The outputs from each decoder step are the next word in the sequence. Detailed Architecture is mentioned below.
![Screenshot (221)](https://user-images.githubusercontent.com/50130996/121775631-7bfb2b80-cba6-11eb-8cf9-efab405d47c3.png)

If you have made it till now, It seems you are really intrested in this case study! Then do checkout my blog where I have explained every step of my approach for solving this case study.

Blog link : [Impression Generation From X-Ray Images — Case Study](https://kundan-jha.medium.com/impression-generation-from-x-ray-images-case-study-341d25af6edf#0535-6053f58966b1)

You can see the deployment part below :

[](https://user-images.githubusercontent.com/50130996/121776317-ce8a1700-cba9-11eb-8a47-500ebd3d7d8a.mp4)

YouTube link : https://youtu.be/V-eDn6c_S08

Feel free to play with codes, If you have a crazy idea, then pull request :)
