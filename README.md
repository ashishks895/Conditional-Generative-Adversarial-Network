# Conditional-Generative-Adversarial-Network
Conditional Generative Adversarial Networks (cGAN) are a class of generative models that extend the capabilities of traditional GANs. 

cGANs introduce conditional information, allowing the model to generate data samples conditioned on specific input data or labels. 
In the context of image generation, cGANs take a label or additional information as input and generate corresponding images. 

In this project, we explore the implementation and training of a cGAN for generating images. Here is an image which shows the architectural difference between GAN and cGAN. 

![image](https://github.com/ashishks895/Conditional-Generative-Adversarial-Network/assets/83638970/4afb2cc5-d58b-43ac-a38f-e96289246744)

SET OF EXPERIMENTS PERFORMED 
Discriminator Model 
We defined a discriminator model as follows: 
• Input: Image (28x28 pixels) and label (categorical input) 
• Additional label information is embedded using an embedding layer. 
• The label information is then reshaped to match the image size. 
• The image and reshaped label information are concatenated to create a merged input. 
• Two convolutional layers with LeakyReLU activation and downsampling are used. 
• The feature maps are flattened and passed through a dropout layer. 
• A dense layer with a sigmoid activation outputs a binary classification result (real or fake). 

Generator Model 
We defined a generator model as follows: 
• Input: Random noise (latent space) and label (categorical input) 
• Additional label information is embedded using an embedding layer. 
• The embedding is linearly transformed and reshaped to match the generator's initial shape (7x7 pixels). 
• A foundation for a 7x7 image is created with dense layers and LeakyReLU activation. 
• The generated image is merged with the label information. 
• Two transposed convolutional layers upsample the image to 28x28 pixels. 
• The output is a generated image with pixel values in the range [-1, 1]. 

Combined GAN Model 
A GAN model is created to link the generator and discriminator. The discriminator's weights are 
frozen, and the generator's outputs are fed into the discriminator. This combined model is used 
to train the generator. 

Training 
We performed the following experiments during training: 
• Varied the number of epochs for training (hyperparameter). 
• Used a batch size of 128 (hyperparameter). 
• Used the Adam optimizer with a learning rate of 0.0002 and a beta of 0.5. 
• Employed binary cross-entropy loss for both the discriminator and generator. 
• Applied dropout (with a rate of 0.4) for regularization in the discriminator. 
• Rescaled real images to the range [-1, 1]. 

