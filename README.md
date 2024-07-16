<!--
Hey, thanks for using the awesome-readme-template template.  
If you have any enhancements, then fork this project and create a pull request 
or just open an issue with the label "enhancement".

Don't forget to give this project a star for additional support ;)
Maybe you can mention me or this repo in the acknowledgements too
-->
<div align="center">

<!--   <img src="assets/logo.png" alt="logo" width="200" height="auto" /> -->
  <h1>A large-scale fisheye dataset for parking slot detection</h1>
  
  <p>
    The benchmark method will be publicly available upon publication! 
  </p>
  
  
<!-- Badges -->
<p>
  <a href="https://github.com/Vipermdl/ParkScape/graphs/contributors">
    <img src="https://img.shields.io/github/contributors/Vipermdl/ParkScape" alt="contributors" />
  </a>
  <a href="">
    <img src="https://img.shields.io/github/last-commit/Vipermdl/ParkScape" alt="last update" />
  </a>
  <a href="https://github.com/Vipermdl/ParkScape/network/members">
    <img src="https://img.shields.io/github/forks/Vipermdl/ParkScape" alt="forks" />
  </a>
  <a href="https://github.com/Vipermdl/ParkScape/stargazers">
    <img src="https://img.shields.io/github/stars/Vipermdl/ParkScape" alt="stars" />
  </a>
  <a href="https://github.com/Vipermdl/ParkScape/issues/">
    <img src="https://img.shields.io/github/issues/Vipermdl/ParkScape" alt="open issues" />
  </a>
<!--   <a href="https://github.com/Vipermdl/ParkScape/blob/master/LICENSE">
    <img src="https://img.shields.io/github/license/Vipermdl/ParkScape.svg" alt="license" />
  </a> -->
</p>
   
<h4>
    <a href="https://github.com/Vipermdl/ParkScape">View Demo</a>
  <span> · </span>
    <a href="https://github.com/Vipermdl/ParkScape">Documentation</a>
  <span> · </span>
    <a href="https://github.com/Vipermdl/ParkScape/issues/">Report Bug</a>
  <span> · </span>
    <a href="https://github.com/Vipermdl/ParkScape/issues/">Request Feature</a>
  </h4>
</div>

<br />

<!-- Table of Contents -->
# :notebook_with_decorative_cover: Table of Contents

- [About the Project](#star2-about-the-project)
  * [Updates](#fire-update)
- [Getting Started](#toolbox-getting-started)
  * [Prerequisites](#bangbang-prerequisites)
  * [Installation](#gear-installation)
- [Methodology](#compass-data-preparation)
  * [Inference](#art-inference)
  * [Training](#key-training)
- [Results](#scroll-results)
- [Contributing](#wave-contributing)
- [License](#warning-license)
- [Contact](#handshake-contact)
- [Citation](#gem-acknowledgements)

<!-- About the Project -->
## :star2: About the Project

<div style="color:#0000FF" align="center">
<img src="imgs/fig1.png"/> 
</div>

Autonomous valet parking systems eliminae the need for human drivers to find parking slots, reducing the hassle associated with parking in congested areas. Fisheye imags provise valuable information over a large area instantaneously; nevertheless, no current dataset captures the complexity of parking scenes at the level of granularity required by real-world applications. To address this, we introduce ParkScapes, an fisheye image dataset with highly-accurate, fine-grained annotation for corner-based parking slot labeling. ParkScape provides annotation for 10,000 images, covering a variety of diverse scanarios, including shopping malls, industrial parks, and communities. Please cite if you use it in your work!

### :fire: Update

- [2024/03/04] We have released the ParkScape, you can download the dataset from [here](https://pan.baidu.com/s/1scbpA9_Kq9CFZGtcDuGc-g?pwd=zni5).

<!-- Getting Started -->
## 	:toolbox: Getting Started

<!-- Prerequisites -->
### :bangbang: Prerequisites

* Python 3.8
* Pytorch 1.11.0
* CUDA 11.3 or higher

<!-- Installation -->
### :gear: Installation

First, install dependencies

```bash
  # clone project 
  git clone https://github.com/Vipermdl/ParkScape
  
  # install project
  cd ParkScape
  pip install -r requirements.txt
```

<!-- Roadmap -->
## :compass: Benchmark method

### :art: Inference

To run the evaluation process, you need to download the model weights

```bash
wget -q https://github.com/Vipermdl/releases/download/v0.1.0-alpha/parkscape_detector.pth
```

 Inference with detect.py

```bash
python detect.py --weights parkscape_detector.pth --source 0                               # webcam
                                                     img.jpg                         # image
                                                     vid.mp4                         # video
                                                     screen                          # screenshot
                                                     path/                           # directory
                                                     list.txt                        # list of images
                                                     list.streams                    # list of streams
                                                     'path/*.jpg'                    # glob
                                                     'https://youtu.be/LNwODJXcvt4'  # YouTube
                                                     'rtsp://example.com/media.mp4'  # RTSP, RTMP, HTTP stream
```

### :key: Training

After the model and dataset download automatically, training time for the parking slot detector are 2 days on a NVIDIA 3090 GPU (Multi-GPU times faster). Use the largest `--batch-size` possible, or pass `--batch-size -1` for detector [AutoBatch](https://github.com/ultralytics/yolov5/pull/5092).

```bash
python train.py --data parkscape.yaml --epochs 300  --cfg parking_slot_detector.yaml  --batch-size 16                                                              
```

<!-- Code of Conduct -->
## :scroll: Results

| Method                                                                              |Backbone|AP_{50}|AP_{75}|AP|AP_{M}|FPS|
| ----------------------------------------------------------------------------------- |------ |------ |------ |------ |------ |------ |
| [CID](https://openaccess.thecvf.com/content/CVPR2022/papers/Wang_Contextual_Instance_Decoupling_for_Robust_Multi-Person_Pose_Estimation_CVPR_2022_paper.pdf/)|HRNet-W32|49.9|46.3|43.9|46.7|15.46|
| [DEKR](https://openaccess.thecvf.com/content/CVPR2021/papers/Geng_Bottom-Up_Human_Pose_Estimation_via_Disentangled_Keypoint_Regression_CVPR_2021_paper.pdf)|HRNet-W32|48.4|45.3|43.3|46.3|16.56|
| [Associative Embedding](https://proceedings.neurips.cc/paper_files/paper/2017/file/8edd72158ccd2a879f79cb2538568fdc-Paper.pdf)|HRNet-W32|52.9|43.9|43.8|48.0|5.854|
| [CenterNet](https://arxiv.org/pdf/1904.07850.pdf)|DLA-34|51.4|47.5|44.9|48.5|52.63|
| Our|CSPDarkNet53|55.1|50.9|47.0|48.1|54.05|


## :wave: Contributing

<a href="https://github.com/Vipermdl/ParkScape/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Vipermdl/ParkScape" />
</a>

Contributions are always welcome!

<!-- FAQ -->
<!-- ## :grey_question: FAQ

- Question 1

  + Answer 1

- Question 2

  + Answer 2 -->


<!-- License -->
## :warning: License

Distributed under the no License. See LICENSE.txt for more information.


<!-- Contact -->
## :handshake: Contact

Dongliang Ma - [@dongliangma1](https://twitter.com/dongliangma1) - mdl.viper@gmail.com

Project Link: [https://github.com/Vipermdl/ParkScape](https://github.com/Vipermdl/ParkScape)


<!-- Acknowledgments -->
## :gem: Citation

If ParkScape is useful or relevant to your research, please kindly recognize our contributions by citing our paper:

```bash
@ARTICLE{fu2024parkscape,
  author={Fu, Li and Ma, Dongliang and Qu, Xin and Jiang, Xin and Shan, Lie and Zeng, Dan},
  journal={IEEE Transactions on Instrumentation and Measurement}, 
  title={ParkScape: A Large-Scale Fisheye Dataset for Parking Slot Detection and a Benchmark Method}, 
  year={2024},
  volume={73},
  number={},
  pages={1-13},
  keywords={Cameras;Distortion;Autonomous vehicles;Detectors;Convolution;Lighting;Annotations;Autonomous driving;cameras;datasets;fisheye images;parking slot detection},
  doi={10.1109/TIM.2024.3406840}}
```
