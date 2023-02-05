# Generating Adversarial Examples using FGSM

This project uses ResNet34 which has been finetuned on the STL-10 data set. There are four functions to create small perturbations in input images such that the model will misclassify the noised image. These functions use the Fast Gradient Sign Method (FGSM), which uses the sign of the gradient of the loss for an image to slightly adjust each pixel. FGSM is applied with single-step and iterative methods, each with a non-targeted and targeted version. 
 
