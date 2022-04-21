# SegNet MHP Camera

 This is a camera that will run off of the SegNet MHP Object Detection network. This can be used as a security camera and can highlight any individuals in frame.

![add image descrition here](direct image link here)

## The Algorithm

Add an explanation of the algorithm and how it works. Make sure to include details about how the code works, what it depends on, and any other relevant info. Add images or other descriptions for your project here. 

## Running this project

`NOTE: This should be completed directly onto your jetson nano. (Simply connect a HDMI cord to a monitor and plug a mouse and keyboard into the jetson. You will also need a usb camera, I used a logitec webcam.`

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
4. Make a directory:
```
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

7. When the download has finished, you should be able to type commands again. Now that you have downloaded Segnet and the MHP networks, run:
```
segnet --network=fcn-resnet18-mhp-640x360 /dev/video0
```
`NOTE: You can change out the '640x360' for '512x320' if you want to. Also, make sure your webcam is connected for '/dev/video0' to work.`

8. If everything works, you should get a live video feed pop up on your jetson's screen, showing everything normally and should only highlight humans in the frame.















[View a video explanation here](video link)
