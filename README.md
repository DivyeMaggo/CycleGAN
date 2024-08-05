<img src='imgs/horse2zebra.gif' align="right" width=384>

<br><br><br>

# CycleGAN
### 

Torch implementation for learning an image-to-image translation (i.e. [pix2pix](https://github.com/phillipi/pix2pix)) **without** input-output pairs, for example:

### Training Instruction
- Download a dataset (e.g. zebra and horse images from ImageNet):
```bash
bash ./datasets/download_dataset.sh horse2zebra
```
- Train a model:
```bash
DATA_ROOT=./datasets/horse2zebra name=horse2zebra_model th train.lua
```
- (CPU only) The same training command without using a GPU or CUDNN. Setting the environment variables ```gpu=0 cudnn=0``` forces CPU only
```bash
DATA_ROOT=./datasets/horse2zebra name=horse2zebra_model gpu=0 cudnn=0 th train.lua
```
- (Optionally) start the display server to view results as the model trains. (See [Display UI](#display-ui) for more details):
```bash
th -ldisplay.start 8000 0.0.0.0
```

### Testing Instruction
- Finally, test the model:
```bash
DATA_ROOT=./datasets/horse2zebra name=horse2zebra_model phase=test th test.lua
```
The test results will be saved to an HTML file here: `./results/horse2zebra_model/latest_test/index.html`.






## Citation

@inproceedings{CycleGAN2017,
  title={Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networkss},
  author={Zhu, Jun-Yan and Park, Taesung and Isola, Phillip and Efros, Alexei A},
  booktitle={Computer Vision (ICCV), 2017 IEEE International Conference on},
  year={2017}
}

The code has been reffered from [PyTorch](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix) | [project page](https://junyanz.github.io/CycleGAN/) |   [paper](https://arxiv.org/pdf/1703.10593.pdf)
