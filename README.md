# FishFry-Detection-YOLOv10-to-v12-DINO-BYOL-STAC 

**Advanced Live/Dead Fish Fry Detection using YOLOv12 with DINO, BYOL, and STAC Knowledge Distillation**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.11-blue)](https://www.python.org/)
[![Ultralytics YOLO](https://img.shields.io/badge/Ultralytics-YOLOv12-8A2BE2)](https://github.com/ultralytics/ultralytics)
[![Dataset](https://img.shields.io/badge/Dataset-Mendeley-brightgreen)](https://data.mendeley.com/datasets/y52ffd3xdc/1)

This project presents a state-of-the-art object detection system for **live and dead largemouth bass (Micropterus salmoides) fry** in dense aquaculture scenes. By combining the latest **YOLOv12** architecture with advanced self-supervised pretraining (**DINO** & **BYOL**) and knowledge distillation (**STAC**), we achieve superior performance on small, overlapping, and low-contrast targets.

Trained and evaluated on the **Fish Fry Dataset (FFD)** – a challenging benchmark for stocking density control and health assessment in aquaculture.

## 📊 Dataset

**Fish Fry Dataset (FFD): used for stocking density control and health assessment**  
- **Authors**: Zhaoyu Zhai, Huanliang Xu, Yuqiang Wu (and others)  
- **Year**: 2024  
- **Images**: 1,101  
- **Annotations**: 51,119 live fry + 3,586 dead fry (YOLO format)  
- **Species**: Largemouth bass (*Micropterus salmoides*) fry  
- **Challenges**: High density (20–80 fry/image), occlusion, overlapping, varying lighting  

**Link**: [Mendeley Data - Fish Fry Dataset (DOI: 10.17632/y52ffd3xdc.1)](https://data.mendeley.com/datasets/y52ffd3xdc/1)  

**Associated Publication**:  
Zhai, Z., Xu, H., Wu, Y., et al. (2024). A fish fry dataset for stocking density control and health assessment based on computer vision. *Data in Brief*, 51, 110937. https://doi.org/10.1016/j.dib.2024.110937

## 🚀 Key Contributions & Pipeline

We systematically explored self-supervised learning and knowledge distillation to boost performance on tiny fish fry:

- **DINO** → Self-supervised pretraining for rich feature extraction
- **BYOL** → Bootstrap Your Own Latent (contrastive learning without negatives)
- **STAC** → Student-Teacher Agreement via Classification distillation
- Progressive experimentation across **YOLOv10 → YOLOv11 → YOLOv12**

**Best Model**: YOLOv12 fine-tuned with full DINO + BYOL + STAC pipeline  
→ Highest mAP, robust detection of live (green boxes) vs. dead (red boxes) fry even in extreme density and occlusion.

## 📂 Repository Contents (Jupyter Notebooks)

| Notebook | Description |
|--------|-------------|
| `dinov10-lat (1).ipynb` | DINO self-supervised pretraining on YOLOv10 |
| `byolv10 (1).ipynb` | BYOL representation learning on YOLOv10 |
| `stac-yolov10n.ipynb` | STAC knowledge distillation (YOLOv10n) |
| `final-dinoyolov11 (2).ipynb` | DINO + supervised fine-tuning on YOLOv11 |
| `byol-yolov11.ipynb` | BYOL on YOLOv11 |
| `stac-yolov11 (1).ipynb` | STAC distillation on YOLOv11 |
| `dino-yolov12-latest (1).ipynb` | DINO pretraining on latest YOLOv12 |
| `stac-yolov12 (2).ipynb` | STAC on YOLOv12 |
| `yolov12-byol-project-bestof-all (1).ipynb` | **Final best pipeline**: YOLOv12 + DINO + BYOL + STAC |

## 🛠️ How to Use / Clone

To clone this repository:

```bash
git clone https://github.com/backlashblitz/FishFryVision-YOLOv10-to-v12.git
cd FishFryVision-YOLOv10-to-v12

pip install ultralytics albumentations pycocotools torchmetrics tqdm

@article{ZHAI2024110937,
  title    = {A fish fry dataset for stocking density control and health assessment based on computer vision},
  journal  = {Data in Brief},
  volume   = {51},
  pages    = {110937},
  year     = {2024},
  issn     = {2352-3409},
  doi      = {https://doi.org/10.1016/j.dib.2024.110937},
  url      = {https://www.sciencedirect.com/science/article/pii/S2352340924010370},
  author   = {Zhaoyu Zhai and Huanliang Xu and Yuqiang Wu and Bowen Liao and Jia Nie and Chengxi Xu and Ziao Zhang}
}

@dataset{Zhai_2024,
  author    = {Zhaoyu Zhai and Huanliang Xu and Yuqiang Wu},
  title     = {Fish Fry Dataset (FFD): used for stocking density control and health assessment},
  year      = {2024},
  publisher = {Mendeley Data},
  version   = {V1},
  doi       = {10.17632/y52ffd3xdc.1},
  url       = {https://data.mendeley.com/datasets/y52ffd3xdc/1}
}
