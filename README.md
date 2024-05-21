# R11921098_THESIS
Bandwidth-Efficient Inferencing at the Edge -- An Experimental Approach to Analyze the Effect of VSR on Compressed Video

[Demo Video](https://youtu.be/fr44s7w-4CE)

### Files Setup
---

Clone this repo
```
git clone https://github.com/b06901089/R11921098_THESISv2.git
cd R11921098_THESISv2/
```

Clone [mAP](<https://github.com/Cartucho/mAP>) inside the repo
```
git clone https://github.com/Cartucho/mAP
```

Clone [BasicVSR++](<https://github.com/ckkelvinchan/BasicVSR_PlusPlus>) inside the repo
```
git clone https://github.com/ckkelvinchan/BasicVSR_PlusPlus.git
```

Overwrite some files
```
cp restoration_video_demo.py BasicVSR_PlusPlus/demo/
cp -r chkpts/ BasicVSR_PlusPlus/
```

### Environment Setup
---

We are going to create one virtual environment with (mini/ana)conda. 
Since [BasicVSR++](<https://github.com/ckkelvinchan/BasicVSR_PlusPlus>) is built on [MMCV](https://github.com/open-mmlab/mmcv).
And MMCV depends very heavily on the version of pytorch and cuda.
We will be installing specific [Pytorch](https://pytorch.org/) versions.
If there are problems related to version mismatch or version conficts, please try to install [CUDA 11.8](https://developer.nvidia.com/cuda-11-8-0-download-archive) or [CUDA 12.1](https://developer.nvidia.com/cuda-12-1-0-download-archive).

Make sure Cuda and Nvidia driver is working
```
nvidia-smi
nvcc -V
```

Create conda environment
```
conda create --name my_env python=3.8
conda activate my_env
pip3 install torch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 --index-url https://download.pytorch.org/whl/cu118
```

Install requirement for [BasicVSR++](<https://github.com/ckkelvinchan/BasicVSR_PlusPlus>).
```
pip install openmim
mim install mmcv-full==1.6.0
cd BasicVSR_PlusPlus
pip install -v -e .
```

Install requirement for YOLOv5.
```
pip install -r requirements.txt
```

Install [FFmpeg](https://ffmpeg.org/).
```
pip install ffmpeg
```

Check FFmpeg version. You will need ffmpeg>=4.4 in our experience. Specific the version when installing if necessary.
```
ffmpeg
```

Install some other packages.
```
pip install psutil
pip install seaborn
```

### Dataset
---

We are using [Inter4K](<https://github.com/alexandrosstergiou/Inter4K>) dataset. 
Download the dataset with the link [https://tinyurl.com/inter4KUHD](<https://tinyurl.com/inter4KUHD>) from the official repository.
Unzip it at wherever you want to save it.
```
unzip Inter4K.zip -d Inter4K
```

For example, I unzip it under "Datasets/". The structure of the dataset should look like below:
```
Datasets/
  Inter4K/
    Inter4K/
      60fps/
        UHD/
          1.mp4
          2.mp4
          (1000 mp4s)
```

### Inference
---

Run the inference with the following command:

```
python run.py --cfg <config files>
```

For example,
```
python run.py --cfg config/inference.json
```

About the parameters in the config files, please refer to `config/parameter.py` and `config/*.json` for more information.

The results will be recorded in the log files.

![plot](https://github.com/b06901089/R11921098_THESISv2/blob/main/image/example.png?raw=true)

### Code Reference

```
https://github.com/alexandrosstergiou/Inter4K
https://github.com/Lornatang/FSRCNN-PyTorch
https://github.com/Cartucho/mAP
https://github.com/ckkelvinchan/BasicVSR_PlusPlus
```

All other necessary citations can be found in the original thesis. Thank you!
