No longer updated. Some of the stuff in here is now wrong

# AI-gym_with_Mujoco-py
Here I show how to setup your enviorment to run AI-gym enviorments that use the physic engine Mujoco. This was a pain to get working on windows, so this repository will have a setup guide and an example on how to learn to walk.
Under construction.


AI gym is a library for machine learning, with where you can try to make your model play games, learn to walk, solve a cube etc.
Some of the enviorments in AI-gym use a physic engine.
To use cool enviorments such as [ant-v2](https://gym.openai.com/envs/#mujoco), bipedal locomotion, and the [new robotic arm enviorments for AI-gym](https://blog.openai.com/ingredients-for-robotics-research/), you need your mujoco-py which lets your python to comunicate with the C++ code that runs the physic engine.


## Setup
Here i show how you get mujoco, mujoco-py and gym to work together in your enviorment. This shows setup for Windows OS, but i dont expect the other operating systems to be very diffrent.

**Visual studio 2017**,
First start download [Visual studio 2017](https://www.visualstudio.com/downloads/)since this takes some time to download and install. You might also be able to do it with only the [build tools](http://landinghub.visualstudio.com/visual-cpp-build-tools) if you dont want to download the entire Visual studio, but i have not tested this.

**Mujoco**
Mujoco is not open source, but it is free for students and you get a 30 day free trial. 30 days should be enough to determine if you like to work with these gym enviorments. (They make it very easy).
For mujoco to work you need a license key, which is easy to get. Even if you are a student it is recomended that you use the 30 day free trial key first, since the key only work once per machine it seems like. Also it takes a day for the student license key application to get processed, while the 30 day free key is a lot faster.
Download [mujoco](https://www.roboti.us/index.html).
Get [30 days free license key](https://www.roboti.us/license.html). If you have student email you can use it to get permanent license key on this page, but for now just use the trial key.
You will a license key on email.
Now, the mujoco-py module will look for Mujoco in C:/Users/"yourUserName"/.mujoco

Open comand promt by searching "cmd" and click enter.
This should make you start in your user directory by default. If not type: cd C:\Users\"yourUserName"
Type mkdir ".mujoco" to create the folder.
In the explorer simply copy paste the mjpro150 folder you downloaded into your ".mujoco" folder.
To make it work put the "mjkey.txt" you got on email into the \.mujoco\mjpro150\bin folder.
For mujoco-py which we will use later, also put the key in the \.mujoco\ folder.

*Test that mujoco works*
From the bin folder, start "simulate.exe". This gives you an empty window with text that tells you to copy models into it.
Go to the models/ folder and drag "humanoid100" file into the mujoco window. It should now show you a human ragdoll and other objects falling to the ground in an physic enviorment
If any of this fail, read the README file in the doc folder.

**Python enviorment**
Note, when I build the physic simulator i got the "path to long" problem. Allowing win32 long paths, did not solve it. Because of this i highly recomend to have your python enviorment run form a shallow path (not to long).
*Anaconda3*
Get [Anaconda3](https://www.anaconda.com/what-is-anaconda/) and install it directly in C:\. Default is \Users\"username", but we want a shorter file path.
Open anaconda promt. (Windows button and search anaconda)
Now we make an python enviorment. I chose to call mine "Ta"
type: conda create -n Ta
type: conda activate Ta
Now we install all the fun stuff we need.
type: conda install pip
pip install --upgrade pip
pip install gym
pip install mujoco-py


For mujoco-py to work we need the enviorment to be able to find vcvarsall.bat and cl.exe. This was maybe my biggest problem when installing, but when you know of them, it goes very fast.

**vcvarsall.bat**
Mujoco-py needs to be able to find the "vcvarsall.bat" file. It looks for it in the enviorment variables. If you dont know where it is, just search in C:\Program Files (x86)\Microsoft Visual Studio\2017\ for vcvarsall
In pycharm
Run (toolbar or in drop down meny next to green play button) -> Edit configurations. For the python file you want to run look at "Enviorment Variables:" and press "..." button to edit. Green pluss sign to add.
Add DISTUTILS_USE_SDK=C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\
Now you dont have to set it every time, but it will be remembered for this python file.


In comand line: SET DISTUTILS_USE_SDK='C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\'


**cl.exe**
cl.exe we add to path, not enviorment variable. (At least as default)
For me this file was found in C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Tools\MSVC\14.12.25827\bin\Hostx64\x64
This might be diffrent depending on you machine configurations. If it is not there just search for it in the explorer.
Let your omputer know where to look for building C++ code with visual studio 2017



**Test Mujoco-py**
Run the python file (not yet added) in examples.
First time you import mujoco_py it will try to build the enviorment. This will perhaps take a little time. If it takes to long, and you get no feedback it might be that there is something wrong with the key (name or location).
If it does not work:
Navigate to the tests that comes with the mujoco-py. Run the test_builder to get more info. Located in C:\Anaconda3\envs\Te\Lib\site-packages\mujoco_py-1.50.1.41-py3.6.egg\mujoco_py\tests


Congratulation, your first step in world domination by a machine army is done. You now need to find out how to make robots learn to walk. This is what we will do next.
It should be a good example of how you can use the AI-gym enviorment.


## Learn to walk
We will use the ant-v1 enviorment to learn a quadroped to walk. To do this we will use a clever evolutionary algorithm proposed by OpenAI [here], and implemented in python by [(...)](githublocation). This means that you dont actually need to know any of the matematics of

pip install evostra

He did not comment a lot, but his code is quite easy to read. the main program crates an Agent. The Agent class has the save, load, train, predict,run, functions already build. You only need to tell it what model to use. The model class is a Neural Network.







