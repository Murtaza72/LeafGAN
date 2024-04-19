# Data Augmentation using Generative Adversarial Networks

We have used GAN to generate fake diseased images of plants. The architecture of model of GAN used here is CycleGAN, which takes healthy(datasetA) and diseased(datasetB) plant images and tries to convert them into each other as A -> B, B -> A.

LeafGAN is an implementation of CycleGAN, which tries to address some issues related to CycleGAN. One the major drawbacks of CycleGAN is its difficulties with the background of the plant images. The background of the image dataset we have used in this project is very consistent as they were taken in the lab environment. As a result, CycleGAN is not very efficient in creating varying backgrounds for the generated images.

The solution to this problem is using only the relevant part of the leafs using a image segmentation neural network, classifying it into 3 categories:
1. Full Leaf
2. Partial Leaf
3. Non Leaf

The main point to be noted here is of partial leaf, which just extracts plants leaf region and discards the other parts. This has a considerable effect on the output when compared against CycleGAN.

More on the LeafGAN paper can be found [here](https://arxiv.org/abs/2002.10100).

We get fake diseased plant images (and fake healthy as well) from the output of this model.

# Failures
The Aim of this project was to generate fake diseased plants images, which can be used for training of image classification models.

Our failure in this project was that, we tried to bite more than we could chew. We took a large dataset with varying plant diseases and species, which resulted in large number of classes when using the generated images with the image classifier.

For a small scope project like this, we could have taken a particular disease for a single species which would reduced the number of classes, the classifier had to work with.

As it is the case with every software project, we had changes in plan, and reduced the scope of project, to just classify the images into healthy and diseased(infected).

# Difficulties
One the major difficulties, we had to face was of hardware. As we are students and don't have access to high-end GPU's to train these beasts of models, we had to take help of google colab which disconnects after every 6 hours in the free tier.

# Usage

### It is recommended to run this script in Google Colab as it was developed on that platform and has workarounds for the runtime disconnection

1. Download the images.zip [here](https://drive.google.com/drive/folders/1GtbeJWkFxoYc-Q_YchgrzR-NOWKGiXwY?usp=sharing).
2. Upload the images.zip file into your google drive in a folder named AIES
3. Run the script until the training of the model
4. If the runtime disconnects, repeat above steps
5. When the model is sufficiently trained, we can run the rest of the script as usual

**Caution:** GAN's(CycleGAN) are very complex models and require large amount of hardware resources and takes lots of time for an accurate result.