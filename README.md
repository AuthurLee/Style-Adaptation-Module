# Style-Adaptation-Module

Codes for [Style Adaptation module: Enhancing detector robustness to inter-manufacturer variability in surface defect detection](https://doi.org/10.1016/j.compind.2024.104084), implemented in [YOLOv7](https://github.com/WongKinYiu/yolov7).

> Open access [link](https://authors.elsevier.com/c/1ino~bquFYjLz) before May 09, 2024. (No sign up, registration or fees are required.)

## Run

- train

```bash
data=data/mt500.yaml
model=cfg/training/style_yolov7.yaml
trainFile=train_sa.py
python $trainFile --weights '' --data $data --cfg $model --batch-size 16 --epochs 50 --cache-images --device 0 --hyp data/hyp.scratch.p5.yaml --with_target_labels --double_stream --transfer_loss norm2
```

- test

```bash
weight=weights/t500.pt
data=data/mt500.yaml

python test.py --data $data --img 640 --batch 16 --conf 0.001 --iou 0.65 --device 0 --weights $weight --task test
```

## More details

Fore more details, see [YOLOv7](https://github.com/WongKinYiu/yolov7).

## Citation

```bibtex
@article{LI2024104084,
    title = {Style Adaptation module: Enhancing detector robustness to inter-manufacturer variability in surface defect detection},
    journal = {Computers in Industry},
    volume = {157-158},
    pages = {104084},
    year = {2024},
    issn = {0166-3615},
    doi = {https://doi.org/10.1016/j.compind.2024.104084},
    url = {https://www.sciencedirect.com/science/article/pii/S0166361524000125},
    author = {Chen Li and Xiakai Pan and Peiyuan Zhu and Shidong Zhu and Chengwei Liao and Haoyang Tian and Xiang Qian and Xiu Li and Xiaohao Wang and Xinghui Li},
    keywords = {Surface defect detection, Domain adaptation, Style transfer},
    abstract = {In recent years, deep learning-based approaches for industrial surface defect detection have shown great promise. To address the domain shift issue among data from different sources in the industrial domain, we present a novel plug-and-play Style Adaptation (SA) module, which endows the equipped defect detector with the capability to exhibit robustness to diverse styles present within the samples. This module effectively leverages datasets sourced from diverse origins while possessing congruent data types. In contrast to other domain adaptation approaches lacking well-defined domain delineations, the SA module generates representations characterized by distinct practical implications and precise mathematical formulations. Moreover, incorporating attention mechanisms reduces the need for manual intervention, allowing the module to focus autonomously on crucial branches in it. Experimental results demonstrate the superior efficacy of our approach compared to state-of-the-art techniques. Furthermore, an authentic dataset from various manufacturers is publicly available for deep learning research and industrial applications. Access the dataset at: https://github.com/THU-PMVAI/MTS3D}
}
```