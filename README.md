# DATASET

All ShapeNet https://drive.google.com/file/d/1gwRviPb18vANDECAqeUqLBCvBTnfq7fo/view [30GB] 
ShapeNet 3 Classes https://drive.google.com/drive/folders/10dVJxcSIjp3EfQkqEiA2xJ9N9mtyTQFV?usp=drive_link

Chairs Airplane Cars

[ OOD --> Toy4k -> ModelNet ] 

## Evaluate on AWS

```ssh -i "3dv.pem" ubuntu@ec2-35-172-217-206.compute-1.amazonaws.com```

```conda activate diffusion-classifier```

```cd /home/ubuntu/3D-Building-Classification-main/diffusion_classifier```

```python eval_prob_adaptive.py --dataset shapenet --split test --n_trials 1 --to_keep 3 1 --n_samples 100 500 --loss l1 --prompt_path prompts/shapenet_prompts_meher.csv```

Then the log directory will be something like this: ``` data/shapenet/v2-0_1trials_3_1keep_100_500samples_l1 ```

Accuracy can be computed by running: ``` python scripts/print_acc.py data/shapenet/v2-0_1trials_3_1keep_100_500samples_l1 ```

Use pytorch 11.7


# Multi-Modal Diffusion Models For 3D Objects Classification 🏢🌐

Team: Biruk Abere, Berfin Inal, Gabriele Dominici, Meher Nigam, Alex Li,  Nursena Koprucu, Sharvaree Vadgama, Le Xue, Shicheng Xu, Alberto Tono 

This repository contains the implementation of our approach that integrates the methodologies of the LION paper and the Diffusion Classifier for advanced 3D building classification. 

![3D Building Classification]()



# Installation 🔧

  * git clone https://github.com/SGI-2023/3D-Building-Classification.git
  * cd multi-modal-diffusion-models
  * pip install -r requirements.txt

# Results  📈


# Licence 📜
Render used [Mitsuba Render here](https://github.com/hasancaslan/BeautifulPointCloud)




