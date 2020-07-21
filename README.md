# Near-field Acoustic Holography analysis with Convolutional Neural Networks
Repository of "Near-field Acoustic Holography analysis with Convolutional Neural Networks"

M. Olivieri, M. Pezzoli, R. Malvermi, F. Antonacci, A. Sarti

Near-field Acoustic Holography (NAH) enables the contactless analysis of the vibrational field on plates and shells from the acoustic data captured in proximity of the vibrating object.<br>
We propose a data-driven approach to NAH by using a Convolutional Neural Network (CNN) that predicts the vibrational field on the object from the acoustic pressure field captured by a microphone array deployed in its proximity.<br>
We have conducted an extensive simulation campaign on rectangular plates of different dimensions, boundary conditions and mechanical properties. This dataset has been generated using Finite Element Method simulation for predicting both vibrational and acoustic pressure fields.<br>
The proposed architecture is able to predict the normal velocity on the structure surface by means of contactless acoustic measurements.
Results have highlighted great performances over a broad frequency range with respect to Normalized Mean Square Error and Normalized Cross Correlation. 
Moreover, we investigated the robustness of the estimate against input data affected by additive white noise and error on microphone positioning.
Therefore, this solution enables to infer useful properties from data by encoding them in an optimal feature representation learned by the network.

## Proposed architecture
The adopted model is inspired by the architecture of the renowned UNet. <br>
This architecture consists of three main components: the contraction, the bottleneck, and the expansion sections.
The contracting component, also known as encoder, is designed to extract a feature map from input. This latent representation obtained in the encoding phase is located at the bottleneck. In the expansion section, also known as decoder, the network exploits the embedding at the bottleneck to provide the desired output. <br>

The proposed encoder consists of a series of four dowsampling blocks. Each block includes two consecutive layers of 2D convolutions with filter size 3x3, each followed by a Rectified Linear Unit function (ReLU). After each block, a 2x2 max pooling operation is applied to achieve the compression. 
The downsampling starts with 16 extracted features and we double the number of feature channels at each step.
Therefore, we reach 256 features at the innermost layer, thus representing the information with a structure of 1x4x256. <br>

Every step of the proposed decoder operates an "up-convolution" by means of a Conv2DTranspose layer with stride 2x2. 
The skip connections between each downsampling block and its corresponding upsampling layer enable the reuse of the encoded features in the decoding process.
Moreover, two 3x3 convolutions with ReLU activations follow each upsampling step.
In this way, the decoder has also a large number of feature channels, which allow the network to propagate context information to higher resolution layers.
As a consequence, the decoder is more or less symmetric to the encoder, and yields a u-shaped architecture. <br>

The detailed structure of the proposed CNN is depicted below. The input and the output of the network are depicted in grey and blue, respectively

![alt text](https://github.com/polimi-ispl/nah-cnn/blob/master/images/UNet_architecture.png)

## About the code
The repo code is structured in the following folders:
* _"src"_ contains the following scipts:
  * _"uNetArchitecture.ipynb"_ contains the proposed architecture.
  * _"example.ipynb"_ contains a complete explanation for using the architecture. In particular you can find the test phase in different boundary conditions scenarios.
* _"data"_ contains the weights to test the trained model and the acoustic pressure measurements and velocity ground truth per each boundary conditions to use in the _example.ipynb_ file.

All the code file are given as Notebook files in order to provide complete explanations of the code.
Scipts are exportable in Python languages and the installation of the following modules is required:
* numpy
* tensorflow
* keras
* sklearn
* pickle (for reading and writing files such as datasets and saved models)
* matplotlib.pyplot (for data visualization with plots)
