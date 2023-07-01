# Learning Seismocardiogram Beat Denoising Without Clean Data

Noninvasive monitoring of cardiovascular health plays a crucial role in predicting risks and reducing mortality rates, especially in the context of trauma care. The seismocardiogram (SCG) in particular is a noninvasive signal that has been shown to monitor key health parameters related to blood volume loss estimation, suggesting its ability to guide trauma care intervention. Robust extraction of features from SCG signals in noisy environments is challenging due to low signal-to-noise ratios (SNR). In addition, lack of access to clean ground truth signals makes developing denoising algorithms even more difficult.

In this work, we introduce a deep learning architecture adapted from the Noise2Noise architecture, which was originally used for image restoration without clean labels. They showed that learning to restore images from corrupted images by only using the corrupted examples (no image priors or corruption likelihoods) is possible. Our proposed architecture is designed to restore clean SCG beats from a corrupted SCG beat, without requiring access to the corresponding clean ground truth labels. 

Experimental results showed (1) enhancement in the SNR (approximately 10 dB and 9 dB increase for AO and AC regions of -10 dB SNR beats respectively), and (2) improvements in feature extraction accuracy (approximately 3x and 1.5x for AO and AC features of -10 dB SNR beats respectively) using the denoising model. Thus, the model effectively reduces noise, and improves the quality of SCG signals, leading to improved accuracy in feature extraction in noisy environments. This is a promising step forward in improving the quality and utility of SCG signals for clinical and research purposes.ound truth labels. 

## Overview
Overview of the proposed SCG beat denoising model. (a) The noisy SCG beat with a low SNR is fed into the model as input. (b, c) The denoising model suppresses the noise artifacts while maintaining the signal power resulting in an output SCG beat with higher SNR. (d) This higher SNR SCG beat can be used for extracting PEP and LVET features more robustly with higher accuracy. SCG: Seismocardiogram; SNR: Signal to Noise Ratio.

<p align="center">
<img src="https://github.com/mohnikbakht/Noise2Noise_SCG_Beats_Demo/blob/main/figures/figure1.png" alt="overview figure" width="600"/>
</p>

## Architecture 

The architecture of the proposed neural network. (a) The SCG beat waveforms are transformed to images using CWT. (b, c) The adapted Noise2Noise architecture proposed will receive the noisy SCG beats and output a higher SNR SCG beat as output. (d) During training, the target output is a noisy SCG beat with a different noise compared to the input noise and the model tries to minimize the loss between it’s output and this target (c) resulting in a denoised output after convergence. CWT: Continuous Wavelet Transform; SNR: Signal to Noise Ratio; SCG: Seismocardiogram.

<p align="center">
<img src="https://github.com/mohnikbakht/Noise2Noise_SCG_Beats_Demo/blob/main/figures/figure2.png" alt="Architecture figure" width="600"/>
</p>

## Results

(a, c) Box and whisker plots showing the mean SNR improvements in both the AO and AC regions of the SCG beats for all pigs (n=6) after denoising the beats using the denoising model proposed. (b, d) RMSE results on estimated PEP and LVET tracked features on all pigs (n = 6) for both noisy SCG beats and denoised SCG beats with different amounts of noise present in the noisy beats.

<p align="center">
<img src="https://github.com/mohnikbakht/Noise2Noise_SCG_Beats_Demo/blob/main/figures/figure3.png" alt="results figure" width="600"/>
</p>

 ## Conclusion

 In this work, we designed and validated a SCG beat denoising model trained without clean signals. Our results demonstrate that it is possible to restore a corrupted SCG beat without needing the corresponding clean SCG beat, which can be difficult to obtain. The model proposed can be used to reduce the noise in corrupted SCG beats while keeping the underlying cardiac content, resulting in enhanced SNR and improved accuracy of feature extraction. This would enable robust tracking of the SCG features in noisy environments for noninvasive patient health assessment helping healthcare professionals make more informed decisions and guide interventions.
