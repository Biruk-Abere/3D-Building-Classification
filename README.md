# Multi-Modal Diffusion Models For 3D Objects Classification 

Team: Biruk Abere, Berfin Inal, Gabriele Dominici, Meher Nigam, Alex Li,  Nursena Koprucu, Sharvaree Vadgama, Le Xue, Shicheng Xu, Alberto Tono 

![Diagram (1)](https://github.com/user-attachments/assets/55b38187-cf11-436a-8fc5-4fa1e31e7908)


Inspired by Geoffrey Hinton’s emphasis on generative modeling (“To recognize shapes, first learn to generate them"), we explore the use of 3D diffusion models for object classification. Leveraging the density estimates from these models, our approach, “Diffusion Classifier for 3D Objects”, dubbed DC3DO, enables zero-shot classification of 3D shapes without additional training. Our method achieves an average of 12.5\% improvement compared with its multi-view counterparts, demonstrating superior multimodal reasoning compared to discriminative approaches. DC3DO uses a class-conditional diffusion model trained on ShapeNet. We run inferences on chairs and cars pointclouds. This work underscores the potential of generative models in 3D object classification.

This repository contains the implementation of our approach that integrates the methodologies of the LION paper and the Diffusion Classifier for advanced 3D building classification. 

# DATASET

ShapeNet first 200 shapes in chairs and cars

![NewHero1](https://github.com/user-attachments/assets/b7be2bde-1339-4205-90ee-65137b962dce)



# Installation 🔧

  * git clone https://github.com/SGI-2023/3D-Building-Classification.git
  * cd multi-modal-diffusion-models
  * pip install -r requirements.txt

# LION (CD3DO)
  * for the LION use ```pytorch 11.7```
  * ```conda activate diffusion-classifier```
  * ```cd /home/ubuntu/3D-Building-Classification-main/diffusion_classifier```
  * ```python eval_prob_adaptive.py --dataset shapenet --split test --n_trials 1 --to_keep 3 1 --n_samples 100 500 --loss l1 --prompt_path prompts/shapenet_prompts_meher.csv```
  * Then the log directory will be something like this: ``` data/shapenet/v2-0_1trials_3_1keep_100_500samples_l1 ```
  * Accuracy can be computed by running: ``` python scripts/print_acc.py data/shapenet/v2-0_1trials_3_1keep_100_500samples_l1 ```


# Licence 📜
Render used [Mitsuba Render here](https://github.com/hasancaslan/BeautifulPointCloud)




