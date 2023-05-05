# Setting Up

SETUP:
- Ubuntu 16.04 (DL AMI with NVIDIA driver pre installed)
- CUDA 8
- CuDnn 6
- Python2.7

Main steps:
- Launch ubuntu 16.04 DL AMI
- Install CUDA 8
- Install CuDnn
- Install Tensorflow
- Clone Repo (custom)


Using AWS Deep Leatning Ubuntu 16.04 API launch a GPU instance. As of now used G4dn.xlarge which ahs 1 16GB T4 GPU. The AMI comes prebuilt with CUDA 10 and 11.
I install CUDA 8 on our own using the runfile(local) option. The deb(local) fails to properly integrate CUDA and CuDnn. 

Follow the link to download CUDA 8. Add the paths as mentioned here for nvcc to detect cuda.
The setup ensures the symbolic link is created. 
The CuDnn version to be used is 6. Download it from here. The recommended way for installing cuDNN is to first copy the tgz file to /usr/local and then extract it, and then remove the tgz file if necessary. This method will preserve symbolic links. 

Use simmilar cmd according to your config:
scp -i ~/G3-Linux-Ubuntu.pem /home/orcazep/Downloads/cudnn-8.0-linux-x64-v6.0.tgz ubuntu@ec2-44-201-134-116.compute-1.amazonaws.com:/home/ubuntu   (Internet bottleneck)

Sudo mv cudnn-8.0-linux-x64-v6.0.tgz /usr/local
Cd /usr/local
Sudo Tar xvf cudnn-8.0-linux-x64-v6.0.tgz

Check version here: cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2


Once you have copied the tar follow this tutorial. CUDA & CuDnn installation complete. Now I need a tensorflow that supports these version and python2.7 too. Install python binary from here as in link: 

(TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow-1.30.0-cp27-none-linux_x86_64.whl)

export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.1.0-cp27-none-linux_x86_64.whl


# Colab Demo
https://colab.research.google.com/drive/1N7Z1A516cdUngk3UQkY1HAuydieR7sNd?usp=sharing