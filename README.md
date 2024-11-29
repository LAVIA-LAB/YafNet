# YafNet
Efficient Multi-Script Identification using Deep CNN

The major contributions of developing a CNN from scratch for script identification include end-to-end training tailored to the task, ensuring feature extraction directly from the input data without external aids. This approach highlights the model's ability to handle class imbalance and provides a robust baseline without relying on pretrained models, ensemble methods, or post-processing. Additionally, it showcases the adaptability and scalability of a purely data-driven CNN architecture for future research and applications.

## **1- Methodology**

To implement a Convolutional Neural Network (CNN) from scratch for script identification, we follow these detailed steps, which are organized into various phases to ensure clarity and effectiveness.
### **1.1 Preprocessing:** 
The first step is to convert the images into a format suitable for CNN processing. This typically involves resizing the images to a uniform size to ensure consistency in input dimensions. Additionally, it is important to normalize the pixel values to a range between 0 and 1. This can be achieved by scaling the pixel values from their original range (0-255) to a range of 0-1.
### **1.2 - Define the CNN Architecture:**
The proposed Deep CNN is composed of several types of layers stacked together to extract and learn features from the input images. The first type of layer is the Convolutional Layer, which applies convolution operations to the input images using filters. These filters slide over the input data to extract features such as edges, textures, and patterns. Each filter produces a feature map that highlights specific aspects of the input image. Next, Batch Normalization Layers are used to normalize the outputs of the convolutional layers. This helps to speed up the training process and provides regularization, which can improve the
model&#39;s performance. The Rectified Linear Unit (ReLU) activation function is then applied, introducing non-linearity to the model. This enables the model to learn more complex patterns by transforming the inputs into more useful representations.
MaxPooling layers are used to reduce the spatial dimensions (height and width) of the feature maps. This reduction helps to keep the most important features while decreasing the computational load and the risk of overfitting. Finally, the Flatten layer converts the 2D feature maps into a 1D vector, which is necessary before feeding the data into fully connected (dense) layers. These fully connected layers
are used to perform the final classification based on the features extracted by the convolutional layers. The final dense layer uses a softmax activation function to output probabilities for each class, indicating the model's prediction confidence for each script.
### **1.3 Compile and Train the Model:**
In this step, we use an optimizer like Adam, which adapts the learning rate during training to speed up convergence and improve performance. The batch size, which is the number of samples that will be processed before updating the model's internal parameters, and the number of epochs, which is the number of complete passes through the training dataset, are
defined in this step. By these steps, we can build an effective CNN for identifying different scripts in images, ensuring high accuracy and robust performance.
![YafNet Model.]([https://myoctocat.com/assets/images/base-octocat.svg](https://drive.google.com/file/d/1u2_RgT_1Xp-TvkiWH5cvDYzpaULdDSWV/view?usp=drive_link))
## **2- Dataset**
In this paper, we evaluated our method using the SIW 2021 Competition dataset [https://www.dropbox.com/scl/fi/val6l6sfrfpqeptmnrnv4/Multiscript_SIW_Database_Feb25_acceptedPaper.zip?rlkey=zbmf4bmvifn1q3ot7tp2jg0pe&e=1&dl=0] for script identification. This dataset includes a large number of words extracted from text images of both handwritten and printed documents. The dataset consists of word images from 13 different scripts: Arabic, Bengali, Gujarati, Gurmukhi, Devanagari, Japanese, Kannada, Malayalam, Oriya, Roman, Tamil, Telugu, and Thai.
## **3- Experiments**
For YafNet, we adopted the Adam optimizer with a learning rate of 0.001 and trained it for 100 epochs with a batch size of 32. To examine the effect of input image size on our model, we evaluated the same model at size: 112x112 pixels. 
For data augmentation, we applied various transformations to the text images, including rotation, shear, and zoom.
For external data, we extracted a word-level dataset from PHDIndic_11 and BN-HTRd . The dataset includes eight classes: Bangla (6,331 words), Oriya (4,993 words), Roman (2,200 words), Gurmukhi (914 words), Telegu (525 words), Devanagari (481 words), Tamil (361 words), and Kannada (272 words). For the Gurmukhi printed script, we additionally made a dataset of 4,037 words from internet documents. These datasets have been added to the training set.
Table 5 shows YafNet's performance across various tasks—handwritten, printed, and mixed scripts—with data augmentation (DA) and external datasets (ED). YafNet with both DA and ED achieves strong baseline performance in all tasks, with 96.03% for handwritten, 99.52% for printed, and 97.73% for mixed scripts  

|Proposed method............|  Metric..................|Task 1 (Handw)|Task 2 (Pinted)|Task 3 (Mixed).|
-------------------------------------------------------------------------------------------------------------------------------
|YafNet using DA and ED.| CCA.......................|96.03%..............|99.52%...........|97.73%.........|
-------------------------------------------------------------------------------------------------------------------------------
|YafNet using DA and ED.| F1 Score...............|96.33%...............|99.53%...........|97.73%.........|
-------------------------------------------------------------------------------------------------------------------------------
|YafNet using DA and ED.| BA.........................|92.85%...............|99.69%...........|97.93%.........|
-------------------------------------------------------------------------------------------------------------------------------
|YafNet using DA and ED.| ROC AUC Score.|99.65%...............|99.99%...........|99.97%.........|
-------------------------------------------------------------------------------------------------------------------------------
