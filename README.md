Hi!<br>
<br> 
This repo supports a handson training on configuring a log collector and SIEM.<br>
<br>
Disclaimer: This is a walkthrough handson demo. You must make you own judgement about safely instally and running code download from the web. <br>
<br>
What you need to set up and get running before following along the hands-on demo.
1. All demo's are in a virtual Linux environment. 
For WIndows: use WSL with Ubuntu. 
We'll Ubuntu 22.04.2 LTS.
4096MB
2 CPU 
25GB disk

2. Make sure git is installed
```
sudo apt install git
```

3. Clone this repo
Find the http link on this page.<br> 
```
git clone <https://.....>
```
4. Install docker  
https://docs.docker.com/engine/install/ubuntu/
Make sure:  docker run hello-world:latest runs.
5. Install docker-compose



6. fluent build and install
7. Install all build tools and requirements.

``` 
sudo apt update
sudo apt -y install cmake
sudo apt -y install flex
sudo apt -y install bison 
sudo apt -y install libyaml-dev
sudo apt -y install libssl-dev
sudo apt -y install libsystemd-dev  
sudo apt -y install pkg-config
sudo apt -y install g++
``` 

Clone the Fluentbit repo:
```
 git clone https://github.com/fluent/fluent-bit
```
`` 
$ cd build
$ make
```
Skip the "make install" step <b>
We'll demonstrate this with Ansible, later on. <br>
<br>

Copy the fluent-bit binary you jsut made to to the repo folder wher eyoud this repository.

```
cp ~/fluent-bit/build/bin/fluent-bit ~/Workshop-Log-Collector/repo/
```





https://docs.fluentbit.io/manual/installation/sources/build-and-install

Fluent Bit v2.1.3





