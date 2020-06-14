---
layout: post
title:  "Docker for deep learning"
date:   2016-09-01
excerpt: "Docker containers for machine learning and deep learning GPU support."
project: true
tag:
- deep learning
- machine learning
- docker
comments: true
---

# Briefing

Solving all the dependencies for environment setup is frustrating, so here is my workhorse docker containers that I maintained on my job. Here is the [Github Repository](https://github.com/Marsan-Ma/docker_mldm)

The [GPU supported one](https://github.com/Marsan-Ma/docker_mldm_gpu) is more active since I have machines with GPU (amazon G series instances). I also make [a non-GPU version](https://github.com/Marsan-Ma/docker_mldm) for cases that I need to deploy smaller projects in cheaper machines.

Both of them include some other machine learning and must-have tools if you are working with data, machine learning and web.


# How to use

Basically both repositories are almost the same, there will be three files:

* **0-prepare-host.sh**
  install docker, nvidia driver, nvidia-docker in your host machine.

* **1-build-mldm.sh**
  build my machine learning toolbelt container
  here I choose **tensorflow gpu supported version** for deep learning, you may append whatever you like in Dockerfile!

* **2-start-mldm.sh**
  start the container with some environment setup script, with ipython notebook in http://<your_machine>:8888


Enjoy!
