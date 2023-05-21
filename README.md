Hi!<br>
<br> 
This repo supports a handson training on configuring a log collector and SIEM.<br>
<br>
Disclaimer: This is a walkthrough handson demo. You must make you own judgement about safely instally and running code download from the web. <br>
<br>
<img src="web_assets/Overview_01.png">
<br>
<br>
What you need to set up and get running before following along the hands-on demo.<br>
<br>
1. All demo's are in a virtual Linux environment. 
For WIndows: use WSL with Ubuntu. <br>
We'll a Ubuntu 22.04.2 LTS VM with 4096MB mem, 2 CPU on a 25GB disk.<br>

2. Make sure git is installed
```
sudo apt install git
```

3. Clone this repo
Find the http link on this page.<br> 
```
git clone <https://.....>
```

4. Install a typof docker 
https://docs.docker.com/engine/install/ubuntu/
<br>
Note: While docker-compose is open source, Docker (c) is not. <br> 
In a commercial environments you'll need to check your required license for Docker (c)<br>
To be sure we'll now use podman.<br>

```
sudo apt install podman
```

Make sure everything works:

```
sudo docker run hello-world:latest
or
podman run hello-world:latest
```

5. Install docker-compose

```
sudo apt install docker-compose
```

Make sure it works:<br>
Create a folder test and create a file there called docker-compose.yml<br>
Contents:
```
version: '2'
services:
  hello_world:
    image: ubuntu
    command: [/bin/echo, 'Hello world']
```
In the same folder run:
```
sudo docker-compose up
```
The expected output:

```
...
...
Creating test_hello_world_1 ... done
Attaching to test_hello_world_1
hello_world_1  | Hello world
test_hello_world_1 exited with code 0
```
Run to clean up:
```
sudo docker-compose down
```
Make sure you understand what is happening!

<b>Fluent build and install</b>

1. Install all build tools and requirements.

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


2. Make sure fluent-bit is runable
``` 
cd ~/Workshop_Log_Collector/repo/
./fluent-bit
```
The output should be something like this:
```
Fluent Bit v2.1.3
** Copyright (C) 2015-2022 The Fluent Bit Authors
** Fluent Bit is a CNCF sub-project under the umbrella of Fluentd
** https://fluentbit.io

...[2023/05/15 21:20:07] [ info] [fluent bit] version=2.1.3, commit=6ae59962d6, pid=16301
...[2023/05/15 21:20:07] [ info] [storage] ver=1.4.0, type=memory, sync=normal, checksum=off, max_chunks_up=128<br>
...[2023/05/15 21:20:07] [ info] [cmetrics] version=0.6.1<br>
...[2023/05/15 21:20:07] [ info] [ctraces ] version=0.3.0<br>
[2023/05/15 21:20:07] [ info] [sp] stream processor started<br>
```
Ctlr-C wil stop her.





https://docs.fluentbit.io/manual/installation/sources/build-and-install

Fluent Bit v2.1.3



<b> Install Docker compose </b>
We'll require Docker Compsoe to deploy de Graylog environment in a pretty an easy way.<br>
The Ubuntu repository contains docker-composer but it's quite outdated so we'll get the latest<br>
<br>
We'll go for a newer version.<br>
For poduction systems I don't recommend add docker pgp repositories to apt for many reasons one being thay you don't want logging systems to be compromised by wrong deployments or potentially buggy new releases. Anyway as alway it depends.<br>
For now we'll get a fixed version. <br> 
Check https://github.com/docker/compose/releases for a recent version.<br>
```
mkdir -p ~/.docker/cli-plugins
chmod 700 ~/.docker/cli-plugins
# X86 platform
curl -SL https://github.com/docker/compose/releases/download/v2.17.3/docker-compose-linux-x86_64 -o ~/.docker/
cli-plugins/docker-compose
# Apple M1 platform
curl -SL https://github.com/docker/compose/releases/download/v2.17.3/docker-compose-linux-aarch64 -o ~/.docker/cli-plugins/docker-compose

chmod 700 ~/.docker/cli-plugins/docker-compose
echo 'PATH=$PATH:~/.docker/cli-plugins/' >> ~/.bashrc
cd ~
docker-compose -v
```
You should see:<br>
```
Docker Compose version v2.17.3
```
<br>
Play with docker-compose and get a demo website running.<br>
See this nice tutorial:<br>
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-22-04#step-1-installing-docker-compose
<br>









