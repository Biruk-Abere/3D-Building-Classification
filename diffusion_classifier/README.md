<div align="center">

<!-- TITLE -->
# **Multi View Diffusion Classifier**

[![arXiv](https://img.shields.io/badge/cs.LG-arXiv:2303.16203-b31b1b.svg)](https://arxiv.org/abs/2303.16203)
[![Website](https://img.shields.io/badge/🌎-Website-blue.svg)](http://diffusion-classifier.github.io)
</div>

## Installation
Create a conda environment with the following command:
```bash
conda env create -f environment.yml
```
If this takes too long, `conda config --set solver libmamba` sets conda to use the `libmamba` solver and could speed up installation.

## Zero-shot Classification with Stable Diffusion

```bash
!python eval_prob_adaptive.py --dataset shapenet --split test --n_trials 1 \
  --to_keep 3 1 --n_samples 100 500 --loss l1 \
  --prompt_path prompts/shapenet_prompts.csv
```
This command reads potential prompts from a csv file and evaluates the epsilon prediction loss for each prompt using Stable Diffusion.
This should work on a variety of GPUs, from as small as a 2080Ti or 3080 to as large as a 3090 or A6000. 
Losses are saved separately for each test image in the log directory. For the command above, the log directory is `data/cifar10/v2-0_1trials_5_1keep_50_500samples_l1`. Accuracy can be computed by running:
```bash
!python scripts/print_acc.py data/shapenet/v2-0_1trials_3_1keep_100_500samples_l1
```

Commands to run Diffusion Classifier on each dataset are [here](commands.md). 
If evaluation on your use case is taking too long, there are a few options: 
1. Parallelize evaluation across multiple workers. Try using the `--n_workers` and `--worker_idx` flags.
2. Play around with the evaluation strategy (e.g. `--n_samples` and `--to_keep`).
3. Evaluate on a smaller subset of the dataset. Saving a npy array of test set indices and using the `--subset_path` flag can be useful for this.

### Evaluating on your own dataset
1. Create a csv file with the prompts that you want to evaluate, making sure to match up the correct prompts with the correct class labels. See `scripts/write_cifar10_prompts.py` for an example. Note that you can use multiple prompts per class.
2. Run the command above, changing the `--dataset` and `--prompt_path` flags to match your use case.
3. Play around with the evaluation strategy on a small subset of the dataset to reduce evaluation time.




## Citation

If you find this work useful in your research, please cite:

```bibtex
@misc{li2023diffusion,
      title={Your Diffusion Model is Secretly a Zero-Shot Classifier}, 
      author={Alexander C. Li and Mihir Prabhudesai and Shivam Duggal and Ellis Brown and Deepak Pathak},
      year={2023},
      eprint={2303.16203},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
}
```
