# Mixture of Experts on Convolutional Neural Network
Mixture of experts is a ensemble model of neural networks which consists of expert neural networks and gating networks. The expert model is a series of neural network that is specialized in a certain inference, such as classifying within artificial objects or within natural objects. The gating network is a discriminator network that decides which expert, or expers, to use for a certain input data, with importance of each expert.
<br>
The mixture of experts can take one gating network, if only deciding an importance of experts, or multiple gating networks, to probabilistically split decision phases to hierarchical order, just like decision tree diagram.
<br><br>
The expert models are pretrained to do only feed-forward inference in the mixture of experts model.
<br>
Training phase of the mixture of experts is to train the gating networks to improve decision making of which experts to use with weighted degree of importance of each experts.
<br><br>
This notebook shows a way to use mixture of experts model with deep learning. The objective is to classify images, using Cifar10 and convolution neural netwok. The mixture of experts model takes hierarchical multiple gating networks, to first decide if the input image is artificial object or natural object. Then the next gating network decides importance of each expert models. 
<br><br>
There are three expert models:<br><br>
basic VGG, which is trained to classify all 10 classes <br>
artificial expert VGG, which is trained only to classify artificial objects, that have a label in 0, 1, 8 and 9 <br>
natural expert VGG, which is trained only to classify natural objects, that have a label in 2, 3, 4, 5, 6 and 7 <br>
<br>
<br>
<br>
## The overview of the mixture of experts model
![0.png](./0.png)
<br>

The first gating network, that decides which way to take, artificial or natural, is a pretrained VGG neural network, to classify the input data.
<br><br>
The second gating network layer, consists of two gating networks, decides the importance of each experts. <br>
The artificial gating network flows classification job to artificial expert VGG and base VGG, only activated when the first gating network decided the input data is an artificial object. 
<br>
The natural gating network flows classification job to natural expert VGG and base VGG, only the first gating netword decided as a natural object.
<br><br>
The classification output is a sum of softmax of expert VGG and base VGG, with importance from previous gating network multiplied.
<br><br>
For instance, if the input image is a cat, then the first gating network identifies it is a natural object, routing to the natural gating network in the second layer gating. The natural gating network predicts importance of expert networks, base VGG and natural expert VGG, in softmax probability. The expert networks infers the image class in softmax, and each of them is multiplied by the importance to finally output the inference.
<br>
The routing of the gatings are as follows:
<br>
![5.png](./5.png)
<br>
The notebook uses Keras with Tensorflow backend to implement the mixture of network model for classifying Cifar10.
<br>
The Cifar10 consists of 10 classes of images, with label of each class representing the following.
<br><br>
0 airplane <br>
1 automobile <br>
2 bird <br>
3 cat <br>
4 deer <br>
5 dog <br>
6 frog <br>
7 horse <br>
8 ship <br>
9 truck <br>

## The mixture of experts neural network
![model.png](./model.png)


