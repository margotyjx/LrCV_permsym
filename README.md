# Learning collective variables for particle systems with permutational symmetry

This repository contains the implementation of paper Learning collective variables for particle systems with permutational symmetry.

## Requirements:
- python 3.7

## Usage

LrCV_permsym
├── CV_evaluation
│   ├──LJ7in2D
│   │   ├── CV_OrderedCoordNum
│   │   │  ├── Data
│   │   │  ├── FEMdataBETA5
│   │   │  ├── FEMdataBETA7
│   │   │  ├── FEMdataBETA9
│   │   │  ├── Figures
│   │   │  ├── LJ7_CV_data
│   │   │  ├── FEM_TPT.py
│   │   │  └── LJ7_CV_SortCNum.ipynb
│   │   ├── CV_SortedDistSquared
│   │   │  ├── Data
│   │   │  ├── FEMdataBETA5
│   │   │  ├── FEMdataBETA7
│   │   │  ├── FEMdataBETA9
│   │   │  ├── Figures
│   │   │  ├── LJ7in2Dmin
│   │   │  ├── MLCV_SortD2_data
│   │   │  ├── FEM_TPT.py
│   │   │  └── MLCV_SortDistSquared.ipynb
│   │   ├── mu2mu3
│   │   │  ├── Data
│   │   │  ├── FEMdataBETA5
│   │   │  ├── FEMdataBETA7
│   │   │  ├── FEMdataBETA9
│   │   │  ├── Figures
│   │   │  ├── LJ7in2Dmin
│   │   │  ├── FEM_TPT.py
│   │   │  └── LJ7mu2mu3.ipynb
│   │   └──  NN_committor_approx.py
│   ├── LJ8in3D
│   │   ├── image_dailylife
│   │   ├── image_comics
│   │   ├── image_robotics
│   │   ├── single_image_dailylife
│   │   ├── single_image_comics
│   │   └──  single_image_robotics
│   └── compute_rates.ipynb
├── CV_learning
│   ├── hallusion_bench
│   │   ├── VD
│   │   ├── VS
│   ├── evaluation.py
│   ├── HallusionBench.json
│   └── HallusionBench_result.json

### Learning collective variables: CV_learning
- **Step 1**. Compute manifold with diffusion maps
  
  ```python diff_map.py --example LJ7 --fname ../LJ7/data/LJ7bins_confs.txt --use_C```
- **Step 2**. Approximate the manifold with neural network

  ```python main_DDnet.py --example LJ7 --read_knn 0.25 --epsilon 1.0 --hidden 45,30,25 --epochs 4000```

  and learn the zero-level set of the manifold

  ```python Manifold.py --example LJ7 --read_knn 0.25 --epsilon 1.0 --generate```
- **Step 3**. Learn collective variables using pre-computed components.

  ```python main_CV.py --example LJ7 --knn 125 --use_C --theta1 1.0 --theta2 0.2 --mep_loss```

### Computation of free energy and diffusion tensor and committor function via FEM


### Visualization and approximation of committor function for forward flux sampling: CV_evaluation




