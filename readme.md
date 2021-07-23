本项目为[yolox](https://github.com/Megvii-BaseDetection/YOLOX)提供docker镜像

这里假设你的电脑有nvidia显卡，并正确安装了docker和nvidia-docker

# 编译镜像

运行以下命令下载dockerfile并编译镜像

```bash
git clone https://github.com/lyyiangang/yolox-dockerfile.git
cd yolox-dockerfile
docker build -f ./Dockerfile.txt -t yolox .
```

# 下载yolox 源码

```bash
git clone https://github.com/Megvii-BaseDetection/YOLOX
mv run-docker.sh YOLOX/
cd YOLOX/
```
只要保证```run-docker.sh```在YOLOX的根目录下就行。

# 启动虚拟容器

按照yolox readme指示下载好对应模型， 比如yolox_s.pth模型文件，运行以下命令测试demo程序

```bash
./run-docker.sh
python tools/demo.py image -n yolox-s -c model/yolox_s.pth --path assets/dog.jpg --conf 0.3 --nms 0.65 --tsize 640 --save_result --device gpu
```
可以得到如下检测结果：

![](doc/dog.jpg)


# TODO

- [ ] tensorrt支持
- [ ] ncnn支持
- [ ] 训练apex支持