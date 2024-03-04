<!--
Hey, thanks for using the awesome-readme-template template.  
If you have any enhancements, then fork this project and create a pull request 
or just open an issue with the label "enhancement".

Don't forget to give this project a star for additional support ;)
Maybe you can mention me or this repo in the acknowledgements too
-->
<div align="center">

<!--   <img src="assets/logo.png" alt="logo" width="200" height="auto" /> -->
  <h1>Deep learning for eastimating dissolved oxygen in global ocean</h1>
  
  <p>
    Details for Oxyformer will be publicly available upon publication! 
  </p>
  
  
<!-- Badges -->
<p>
  <a href="https://github.com/Vipermdl/Oxyformer/graphs/contributors">
    <img src="https://img.shields.io/github/contributors/Vipermdl/Oxyformer" alt="contributors" />
  </a>
  <a href="">
    <img src="https://img.shields.io/github/last-commit/Vipermdl/Oxyformer" alt="last update" />
  </a>
  <a href="https://github.com/Vipermdl/Oxyformer/network/members">
    <img src="https://img.shields.io/github/forks/Vipermdl/Oxyformer" alt="forks" />
  </a>
  <a href="https://github.com/Vipermdl/Oxyformer/stargazers">
    <img src="https://img.shields.io/github/stars/Vipermdl/Oxyformer" alt="stars" />
  </a>
  <a href="https://github.com/Vipermdl/Oxyformer/issues/">
    <img src="https://img.shields.io/github/issues/Vipermdl/Oxyformer" alt="open issues" />
  </a>
<!--   <a href="https://github.com/Vipermdl/Oxyformer/blob/master/LICENSE">
    <img src="https://img.shields.io/github/license/Vipermdl/Oxyformer.svg" alt="license" />
  </a> -->
</p>
   
<h4>
    <a href="https://github.com/Vipermdl/Oxyformer">View Demo</a>
  <span> · </span>
    <a href="https://github.com/Vipermdl/Oxyformer">Documentation</a>
  <span> · </span>
    <a href="https://github.com/Vipermdl/Oxyformer/issues/">Report Bug</a>
  <span> · </span>
    <a href="https://github.com/Vipermdl/Oxyformer/issues/">Request Feature</a>
  </h4>
</div>

<br />

<!-- Table of Contents -->
# :notebook_with_decorative_cover: Table of Contents

- [About the Project](#star2-about-the-project)
  * [Model architecture](#camera-model-architecture)
  * [Contributions](#dart-contributions)
- [Getting Started](#toolbox-getting-started)
  * [Prerequisites](#bangbang-prerequisites)
  * [Installation](#gear-installation)
- [Data preparation](#compass-data-preparation)
  * [Dissolved Oxygen measurements](#art-dissolved-oxyen-measurements)
  * [Driven factors](#key-driven-factors)
- [Develop the Oxyformer](#eyes-develop-the-oxyformer)
  * [Training Oxyformer](#test_tube-training-oxyformer)
  * [Run inference](#running-run-inference)
  * [Post process](#triangular_flag_on_post-post-process)
 - [Data and Results](#scroll-data-and-results)
- [Contributing](#wave-contributing)
- [License](#warning-license)
- [Contact](#handshake-contact)
- [Acknowledgements](#gem-acknowledgements)

<!-- About the Project -->
## :star2: About the Project

### :fire: Update

- [2023/07/11] We have released the annual Dissolved Oxygen Products derived by Oxyformer, details are shown in [here](https://github.com/Vipermdl/Oxyformer/blob/main/data.md).


<!-- Getting Started -->
## 	:toolbox: Getting Started

<!-- Prerequisites -->
### :bangbang: Prerequisites

* Python 3.8
* Pytorch 1.10.1
* CUDA 11.3 or higher

<!-- Installation -->
### :gear: Installation

First, install dependencies

```bash
  # clone project 
  git clone https://github.com/Vipermdl/Oxyformer
  
  # install project
  cd Oxyformer
  pip install -r requirements.txt
```

<!-- Roadmap -->
## :compass: Data preparation

* [x] Dissolved Oxygen measurements
* [ ] Driven factors

### :art: Dissolved Oxygen measurements

| Name                                                                                |Date accessed|
| ----------------------------------------------------------------------------------- |------ |
| [World Ocean Database](https://www.ncei.noaa.gov/)|02-2023|
| [CLIVAR and Carbon Hydrographic Database](https://cchdo.ucsd.edu/)|02-2023|
| [Pangaea Database](https://www.pangaea.de/)|02-2023|
| [Global Ocean Data Analysis](https://www.ncei.noaa.gov/access/ocean-carbon-acidification-data-system/oceans/GLODAPv2_2021/)|02-2023|

- After download the measurements of oxygen data, run the following command to data compilation and quality control

```bash
  # interpolate depth mapping using pchip function and data integrated.
  python scripts/interpolate.py
  # quality control for observational oxygen data
  python scripts/quality_control.py
```

### :key: Driven factors

- More details will be updated soon...
- After download the driven factors, run the following command to obtain the dataset dicatating Oxyformer's input and output data and train/val/test splits.

```bash
  python scripts/label_utils.py --merge --splits
```

## :eyes: Develop the Oxyformer

<!-- Screenshots -->
### :camera: Model architecture

<!-- <div align="center"> 
  <img src="https://placehold.co/600x400?text=Your+Screenshot+here" alt="screenshot" />
</div> -->

<!-- Running Tests -->
### :test_tube: Training Oxyformer

To train Oxyformer, run the following command

```bash
  python main.py experiments/Oxyformer.toml
```

<!-- Run Locally -->
### :running: Run inference

To save predictions between July 2002 and December 2020 as NetCDFs for Oxyformer run

```bash
  python inference.py experiments/inference.toml -o outputdir
```

<!-- Deployment -->
### :triangular_flag_on_post: Post process

The post-processing algorithm is then applied

```bash
  python post-processing/mask_result_by_bathymetric.py
```

<!-- Code of Conduct -->
## :scroll: Data and Results

- See [DATA.md](https://github.com/Vipermdl/Oxyformer/blob/main/data.md) for instructions on how to download the data of our Oxyformer.
- Please read the [DRAW.md](https://github.com/Vipermdl/Oxyformer/blob/main/draw.md) to generate the paper figures.

<!-- Contributing -->
## :wave: Contributing

<a href="https://github.com/Vipermdl/Oxyformer/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Vipermdl/Oxyformer" />
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

Project Link: [https://github.com/Vipermdl/Oxyformer](https://github.com/Vipermdl/Oxyformer)


<!-- Acknowledgments -->
## :gem: Acknowledgements

Use this section to mention useful resources and libraries that you have used in your projects.

 - [Xarray](https://docs.xarray.dev/en/stable/)
 - [Cartopy](https://scitools.org.uk/cartopy/docs/latest/)
 - [GEBCO_2022](https://www.gebco.net/data_and_products/gridded_bathymetry_data/gebco_2022/)
