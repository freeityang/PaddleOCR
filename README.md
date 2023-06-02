参考文档： https://github.com/PaddlePaddle/PaddleOCR/blob/release/2.6/deploy/hubserving/readme.md



CPU: registry.baidubce.com/paddlepaddle/paddle:2.4.2
GPU: registry.baidubce.com/paddlepaddle/paddle:2.4.2-gpu-cuda11.2-cudnn8.2-trt8.0       ## CUDA11.2

GPU: registry.baidubce.com/paddlepaddle/paddle:2.4.2-gpu-cuda11.7-cudnn8.4-trt8.4       ## CUDA11.7

git clone -b 2.6  https://github.com/PaddlePaddle/PaddleOCR.git

cd PaddleOCR-release-2.6

pip install paddlehub -i https://mirror.baidu.com/pypi/simple

pip3 install starlette==0.27.0

pip3 install astroid==2.11.6

pip3 install protobuf==3.20.2

pip3 install gradio==3.11.0

 pip3 install flask-babel==2.0.0

pip3 install paddlehub -i https://mirror.baidu.com/pypi/simple

pip install Polygon3 -i https://pypi.tuna.tsinghua.edu.cn/simple

pip install lanms-neo

pip install scikit-image

pip install imgaug

pip install pyclipper

pip install lmdb

hub install deploy/hubserving/ocr_det/

hub install deploy/hubserving/ocr_rec/

hub install deploy/hubserving/ocr_system/

vim deploy/hubserving/ocr_system/params.py

vim deploy/hubserving/ocr_system/config.json

 export CUDA_VISIBLE_DEVICES=0      ###GPU版本开启

 vim /etc/profile                                        ###加入上面的export        

 vim /root/.bashrc                                     ###加入上面的export   

 source /etc/profile

 hub serving start -c deploy/hubserving/ocr_system/config.json

  ### 测试

 cd PaddleOCR-release-2.6

 python tools/test_hubserving.py --server_url=http://127.0.0.1:8868/predict/ocr_system --image_dir=/app/1.jpg
