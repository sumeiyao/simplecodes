## STEP1 Server Connection and Conda Installation

```bash
## vscode terminal
ssh your_nethz@mtec-cae-gpu02
#paste password


cd /data-nfs
mkdir sumyao
cd sumyao 

wget https://repo.anaconda.com/archive/Anaconda3-2023.03-Linux-x86_64.sh  #下载anaconda 
bash Anaconda3-2023.03-Linux-x86_64.sh  #安装anaconda 
```



## STEP2 Envs for GPU

VSCODE连接sumyao文件夹后

```bash
conda activate --name gpu python=3.9 #创建环境
conda activate gpu #激活环境
conda install ipykernel #安装环境注册包
python -m ipykernel install --user --name gpu --display-name "gpu" #注册内核
nvidia-smi #查看cuda版本
#安装支持gpu的pytorch(官网）
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118  #linux系统/pip命令/cuda平台比系统高没事
```

 在ipynb文件中查看cuda是否可以使用

```python
import torch
print(f"CUDA available: {torch.cuda.is_available()}")
if torch.cuda.is_available():
  print(f"Number of GPUs: {torch.cuda.device_count()}")
  print(f"Current GPU device: {torch.cuda.current_device()}")
  print(f"GPU name: {torch.cuda.get_device_name(torch.cuda.current_device())}")

```

## STEP3 open in browser

?  ssh -N -f -L localhost:8894:localhost:8894 sumyao@mtec-cae-gpu02

 

 

