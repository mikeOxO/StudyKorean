# Image Caption in Chinese

The Chinese image description problem combines the two directions of computer vision and natural language processing, and outputs a sentence description of the picture. Descriptive sentences are required to conform to natural language habits, highlight important information in images, and cover main characters, scenes, and actions.

## Environment

- Python==3.5
- Tensorflow==1.5.0
- Keras==2.2.2

## 数据集

<div align=center><img width="600" src="https://github.com/mikeOxO/image-caption-in-chinese/raw/master/images/dataset.png"></div>

数据来自[2017 AI Challenger](https://challenger.ai/competition/caption)  
数据集对给定的每一张图片有五句话的中文描述。数据集包含 30 万张图片，150 万句中文描述。  
训练集：210,000 张  
验证集：30,000 张  
测试集 A：30,000 张  
测试集 B：30,000 张  
[数据集下载](https://challenger.ai/dataset/caption)，放在 data 目录

## 模型结构

<div align=center><img width="600" src="https://github.com/mikeOxO/image-caption-in-chinese/raw/master/images/net.png"></div>

## Result

| CIDEr | Bleu_4 | Bleu_3 | Bleu_2 | Bleu_1 | ROUGE_L | METEOR |
| ----- | ------ | ------ | ------ | ------ | ------- | ------ |
| 0.810 | 0.281  | 0.368  | 0.482  | 0.634  | 0.489   | 0.291  |

## 使用方式

### Demo

下载 [预训练模型](https://github.com/mikeOxO/image-caption-in-chinese/releases/download/v1.0/model.04-1.3820.hdf5) 放在 models 目录

```bash
$ python app.py
```

| Image                                                                                          | Caption                                                                                                                                                                                                                                                                                      |
| ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![image](https://github.com/mikeOxO/image-caption-in-chinese/raw/master/images/0_bs_image.jpg) | Beam Search, k=1: 一个穿着潜水服的人在蔚蓝的海里潜水<br>Beam Search, k=3: 海面上有一个穿着潜水服的人在潜水<br>Beam Search, k=5: 海面上有一个穿着潜水服的人在潜水<br>Beam Search, k=7: 波涛汹涌的大海里有一个穿着潜水服的人在冲浪                                                             |
| ![image](https://github.com/mikeOxO/image-caption-in-chinese/raw/master/images/1_bs_image.jpg) | Beam Search, k=1: 大厅里一群人旁边有一个穿着黑色衣服的女人在下国际象棋<br>Beam Search, k=3: 大厅里一群人的旁边有一个左手托着下巴的女人在下国际象棋<br>Beam Search, k=5: 大厅里一群人旁有一个戴着眼镜的女人在下国际象棋<br>Beam Search, k=7: 大厅里一群人旁边有一个戴着眼镜的女人在下国际象棋 |

### 数据预处理

```bash
$ python generated.py
```

### 训练

```bash
$ python backward.py
```

### 可视化训练过程

```bash
$ tensorboard --logdir path_to_current_dir/logs
```

## 网页展示

<div align=center><img width="600" src="https://github.com/mikeOxO/image-caption-in-chinese/raw/master/images/web1.jpg"></div>
<div align=center><img width="600" src="https://github.com/mikeOxO/image-caption-in-chinese/raw/master/images/web2.jpg"></div>

## Reference

- Paper: Show and Tell: A Neural Image Caption Generator https://arxiv.org/pdf/1411.4555
- Code: https://github.com/foamliu/Image-Captioning
