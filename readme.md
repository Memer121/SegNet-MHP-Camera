# SegNet MHP Camera

 This is a camera that will run off of the SegNet Semantic Segmentation model. This can be used as a security camera and can highlight any individuals in frame using Multi-Human Parsing (MHP).

![image](https://user-images.githubusercontent.com/101989644/167172849-9670be5e-a216-49aa-ac01-015b4c4e1c91.png)
[Imgur](https://imgur.com/Bm857Cj)

## The Algorithm

SegNet is a semantic segmentation model. It consists of an encoder network and a decoder network, followed by a, one pixel at a time, classification layer. The enconder is usually a pre-trained network, such as ResNet. What the decoder network does is semantically projects the features learnt by the encoder onto a pixel space to get a dense classification.

## Running this project

1. Make sure git and cmake are installed. Run:
```
sudo apt-get update
sudo apt-get install git cmake
```
2. Clone the `jetson-inference` project:
```
git clone https://github.com/dusty-nv/jetson-inference
cd jetson-inference
git submodule update --init
```
3. Now install the python packages:
```
sudo apt-get install libpython3-dev python3.numpy
```
4. Go into 'jetson-inference' and create a directory to store SegNet.
```
cd jetson-inference
mkdir build
```
5. Download SegNet using the downloader tool:
```
cd build
cmake ../
```
[Imgur](https://imgur.com/E2KauvE)
![image](https://user-images.githubusercontent.com/101989644/164261058-21cb2317-40fb-46a4-946b-90bbefd3fc4e.png)

6. You will see the downloader tool (pictured above). Anything with a star, move to it using the arrow keys and unselect it by pressing the spacebar.
Now, scroll down until you find `FCN-Resnet18-MHP-(numbers)`. Select both `MHP-512x320` and `MHP-640x360`. Now, with both selected, press the Enter key.

[Imgur](https://imgur.com/aRJ5aG8)
![image](https://user-images.githubusercontent.com/101989644/164263701-591b3661-83e3-4989-b97f-2a8692d6af95.png)

7. When the download has finished, you should be able to type commands again. Now download VLC Media Player: https://www.videolan.org/ and this SDP file: https://drive.google.com/file/d/1EpYkg0_KYitMhMwYFK-zl81ucJX75GLL/view

8. Now run SegNet on a live video:
```
segnet --network=fcn-resnet18-mhp-640x360 --output-codec=h264 /dev/video* rtp://192.168.55.100:1234
```

`NOTE: You can change out the '640x360' for '512x320' if you want to. Also, make sure your webcam is connected for '/dev/video0' to work.`

9. Now right-click the SDP file and select `Open with VCL Player`

10. If everything works, you should get a live video on your screen, showing everything normally and should only highlight humans in the frame.
`NOTE: It may take a few minutes to load and they might be some lag`















[Will add a video explanation soon]
