# CarND-Traffic-Light-Classifier
Traffic Light Classifier for the Term 3 Capstone Project

# Installation Instructions

#### Ensure the following is installed
sudo apt-get install protobuf-compiler python-pil python-lxml python-tk

pip install tensorflow-gpu==1.4

pip install matplotlib

#### Clone this repo to your workspace
git clone XXXX

#### Clone the Tensorflow models repo to your workspace
git clone https://github.com/tensorflow/models.git

#### Checkout the version that works with Tensorflow 1.4
git checkout f7e99c0

#### Run the following in the research directory
protoc object_detection/protos/*.proto --python_out=.

export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim

python object_detection/builders/model_builder_test.py

#### Download and extract the SSD Inception V2 model to ./models
wget http://download.tensorflow.org/models/object_detection/ssd_inception_v2_coco_2017_11_17.tar.gz

tar -xvzf ssd_inception_v2_coco_2017_11_17.tar.gz

#### Download the datasets
wget https://www.dropbox.com/s/vaniv8eqna89r20/alex-lechner-udacity-traffic-light-dataset.zip?dl=0

wget https://www.dropbox.com/s/bvq7q1zoex3b46i/dataset-sdcnd-capstone.zip?dl=0 

unzip alex-lechner-udacity-traffic-light-dataset.zip?dl=0

unzip dataset-sdcnd-capstone.zip?dl=0 

#### Train the Classifiers 
python train.py --logtostderr --train_dir=./models/sim/train --pipeline_config_path=./config/ssd_inception_v2_coco_sim.config

python train.py --logtostderr --train_dir=./models/real/train --pipeline_config_path=./config/ssd_inception_v2_coco_real.config
