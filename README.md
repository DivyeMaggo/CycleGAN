# CycleGAN
CycleGAN has been essential to the field of unpaired image-to-image translation.The unique aspect of CycleGAN  is its ability to learn these translations in both directions. It comprises two main components: a generator and a discriminator. The generator transforms images from one domain to another, while the discriminator distinguishes between the generated images and real images. What sets CycleGAN [39] apart is its cycle-consistency principle, ensuring that if an image is transformed from domain A to domain B and back to domain A, it should resemble the original image. This cycle consistency constraint enables the model to preserve important visual characteristics during the transformation process.

All loss functions generated during model training
![image](https://github.com/user-attachments/assets/baba41e6-c36f-4250-b708-d00d046ff278)

For the whole logs please go to https://wandb.ai/aiml23/CycleGan/runs/43akmgtg/overview



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
