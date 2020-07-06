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
