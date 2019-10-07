# Basic Setup for Ubuntu 18.04-2 in Raspberry Pi 
The note show how to add some userful packages in Pi  
## Install Basic command package in Pi   
$ sudo apt-get install aptitude apt-file byobu  
$ sudo apt-get install vim tasksel   
$ sudo apt-get install tree  
$ sudo apt-file update    

## Install Python's Conda environment in Pi
Conda is very nice tool the make sure python environment can be developed in different situation, So that we can develope different python application and don't worried about the messy python environment because every different python environment is independent.   
 
### check current environment for the Pi board with current OS
   
$ lsb_release -a     
No LSB modules are available.  
Distributor ID:	Ubuntu  
Description:	Ubuntu 18.04.2 LTS  
Release:	18.04  
Codename:	bionic  
$ uname -a    
Linux blockstream-desktop 4.15.0-1032-raspi2 #34-Ubuntu SMP PREEMPT Wed Feb 6 11:50:42 UTC 2019 armv7l armv7l armv7l GNU/Linux    

### Install for conda      
Thus, we have no anaconda for it but we can use miniconda to instead anaconda   
  
$ wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-armv7l.sh  
$ sudo md5sum Miniconda3-latest-Linux-armv7l.sh # (optional) check md5   
$ sudo /bin/bash Miniconda3-latest-Linux-armv7l.sh # -> change default directory to /home/blockstream/miniconda3  
  
PS: click yes for every yes/no question and you can setup conda completely.   
  
### To check the status of conda now 
$ which conda    
/home/blockstream/miniconda3/bin/conda    
When you see above message, it mean your conda is ready now.   
  
### Add rpi channel for conda  
You need to add rpi channel because the basic conda package is put on  rpi channel    
$ conda config --add channels rpi  
  
### Try to Create web-api-server with python=3.6  
$ conda create -n web-api-server python=3.6  

### Basic commands to change to different conda environment  
#### To see what conda environment you are in
$ conda env list   
\# conda environments:  
\#
web-api-server           /home/blockstream/.conda/envs/web-api-server  
root                  *  /home/blockstream/miniconda3   

Don't install anything in root environment.  Do the following command and you can change environment into web-api-server.  
$ source activate web-api-server  
  
$ conda env list   
\# conda environments:   
\#
web-api-server        *  /home/blockstream/.conda/envs/web-api-server  
root                     /home/blockstream/miniconda3   
  
Now, you are in web-api-server environment.  
  
Futher more , The way to escape is by the following command...  
$ source deactivate   

