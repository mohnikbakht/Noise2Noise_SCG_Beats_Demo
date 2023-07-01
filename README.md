# Learning Seismocardiogram Beat Denoising Without Clean Data

Seismocardiogram (SCG) is the measure of the thoracic vibrations produced by the heart’s contraction and the ejection of blood from the ventricles into the vascular tree and is a non-invasive cardiovascular signal containing features correlated to aortic opening (AC) and aortic closing (AC) events. These features in particular are important for this task as they contain information about the left ventricular health

However, the small amplitude of SCG signals makes them vulnerable to external vibrations and motion artifacts which can corrupt the AO and AC features. This susceptibility can result in unreliable estimation of SCG features, particularly in real-world scenarios such as when a patient is being transported to a hospital.

In this work, we introduce a deep learning architecture adapted from the Noise2Noise architecture, which was originally used for image restoration without clean labels \cite{lehtinen2018noise2noise}. They showed that learning to restore images from corrupted images by only using the corrupted examples (no image priors or corruption likelihoods) is possible \cite{lehtinen2018noise2noise}. Our proposed architecture is designed to restore clean SCG beats from a corrupted SCG beat, without requiring access to the corresponding clean ground truth labels. 

## Overview
Overview of the proposed SCG beat denoising model. (a) The noisy SCG beat with a low SNR is fed into the model as input. (b, c) The denoising model suppresses the noise artifacts while maintaining the signal power resulting in an output SCG beat with higher SNR. (d) This higher SNR SCG beat can be used for extracting PEP and LVET features more robustly with higher accuracy. SCG: Seismocardiogram; SNR: Signal to Noise Ratio.

<p align="center">
<img src="https://github.com/mohnikbakht/Noise2Noise_SCG_Beats_Demo/blob/main/Images/figure1.png" alt="overview figure" width="600"/>
</p>

## Architecture 

The architecture of the proposed neural network. (a) The SCG beat waveforms are transformed to images using CWT. (b, c) The adapted Noise2Noise architecture proposed will receive the noisy SCG beats and output a higher SNR SCG beat as output. (d) During training, the target output is a noisy SCG beat with a different noise compared to the input noise and the model tries to minimize the loss between it’s output and this target (c) resulting in a denoised output after convergence. CWT: Continuous Wavelet Transform; SNR: Signal to Noise Ratio; SCG: Seismocardiogram.

<p align="center">
<img src="https://github.com/mohnikbakht/Noise2Noise_SCG_Beats_Demo/blob/main/Images/figure2.png" alt="Architecture figure" width="600"/>
</p>

## Results

(a, c) Box and whisker plots showing the mean SNR improvements in both the AO and AC regions of the SCG beats for all pigs (n=6) after denoising the beats using the denoising model proposed. (b, d) RMSE results on estimated PEP and LVET tracked features on all pigs (n = 6) for both noisy SCG beats and denoised SCG beats with different amounts of noise present in the noisy beats.

<p align="center">
<img src="https://github.com/mohnikbakht/Noise2Noise_SCG_Beats_Demo/blob/main/Images/figure3.png" alt="results figure" width="600"/>
</p>

 ## Conclusion

 In this work, we designed and validated a SCG beat denoising model trained without clean signals. Our results demonstrate that it is possible to restore a corrupted SCG beat without needing the corresponding clean SCG beat, which can be difficult to obtain. The model proposed can be used to reduce the noise in corrupted SCG beats while keeping the underlying cardiac content, resulting in enhanced SNR and improved accuracy of feature extraction. This would enable robust tracking of the SCG features in noisy environments for noninvasive patient health assessment helping healthcare professionals make more informed decisions and guide interventions.
