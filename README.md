# Investigation of Vision Models

<div align ="center">
 <img src="https://github.com/Mehul0x/Expected-Calibration-Error-for-Vision-Models/assets/146676085/e88c5915-dba0-4754-8888-90e90b40620c" >

  
</div>

Vision Models learn "shortcuts", i.e. easily learnable features instead of actual visual cues, this causes the non-transferability of the models, i.e. they aren't practical to use in a real-world scenario.
Some of this model's issues can be related to miscalibration, when a model’s confidence in its predictions does not align with actual accuracy.  For example, if the model predicts some inputs to be 90% confident, does the actual accuracy be 90%?

This can be measured using **Expected Calibration Error**. It involves dividing the predicted probabilities into bins and calculating the accuracy and average predicted probability (confidence) for each bin. 
ECE is the weighted average of the absolute differences between these accuracies and confidences across all bins, reflecting how much predicted probabilities deviate from true likelihoods.
For instance, if a model predicts a 70% chance of an event and it happens 70% of the time, the model is well-calibrated. ECE helps in identifying models that give reliable probability estimates,
crucial for applications where understanding uncertainty is important.

## Inspiration

This was inspired by https://arxiv.org/pdf/2311.09215 "ConvNet vs Transformer, Supervised vs CLIP: Beyond ImageNet Accuracy" 

This paper deeply analysed vision models, while differentiating between conventional CNNs (ConvNext) & upcoming transformer-based architectures (ViT). It also differentiates between supervised and CLIP (Contrastive Language Image Pre-Training). The authors go into the depth of which model is better at which particular task and which is more "transferable", i.e. has more real-world potential. They used ImageNet-1k and ImagNet-R to evaluate already pre-trained models.
My goal with this repo is to recreate some parts of this reasearch paper, while improving my understanding of ECE, Convnext, ViT & CLIP. Interestingly, I had slightly different results compared to the research paper.

## My Results

I have used Imagenet-1k's validation as the author would have to get these results.

### ConvNext-sup
<img src="https://github.com/ariesiitr/Expected-Calibration-Error-for-Vision-Models/assets/146676085/c56db5fe-a646-4c88-a36c-92713efd62bf" width="412" height="517"/>

**ECE=0.09**
This is vastly different to the article, which has an ECE of 0.0281, also the accuracy in my test is 1% lower. Why this difference? I have used to exact architecture, training and fine-tuned model as specified.

![image](https://github.com/ariesiitr/Expected-Calibration-Error-for-Vision-Models/assets/146676085/0876d79b-a07c-4e49-877c-4f814196c50f)


### ViT-sup

<img src="https://github.com/ariesiitr/Expected-Calibration-Error-for-Vision-Models/assets/146676085/443f856a-4b41-48a0-bb8b-5eacf07f013b" width="412" height="517"/>

Its calibration is much higher, outperforming what's given in the reference but it has a lower accuracy.

![image](https://github.com/ariesiitr/Expected-Calibration-Error-for-Vision-Models/assets/146676085/bdf173fa-846d-4c2e-b494-3459a3a52457)

### ConvNext-CLIP

<img src="https://github.com/ariesiitr/Expected-Calibration-Error-for-Vision-Models/assets/146676085/be9d8645-298b-4851-8892-2d37eedc283e" width="412" height="517"/>

Again, we see a vast difference in performance.

![image](https://github.com/ariesiitr/Expected-Calibration-Error-for-Vision-Models/assets/146676085/593dcf27-0d65-4bcd-b7a0-7d574b10f959)

### ViT-CLIP

<img src="https://github.com/ariesiitr/Expected-Calibration-Error-for-Vision-Models/assets/146676085/6c422741-a776-4c34-a1f3-de90046b300d" width="412" height="517"/>

This time the ECE is an exact match but the accuracy of the model is tremendously better.

![image](https://github.com/ariesiitr/Expected-Calibration-Error-for-Vision-Models/assets/146676085/77fc0d53-e684-4fa1-a7c6-f6fbf2d69e49)


