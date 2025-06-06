This repository contains the PyTorch implementation of the following paper:

**MuTri: Multi-view Tri-alignment for OCT to OCTA 3D Image Translation**

## Installation

- Create conda environment and activate it:
```
conda create -n octa python=3.6
conda activate octa
```
- Clone this repo:
```
git clone https://github.com/cheny124800/MuTri.git
cd MuTri
```

- Install requirements:
```
pip install -r requirements.txt
```

## Usage
### Data preparation
We use OCTA-3M, OCTA-6M, and OCTA2024 datasets in our paper. 

The OCTA-3M amd OCTA-6M datasets are from [OCTA-500](https://ieee-dataport.org/open-access/octa-500)

Please contact us for the access of OCTA2024 dataset with research purpose only

### Train 
- To view training results and loss plots, please run:
```
python -m visdom.server -p 6031
```
and click the URL http://localhost:6031

- Stage I Training, please run:
```
python train_Stage_I.py --dataroot ./octa-500/OCT2OCTA3M_3D --name MuTri_3M_Stage_I --model MuTri --netG unet_256 --direction AtoB --lambda_A 10 --lambda_C 5 --dataset_mode alignedoct2octa3d --norm batch --pool_size 0 --load_size 304 --input_nc 1 --output_nc 1 --display_port 6031 --gpu_ids 0 --no_flip
```

- Stage II Training, please run:
```
python train_Stage_II.py --dataroot ./octa-500/OCT2OCTA3M_3D --name MuTri_3M_Stage_II --model MuTri --netG unet_256 --direction AtoB --lambda_A 10 --lambda_C 5 --dataset_mode alignedoct2octa3d --norm batch --pool_size 0 --load_size 304 --input_nc 1 --output_nc 1 --display_port 6031 --gpu_ids 0 --no_flip
```

### Test
- To test the model, please run:
```
python test.py --dataroot ./octa-500/OCT2OCTA3M_3D --name MuTri_3M_Stage_test --test_name MuTri_3M_Stage_test --model MuTri --netG unet_256 --direction AtoB --lambda_A 10 --lambda_C 5 --dataset_mode alignedoct2octa3d --norm batch --input_nc 1 --output_nc 1 --gpu_ids 0 --num_test 15200 --which_epoch 164 --load_iter 164
```


## Citation
If our paper is useful for your research, please cite:


## :rocket: Implementation reference
  - https://github.com/ustlsh/TransPro


## :smile: Feel free to contact us
  - 1248013830@qq.com

