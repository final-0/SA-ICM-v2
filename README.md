<div align="center">

### Image Coding for Machines with Edge Information Learning <br>
### Using Segment Anything
# (under construction)

---

### [SA-ICM](https://arxiv.org/abs/2403.04173) (IEEE ICIP 2024)
</div>

---
---

This is the official implementation of the following paper.<br>
<br>
・Image Coding for Machines with Edge Information Learning Using Segment Anything<br>
([IEEE Xplore](https://ieeexplore.ieee.org/document/10647785))
([arXiv](https://arxiv.org/abs/2403.04173))<br>
<br>
[![Paper](https://img.shields.io/badge/cs.CV-Paper-b31b1b?logo=arxiv&logoColor=red)](https://arxiv.org/abs/2403.04173)
[![arXiv](https://img.shields.io/badge/arXiv-2403.04173-b31b1b.svg)](https://arxiv.org/abs/2403.04173)

---
<div align="center">
  
### Compression Performance

|  lambda                                |   0.02   |   0.03   |   0.04   |   0.05   |   0.06   |   0.07   |
|:--------------------------------------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
| bitrate                                |   xxxxx  |   0.179  |   0.205  |   0.227  |   0.244  |   0.260  |

| bitrate                                |   xxxxx  |   0.179  |   0.205  |   0.227  |   0.244  |   0.260  |
|:--------------------------------------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|
| **yolo-v5** [detection]                |   xxxxx  |   41.1   |   41.6   |   41.9   |   42.1   |   42.2   |
| **mask r-cnn** [detection]             |   xxxxx  |   34.7   |   35.2   |   35.6   |   xxxxx  |   xxxxx  |
| **mask r-cnn** [instance-segmentation] |   xxxxx  |   31.2   |   31.8   |   32.1   |   xxxxx  |   xxxxx  |

</div>

config

- **yolov5**: [ultralytics](https://github.com/ultralytics/yolov5), yolov5m
- **mask r-cnn**: [mmdetection](https://github.com/open-mmlab/mmdetection), mask-rcnn_r50_fpn_1x_coco.py

---
<div align="center">
  
### Installation
</div>

1. Clone this repository from GitHub.
```
git clone https://github.com/final-0/SA-ICM-v2.git
```
2. Change the current directory to the "SA-ICM-v2" folder.
```
cd SA-ICM-v2/
```
3. Install the required dependencies in the current directory.

```
pip3 install -r requirements.txt 
```

---

<div align="center">

### Recommended Specs
</div>

For testing only, a GPU with about 11GB of memory is sufficient. (e.g. 1080ti, 2080ti)

---

<div align="center">
  
### Usage
</div>

###  image compression

Download [model weights](https://drive.google.com/drive/folders/1s7SwxFbDiI0CH0jLYw35edyPPYpIVUoK?usp=drive_link). 
You can obtain **"sa-icm_[lambda].pth.tar"** from this link. 
Lambda is a parameter to control the rate.<br>
These weights can be used by placing them in the "param" folder.<br>
``` 
param ---- param_details.txt
       |-- sa-icm_0.03.pth.tar
       |-- sa-icm_0.04.pth.tar
       |-- sa-icm_0.05.pth.tar
       |-- sa-icm_0.06.pth.tar
       |-- sa-icm_0.07.pth.tar
```

If you want to compress images for "Machines" with , run the following command :
``` 
python3 coding_m.py --checkpoint param/sa-icm_[lambda].pth.tar --input image/input
```

Add “--real” to the command to obtain a bit-stream:
``` 
python3 coding_m.py --checkpoint param/sa-icm_[lambda].pth.tar --input image/input --real
```

Compressed images will be saved in the folder "output_saicm_[lambda]".
``` 
image ---- input
       |-- output_saicm_[lambda]
```

---
