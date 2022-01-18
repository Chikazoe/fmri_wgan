# fmri_wgan
## 1. data preprocess
- Get fmri data
  - It access "/media/chikazoe/HDD6TB_2/nagai/data"
  - There are pareprocess data in "Wasserstein_GAN/true_data" → Go to chapter 2 or chapter 3
- Execute atlas_to_icosahedron.ipynb
  - atlas_to_icosahedron.ipynb : fMRI data segmented and transformed into a planar image
- Execute preprocessed.ipynb
  - preprocessed.ipynb : Image preprocessed for application to machine learning models such as GAN
## 2. train DCGAN
- Execute Ico_DCGAN.ipynb
  - Ico_DCGAN.ipynb : Learning with DCGAN
## 3. train WGAN-GP
```
cd Wasserstein_GAN
```
- Execute below command in GPU
```
python main.py --model WGAN-GP \
               --is_train True \
               --generator_iters 40000 \
               --cuda True \
               --batch_size 64
```
- Execute below command in order to check result
```
tensorboard --logdir logs/
```
# 4 visualization
- Execute visualization.ipynb in order to get fake_data_wgan.pickle and data.pickle

```
cd ..
```
- get hcp_visualize from media/chikazoe/koyama_space/data/hcp_visualize
- Execute Back_to_Brain.ipynb in order to get visualization/weights/100206encoder_weight_corr0.2291.csv
  - Back_to_Brain.ipynb : Transformation of the generated image into the underlying fMRI data
- Execute target_of_MATLABmatrix_to_CIfTI.m in order to get *.nii file
- Operate wb_view
