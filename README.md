# hwc-matlab-client
<p align="center">
  <img src="https://user-images.githubusercontent.com/26273766/190159953-ad5e1969-7da5-43bf-8437-16cec4d9d7c9.svg" width="400"/>
</p>

Homework Checker client for matlab. This is the client side of the [HWC](https://github.com/ITMORobotics/hwc-server) application.

## Installation

1. Create new working directory and open matlab here.  
2. Download HWC Lab Checker using matlab Git Project:  
    ```
    HOME -> New -> Project -> From Git
    ```
    <img src="https://i.imgur.com/1SvD4lu.png" alt="From GIT" width="70%"/>

3. Type into __Repository path__: https://github.com/ITMORobotics/hwc-matlab-client.git, and select the working directory in the field __Sansdbox__ and click __Retrieve__:  
    <img src="https://i.imgur.com/hoOAq5f.png" alt="github" width="95%"/>
4. Select project name and submit project creating:  
    <img src="https://i.imgur.com/WGze49L.png" alt="submit" width="75%"/>

5. Close this window  
    <img src="https://i.imgur.com/nSYLPgW.png" alt="submit" width="70%"/>


6. Later for openning the project you can use:  
    ```
    Open -> Recent -> Your Project
    ```
    <img src="https://i.imgur.com/5j19zWW.png" alt="submit" width="90%"/>

### Another way (if you dont have git-upload-pack)
![](https://i.imgur.com/CT1H85y.png)
If you get this error, you can download client in archive .zip:

1. Create new working directory and open matlab here.  

2. Download [Client](https://github.com/ITMORobotics/hwc-matlab-client/zipball/main/)  

3. Extract to working directory.  

4. Open the extracted directory in left window:  
    ```
    HOME -> Open -> From Folder
    ```
    ![](https://i.imgur.com/gbh8PeQ.png)

    
5. Add to path it and go to the directory:
    <img src="https://i.imgur.com/Ufr4Mjo.png" alt="addfolder" width="100%"/>


    
## Registration
1. To start doing lab work, you must register in the system. To do this, enter in the Matlab console:  
    ```python
    hwc = hwc_connect('SERVER_URL')
    ```
    for example:
    ```python
    hwc = hwc_connect('https://hwc-test-server.ru')
    ```
    If you have a problems with SSL Certificate. Please use `http` instead of `https`, for example:
    ```python
    hwc = hwc_connect('http://hwc-test-server.ru')
    ```
2. Fill in *Full name* and click __Enter__. After that fill in other required fields:  
    <img src="https://i.imgur.com/jcltADj.png" alt="submit2" width="100%"/>

If you have reinstalled client you should use also:
```python
hwc = hwc_connect('SERVER_URL')
```

In this case please repeat your name, id, email and password provided earlier.

## Usage

After registration you can connect at any time with   
```python
hwc = hwc_connect('SERVER_URL')
```
or to connect via http please change `https` on `http`.

For getting first task(lab) you must type:  
```python
task = hwc.get_task(1)
```

For other tasks(labs) you must type desired number:  
```python
task = hwc.get_task(laboratory_number)
```

The case will be generated on the first call. After that, you can retrieve your task at any time with  
```python
task = hwc.get_task(laboratory_number)
```

<img src="https://i.imgur.com/l8p7nNc.png" alt="task" width="79%"/>

There is your task. In task structure you can see in variable  __files__ associated filenames. In this case: *l1_1.pdf*. This file contains in folder __files__.  

In struct __parameters__ presented input variables for modeling the system described in *pdf* file:  
<img src="https://i.imgur.com/uFzZEGO.png" alt="task_parameters" width="79%"/>

In struct __answers__ presented variables that you must fill instead of __?__:  
<img src="https://i.imgur.com/6OUihVT.png" alt="task_answers" width="79%"/>

When you fill all variables in struct __answers__ instead of __?__ you can check it with:
```python
hwc.send_task(task)
```
<img src="https://i.imgur.com/MkJOnrn.png" alt="task_send" width="79%"/>

You are right if you have nonzero score opposite the corresponding variable. The total score is the sum of all scores. You can also see the number of attempts.

## Submission of laboratory work  
    
1. Upload the required answers to the HWC Lab Checking system as above.

2. Please send to `hdulab.checker@yandex.ru` from email, that you used to register in the HWC Lab Checker:
    - a zip-archive with all matlab files with comments, or in live script, or with some kind of brief report,
    - your password for HWC Lab Checker.