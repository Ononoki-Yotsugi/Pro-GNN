# Pro-GNN 

A PyTorch implementation of "Graph Structure Learning for Robust Graph Neural Networks" (KDD 2020). [[paper]](https://arxiv.org/abs/2005.10203) [[slides]](http://cse.msu.edu/~jinwei2/files/Slides_ProGNN.pdf)

The code is based on our Pytorch adversarial repository, DeepRobust [(https://github.com/DSE-MSU/DeepRobust)](https://github.com/DSE-MSU/DeepRobust)

<div align=center><img src="https://raw.githubusercontent.com/ChandlerBang/Pro-GNN/master/ProGNN.png" width="700"/></div>

## Abstract 
Graph Neural Networks (GNNs) are powerful tools in representation learning for graphs. However, recent studies show that GNNs are vulnerable to carefully-crafted perturbations, called adversarial attacks. Adversarial attacks can easily fool GNNs in making predictions for downstream tasks. The vulnerability to adversarial attacks has raised increasing concerns for applying GNNs in safety-critical applications. Therefore, developing robust algorithms to defend adversarial attacks is of great significance. A natural idea to defend adversarial attacks is to clean the perturbed graph. It is evident that real-world graphs share some intrinsic properties. For example, many real-world graphs are low-rank and sparse, and the features of two adjacent nodes tend to be similar. In fact, we find that adversarial attacks are likely to violate these graph properties. Therefore, in this paper, we explore these properties to defend adversarial attacks on graphs. In particular, we propose a general framework Pro-GNN, which can jointly learn a structural graph and a robust graph neural network model from the perturbed graph guided by these properties. Extensive experiments on real-world graphs demonstrate that the proposed framework achieves significantly better performance compared with the state-of-the-art defense methods, even when the graph is heavily perturbed.

## Requirements
See that in https://github.com/DSE-MSU/DeepRobust/blob/master/requirements.txt
```
matplotlib==3.1.1
numpy==1.17.1
torch==1.2.0
scipy==1.3.1
torchvision==0.4.0
texttable==1.6.2
networkx==2.4
numba==0.48.0
Pillow==7.0.0
scikit_learn==0.22.1
skimage==0.0
tensorboardX==2.0
```

## Installation
To run the code, first you need to install DeepRobust:
```
pip install deeprobust
```
Or you can clone it and install from source code:
```
git clone https://github.com/DSE-MSU/DeepRobust.git
cd DeepRobust
python setup.py install
```

## Run the code
After installation, you can clone this repository
```
git clone https://github.com/ChandlerBang/Pro-GNN.git
cd Pro-GNN
python train.py --dataset polblogs --attack meta --ptb_rate 0.15 --epoch 1000
```

## Reproduce the results
All the hyper-parameters settings are included in [`scripts`](https://github.com/ChandlerBang/Pro-GNN/tree/master/scripts) folder. Note that same hyper-parameters are used under different perturbation for the same dataset. 

To reproduce the performance reported in the paper, you can run the bash files in folder `scripts`.
```
sh scripts/meta/cora_meta.sh
```
To test performance under different severity of attack, you can change the `ptb_rate` in those bash files.

<!--
**IMPORTANT NOTICE** For the performance of Pubmed dataset, if you don't add the code (line 59-62 in `train.py`), the performance of GCN should be around 85 since the data splits are different from what I used in the paper. See details in https://github.com/ChandlerBang/Pro-GNN/issues/2
-->

## Generate attack by yourself
With the help of DeepRobust, you can run the following code to generate meta attack
```
python generate_attack.py --dataset cora --ptb_rate 0.05 --seed 15
```

## Cite
For more information, you can take a look at the [paper](https://arxiv.org/abs/2005.10203) or the detailed [code](https://github.com/DSE-MSU/DeepRobust/blob/master/deeprobust/graph/defense/prognn.py) shown in DeepRobust.

If you find this repo to be useful, please cite our paper. Thank you.
```
@inproceedings{jin2020graph,
  title={Graph Structure Learning for Robust Graph Neural Networks},
  author={Jin, Wei and Ma, Yao and Liu, Xiaorui and Tang, Xianfeng and Wang, Suhang and Tang, Jiliang},
  booktitle={26th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, KDD 2020},
  pages={66--74},
  year={2020},
  organization={Association for Computing Machinery}
}
```
