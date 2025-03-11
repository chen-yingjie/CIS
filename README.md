# Causal Intervention for Subject-Deconfounded Facial Action Unit Recognition

Official implementation of "Causal Intervention for Subject-Deconfounded Facial Action Unit Recognition" (AAAI 2022)[paper](https://arxiv.org/abs/2204.07935).

<p align="center">
<img src="images/CIS_overview.png" width="88%" />
</p>

## 💡 Abstract
Subject-invariant facial action unit (AU) recognition remains challenging for the reason that the data distribution varies among subjects. In this paper, we propose a causal inference framework for subject-invariant facial action unit recognition. To illustrate the causal effect existing in AU recognition task, we formulate the causalities among facial images, subjects, latent AU semantic relations, and estimated AU occurrence probabilities via a structural causal model. By constructing such a causal diagram, we clarify the causal effect among variables and propose a plug-in causal intervention module, CIS, to deconfound the confounder Subject in the causal diagram. Extensive experiments conducted on two commonly used AU benchmark datasets, BP4D and DISFA, show the effectiveness of our CIS, and the model with CIS inserted, CISNet, has achieved state-of-the-art performance.

## 🔧 Usage
### Dependencies
```bash
$ git clone https://github.com/echoanran/CIS.git $INSTALL_DIR
```
* python >= 3.6
* torch >= 1.1.0
* requirements.txt
```bash
$ pip install -r requirements.txt
```
* torchlight
```bash
$ cd $INSTALL_DIR/torchlight
$ python setup.py install
```

### Data Preparation
#### Step 1: Download datasets
First, request for the access of the two AU benchmark datasets:
* [BP4D](http://www.cs.binghamton.edu/~lijun/Research/3DFE/3DFE_Analysis.html)
* [DISFA](http://mohammadmahoor.com/disfa/)

#### Step 2: Preprocess raw data
Preprocess the downloaded datasets using [Dlib](http://dlib.net/)
* Detect face and facial landmarks
* Align the cropped faces according to the computed coordinates of eye centers
* Resize faces to (256, 256)

#### Step 3: Split dataset for subject-exclusive 3-fold cross-validation
Split the subject IDs into 3 folds randomly

#### Step 4: Generate feeder input files
Our dataloader `$INSTALL_DIR/feeder/feeder_image_causal.py` requires two data files (an example is given in `$INSTALL_DIR/data/bp4d_example`):
* `label_path`: the path to file which contains labels ('.pkl' data), [N, 1, num_class]
* `image_path`: the path to file which contains image paths ('.pkl' data), [N, 1]

### Training 
```bash
$ cd $INSTALL_DIR
$ python run-cisnet.py
```

## 🔗 Citation
Please cite our paper if you use the codes:
```
@inproceedings{chen2022cis,
  title={Causal Intervention for Subject-Deconfounded Facial Action Unit Recognition},
  author={Chen, Yingjie and Chen, Diqi and Wang, Tao and Wang, Yizhou and Liang, Yun},
  journal={arXiv preprint arXiv:2204.07935},
  booktitle={AAAI},
  year={2022}
}
```
