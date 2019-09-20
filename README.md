# CSPN implemented in Pytorch 0.4.1

### Build & Run

This branch fixed some bugs and added the implementation for reading KITTI dataset.
You need to download the following dataset in HDF5 format:
```sh
 mkdir data; cd data
 wget http://datasets.lids.mit.edu/sparse-to-dense/data/nyudepthv2.tar.gz
 tar -xvf nyudepthv2.tar.gz && rm -f nyudepthv2.tar.gz
 wget http://datasets.lids.mit.edu/sparse-to-dense/data/kitti.tar.gz
 tar -xvf kitti.tar.gz && rm -f kitti.tar.gz
 cd ..
```


### Introduction
This is a PyTorch(0.4.1) implementation of [Depth Estimation via Affinity Learned with Convolutional Spatial Propagation Network](http://arxiv.org/abs/1808.00150). At present, we can provide train script in NYU Depth V2 dataset for depth completion and monocular depth estimation. KITTI will be available soon!

### Faster Implementation
We re-implement CSPN using [Pixel-Adaptive Convolution](http://arxiv.org/abs/1904.05373). 

### Multi_GPU
The implementation of multi-gpus is based on [inplace abn](http://arxiv.org/abs/1712.02616).

### Results
Method | Implementation details |  rml  | rmse  | log10 | Delta1 | Delta2 | Delta3 
 :-------| :------:  | :------: | :------: | :------: | :------: | :------: | :------: 
 Paper   | batch size=24 epoch=40 | 0.016  | 0.117 | - | 0.992 | 0.999 | 1.000
 Our_impl  | batch size=8 iteration=100k | 0.018 | 0.127 | 0.008 | 0.991 | 0.998 | 1.000
 Our_CSPN  | batch size=8 iteration=100k | 0.018 | 0.127 | 0.008 | 0.991 | 0.998 | 1.000

 ![Image text](https://github.com/dontLoveBugs/CSPN_monodepth/blob/master/result/nyu.PNG)

### Third Libs
[inplace abn](https://github.com/mapillary/inplace_abn)

[Pixel-Adaptive Convolution](https://github.com/NVlabs/pacnet)
