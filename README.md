# Single-Image Super-Resolution (SR)

## Abstract

We address the task of reconstructing high-resolution (HR) images from low-resolution (LR) inputs using a GAN-based approach. Our model (SRGAN) is designed to preserve structure while improving fidelity and sharpness.

<p align="center">

![image](https://github.com/doobiusP/Single_Image_Super_Resolution/assets/36434536/e1faf3e4-75c6-4127-8255-1d9c22719930?raw=True)

</p>

## Highlights

* **Model**: SRGAN trained on > **6,000** HR/LR pairs with 273 validation pairs (dataset available on Kaggle <a href="https://www.kaggle.com/datasets/doobiusp/various-ordered-images-for-super-resolution-task">here</a>).
* **Pipeline**: Includes dataset loading, model architecture, and training scripts with on-the-fly data augmentation.
* **Inference**: Simple `upscale()` utility to enlarge any image from its file path.

## Method

We perform single-image, single-output SR using a generator–discriminator GAN.

<p align="center">

![image](https://github.com/doobiusP/Single_Image_Super_Resolution/assets/36434536/18949d5a-5ea8-4333-aa2f-2f36f4674803) <br/> <sub>Fig. 1 — Generator</sub>

![image](https://github.com/doobiusP/Single_Image_Super_Resolution/assets/36434536/e4a1128e-12bf-4c4f-b2d7-169b9969ef16) <br/> <sub>Fig. 2 — Discriminator</sub>

</p>

**Generator**: a stack of residual blocks with pixel-shuffle upsampling.
**Color baseline**: a bicubically upscaled input is fused to stabilize color.
**Post-processing**: optional sharpening after upscaling.

## Results

<p align="center">

![image](https://github.com/doobiusP/Single_Image_Super_Resolution/assets/36434536/eb82c8e3-ebcf-4896-bc59-bff5dd6a3a4a)

</p>

<p align="center">

![image](https://github.com/doobiusP/Single_Image_Super_Resolution/assets/36434536/8e11d509-4eed-4021-bc63-8d06c21da190) <br/> <sub>Fig. 3 — Flask web UI for the model.</sub>

</p>

<p align="center">

![image](https://github.com/doobiusP/Single_Image_Super_Resolution/assets/36434536/67cdd0d3-2438-44a3-9b76-52b0c0de46e6?raw=True) <br/> <sub>Fig. 4 — Example output. Note the high SSIM.</sub>

</p>

**Evaluation** (76 unseen images; diverse content):

* Average **PSNR**: 23.048
* Average **SSIM**: **0.9438**

<sub>SSIM ∈ [0,1]; closer to 1 is better. PSNR is reported for completeness but correlates weakly with perceived quality.</sub>

## Conclusion

Our SRGAN implementation achieves sharp, perceptually convincing HR reconstructions and exceeds results reported in the original paper due to targeted modifications. With more data and training time, the model is suitable for integration into consumer image-editing workflows.

## Tech Stack

* NumPy
* PyTorch
* Matplotlib
* Pillow
* Flask
* HTML/CSS

## Links

* <a href="https://www.kaggle.com/code/doobiusp/srgan">Kaggle Code</a>
* <a href="https://www.kaggle.com/datasets/doobiusp/various-ordered-images-for-super-resolution-task">Kaggle Dataset</a>

## References

* <a href="https://arxiv.org/abs/1609.04802">Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network</a>
* <a href="https://youtu.be/1HqjPqNglPc?si=ezqEiYBfKW1Wtv_I">SRGAN in Keras (video)</a>
* <a href="https://medium.com/@neetu.sigger/a-comprehensive-guide-to-understanding-and-implementing-bottleneck-residual-blocks-6b420706f66b">Bottleneck residual blocks</a>
