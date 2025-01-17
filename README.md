# QOT
QUATERNION ORTHOGONAL TRANSFORMER FOR FACIAL EXPRESSION RECOGNITION IN THE WILD
## Requirements
- Python=3.8
- tensorflow=2.6.0
- PyTorch=1.10
- torchvision=0.11.0
- cudatoolkit=11.3
- matplotlib=3.5.3

## Training & Evaluate
We evaluate QOT on RAF-DB, AffectNet and SFEW. We take RAF-DB as an example to introduce our method.
### Traning
- Step 1: download RAF-DB datasets from official website, and put it into ./datasets
- Step 2: download pre-trained ResNet-50 from [Google Drive](https://drive.google.com/file/d/1gbaCNiNdpnYEnc9ygdB-u7eEnV5Sd_1c/view?usp=sharing), and put it into ./pretrianed
- Step 3: run main_Upload.py to train Orthogonal_CNN model.
- step3 会报错
- Original Traceback (most recent call last):
  File "/home/cike/anaconda3/lib/python3.9/site-packages/torch/nn/parallel/parallel_apply.py", line 61, in _worker
    output = module(*input, **kwargs)
  File "/home/cike/anaconda3/lib/python3.9/site-packages/torch/nn/modules/module.py", line 1130, in _call_impl
    return forward_call(*input, **kwargs)
  File "/home/cike/QOT-main/models/resnet_v1.py", line 285, in forward
    return self._forward_impl(x)
  File "/home/cike/QOT-main/models/resnet_v1.py", line 280, in _forward_impl
    x = self.fc(x)
  File "/home/cike/anaconda3/lib/python3.9/site-packages/torch/nn/modules/module.py", line 1130, in _call_impl
    return forward_call(*input, **kwargs)
  File "/home/cike/anaconda3/lib/python3.9/site-packages/torch/nn/modules/linear.py", line 114, in forward
    return F.linear(input, self.weight, self.bias)
RuntimeError: mat1 and mat2 shapes cannot be multiplied (2x192 and 768x7)


进程已结束,退出代码1

- Step 4: replace the path with the pretrained model in Step 3 in main_generate_ortho.py to generate the numpy file of orthogonal features.
- Step 5: load orthogonal features generated in Step4 or directly download the pre-generated features from [Google Drive](https://drive.google.com/file/d/1MYJm235ZINywXBcZ0Z4nBqT3JUMROoaA/view?usp=sharing), and run q-vit_RAFDB_Upload.py to training QOT module.
### Evaluate
- Step 1: download RAF-DB datasets from official website, and put it into ./datasets
- Step 2: download the checkpoint from [Google Drive](https://drive.google.com/file/d/14pxYAWQCaAdk64xP8A9i2egOVEQ365L_/view?usp=sharing), and put it into ./checkpoint_cnn
- Step 3: edit the evaluate_path with path in Step 2 and run main_Upload.py to evaluate Orthogonal_CNN model.
- Step 4: download the pre-generated orthogonal feature from Google Drive, and put it into ./orthogonal_npy
- Step 5: download the checkpoint from [Google Drive](https://drive.google.com/file/d/1S9nCW4WZSqVKCalwbzCaRzh_Cuz-rqy8/view?usp=sharing), and put it into ./checkpoint_qvit
- Step 6: run the evaluate code in q-vit_RAFDB_Upload.py to evaluate QOT module.

## Pre-trained Model
Orthogonal_CNN:[Google Drive](https://drive.google.com/file/d/14pxYAWQCaAdk64xP8A9i2egOVEQ365L_/view?usp=sharing)
Orthogonal Features:[Google Drive](https://drive.google.com/file/d/1MYJm235ZINywXBcZ0Z4nBqT3JUMROoaA/view?usp=sharing)
QOT: [Google Drive](https://drive.google.com/file/d/1S9nCW4WZSqVKCalwbzCaRzh_Cuz-rqy8/view?usp=sharing)


