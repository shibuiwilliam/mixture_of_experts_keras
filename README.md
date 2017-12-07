# Mixture of Experts on Convolutional Neural Network
Mixture of experts is a ensemble model of neural networks which consists of expert neural networks and gating networks. The expert model is a series of neural network that is specialized in a certain inference, such as classifying within artificial objects or within natural objects. The gating network is a discriminator network that decides which expert, or expers, to use for a certain input data, with importance of each expert.<br>
The mixture of experts can take one gating network, if only deciding an importance of experts, or multiple gating networks, to probabilistically split decision phases to hierarchical order, just like decision tree diagram.<br><br>
The expert models are pretrained to do only feed-forward inference in the mixture of experts model.
Training phase of the mixture of experts is to train the gating networks to improve decision making of which experts to use with weighted degree of importance of each experts.<br><br>
This notebook shows a way to use mixture of experts model with deep learning. The objective is to classify images, using Cifar10 and convolution neural netwok. The mixture of experts model takes hierarchical multiple gating networks, to first decide if the input image is artificial object or natural object. Then the next gating network decides importance of each expert models. There are three expert models:
basic VGG, which is trained to classify all 10 classes
artificial expert VGG, which is trained only to classify artificial objects, that have a label in 0, 1, 8 and 9
natural expert VGG, which is trained only to classify natural objects, that have a label in 2, 3, 4, 5, 6 and 7 

### The overview of the mixture of experts model
![0.png](./0.png)

