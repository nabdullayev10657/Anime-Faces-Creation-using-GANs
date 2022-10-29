# Anime-Faces-Creation-using-GANs

GAN OVERVIEW
Past 2 decades have been memorized for huge innovations and revolutions in many fields of AI, and they have given root for today's newly emerging fields of modern AI and DL. In this sense, GANs have gained huge popularity and usage throughout last decades. GANs are mosly used to create images that do not exist in real world. It can be implemented in creating new datasets for further research in AI, creating human faces, new characters, and so on. 

PROJECT OVERVIEW
This project is designed to create (generate) anime pictures from scratch using Generative Adversarial Network (GAN). We should note that today there are some other GAN implementations that are working on this and similar datasets and also more advance versions are working on human face generation tasks. Considering huge demand and intensive research in this field, I hope my project will contribute to this process to some extend. I have tried to implement different variations of parameters (in the code) and tried to analyze how it affects to the whole scenerio visualizing loss and score graphs.

DISCRIMINATOR NETWORK IMPLEMENTATION
Discriminator Network is used to determine whether the picture is fake or not. Discriminator Network's main responsibility is to check whether the image comes from original source or it is artificially generated. Throughout the process, Discriminator will learn how to detect fake images better and better. In the network, convolutional layers and normalizers are following each other. As the actiovation function, I am using LeakyReLU simply because according to research and referencing to popular GAN implementations using only ReLU would lead to loose so much values while LeakyReLU keeps even negative values (cofficient = 0.15). At the end layer, sigmoid activation function is used because of using only 1 class. We will be getting either 0 or 1 after discriminator network layers.

GENERATOR NETWORK IMPLEMENTATION
Generator Network is used to generate and fool Discriminator Network. It takes the array and creates RGB pictures (in our case: [3, 64, 64]). In order to do that, it implements deconvolution operation (for more information, link is added to 'References' part). At the end, as an activation function, we are taking Tanh (hyperbolic tangent). That is because hyperbolic tangent activation returns the values in the range of [-1, 1] which perfectly matches with our initial tensor (we have brought this range in the very beginning of the implementation). 

GENERATOR & DISCRIMINATOR TRAINING (SEPERATE TRAINING)
Discriminator's training is based on creating random images (with generator network) and labeling them as 0, putting real images as labeling them as 1 and to make discriminator learn that how fake and real image should look like. Generator's training is based on calculating Binary Cross Entropy Loss between discriminator's predictedf labels and real labels of real images. So, generaotr will learn and every time it will create better and better images. Similarly, discriminator will learn how to differentiate fake and real images better and better time by time.

OPTIMIZERS
As an optimizer, I have taken Adam Optimizer and added hyperparameter betas (0.5, 0.9) because research showed that Adam optimizer and betas range works pretty well in GAN implementations (mostly). 

TRAINING WHOLE & LOSSES
After we are done with everything, we are ready to go with training the model. I used 20 epoches, 0.001 learning rate, CPU for running, 200 as batch size, 64x64 as image size. Running took almost 10 hours in my local machine. After fitting the model, I have printed graphical representation of the whole process. As can be seen from graphs, real scores is going to increase, and fake scores is going to decrease, which is something that we want to achieve.

LIMITATIONS
I could use more epoches and less learning rate to get better results, and also instead of CPU, GPU could have been used to reduce time and energy. Also loss function could be weighted loss to make the process more smooth. Because in that way, we would have better idea which network contributed the total loss to what extend and cofficients would also be used as hyperparameters. These can be further improved and might be future scope of this work.



References & Useful links:
https://medium.com/@marsxiang/convolutions-transposed-and-deconvolution-6430c358a5b6
https://www.baeldung.com/cs/sigmoid-vs-tanh-functions
https://www.kaggle.com/code/sachinrajput17/gans-for-anime-face-dataset
Jovian, Deep Learning with PyTrch: Zero to GANs
https://towardsdatascience.com/generating-anime-characters-with-stylegan2-6f8ae59e237b

