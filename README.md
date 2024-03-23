# Generating Adversarial Examples using FGSM

This project uses ResNet34 which has been finetuned on the STL-10 data set. There are four functions to create small perturbations in input images such that the model will misclassify the noised image. These functions use the Fast Gradient Sign Method (FGSM), which uses the sign of the gradient of the loss for an image to slightly adjust each pixel. FGSM is applied with single-step and iterative methods, each with a non-targeted and targeted version. 

We find that these methods are quite effective, with a slight caveat - one needs to have access to the classification model in order to generate these adversarial inputs. Below are confusion matrices showing the performance of the model on clean images, FGSM-perturbed images, and targeted iterative FGSM-perturbed images. The rows are true class and the columns are predicted class.

Confusion Matrix for Clean Images:
|     | *0* | *1* | *2* | *3* | *4* | *5* | *6* | *7* | *8* | *9* |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| *0* |  128  |  1  |  3  |  13  |  3  |  0  |  0  |  0  |  3  |  4  |
| *1* |  7  |  112  |  1  |  39  |  14  |  4  |  1  |  0  |  2  |  0  |
| *2* |  1  |  0  |  140  |  5  |  1  |  0  |  0  |  0  |  0  |  4  |
| *3* |  1  |  2  |  0  |  148  |  12  |  3  |  1  |  0  |  0  |  0  |
| *4* |  2  |  5  |  1  |  22  |  117  |  0  |  3  |  0  |  1  |  0  |
| *5* |  1  |  1  |  2  |  95  |  23  |  26  |  4  |  3  |  0  |  0  |
| *6* |  1  |  2  |  1  |  44  |  32  |  6  |  67  |  0  |  2  |  1  |
| *7* |  0  |  13  |  2  |  88  |  15  |  6  |  0  |  44  |  1  |  0  |
| *8* |  6  |  1  |  2  |  5  |  0  |  0  |  0  |  0  |  129  |  0  | 
| *9* |  1  |  1  |  24  |  9  |  1  |  0  |  0  |  0  |  12  |  104  | 

Confusion Matrix for FSGM-perturbed Images:
|     | *0* | *1* | *2* | *3* | *4* | *5* | *6* | *7* | *8* | *9* |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| *0* |  33  |  9  |  20  |  39  |  12  |  2  |  0  |  1  |  17  |  22  |
| *1* |  18  |  5  |  3  |  89  |  34  |  18  |  3  |  6  |  3  |  1  |
| *2* |  14  |  5  |  25  |  38  |  6  |  3  |  0  |  4  |  6  |  50  |
| *3* |  2  |  29  |  11  |  2  |  98  |  11  |  4  |  9  |  1  |  0  | 
| *4* |  6  |  15  |  7  |  100  |  3  |  7  |  9  |  0  |  1  |  3  | 
| *5* |  0  |  1  |  5  |  98  |  41  |  0  |  5  |  5  |  0  |  0  |
| *6* |  1  |  4  |  4  |  94  |  50  |  1  |  0  |  0  |  2  |  0  |
| *7* |  0  |  18  |  3  |  111  |  30  |  3  |  3  |  0  |  1  |  0  |
| *8* |  45  |  3  |  24  |  32  |  3  |  2  |  0  |  0  |  3  |  36  | 
| *9* |  9  |  5  |  68  |  29  |  4  |  2  |  1  |  1  |  31  |  2  |

Average SSIM: 0.966

Confusion Matrix for Targeted Iterative FGSM-perturbed images:
|     | *0* | *1* | *2* | *3* | *4* | *5* | *6* | *7* | *8* | *9* |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| *0* |  155  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
| *1* |  180  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
| *2* |  151  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
| *3* |  166  |  0  |  1  |  0  |  0  |  0  |  0  |  0  |  0  |  0  | 
| *4* |  151  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  | 
| *5* |  155  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
| *6* |  156  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
| *7* |  169  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |
| *8* |  148  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  | 
| *9* |  152  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  |  0  | 

Average SSIM: 0.958
 
